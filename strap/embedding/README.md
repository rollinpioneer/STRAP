## Configuring Embedding
We have defined the CLIP and DINOv2 encoders in `strap/embedding/encoders.py`. You can define your own encoders by inheriting from the `BaseEncoder` class and overwriting the `encode` and `preprocess` methods. 

To encode your datasets, use the `encode_datasets.py` script. This script will use the encoders you have defined in `get_encoders()` and the datasets you have defined in `get_datasets()`. Just change the dataset configs and the encoders list if you want to use different datasets or encoders. Set the `VERBOSE` flag to `False` to disable most of the logging statements. 

We also have a parallelized version of the dataset saving process as we noticed a large bottleneck in the dataset saving process. You can enable this by setting the `saver_threads` argument in the `encode_dataset` function to the number of threads you want to use. You can also set the `image_size` of the crop, and the batch_size of the encoder, as well as if you want to flip the images. LIBERO has upside down images, so we set `flip_images=True` for the embeddings to improve performance.

配置嵌入
我们在 strap/embedding/encoders.py 中定义了 CLIP 和 DINOv2 编码器。你可以通过继承 BaseEncoder 类并重写 encode 和 preprocess 方法来定义自定义编码器。

要对数据集进行编码，请使用 encode_datasets.py 脚本。该脚本会使用你在 get_encoders() 中定义的编码器和在 get_datasets() 中定义的数据集。如果要使用不同的数据集或编码器，只需更改数据集配置和编码器列表。将 VERBOSE 标志设为 False 可关闭大部分日志输出。

我们注意到数据集保存过程是一个瓶颈，因此提供了并行化的保存版本。可在 encode_dataset 函数中通过设置 saver_threads 参数为所需线程数来启用。你还可以设置裁剪的 image_size、编码器的 batch_size，以及是否翻转图像。LIBERO 有倒置图像，因此我们将 flip_images=True 用于嵌入以提高性能。