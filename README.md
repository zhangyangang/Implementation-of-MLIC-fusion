**NOT FINISHED**

# Implementation-of-MLIC-fusion paper
Multiscale Shape and Detail Enhancement from Multi-light Image Collections; Fattal, Agrawal, Rusinkiewicz

Synthesis algorithm is designed to enhance shape and surface detail by combining shading information across all of the input MLIC images.
Each is taken from same camera spot, but with different lightning directions.

## Paper link
* [The Hebrew University of Jerusalem](http://www.cs.huji.ac.il/~raananf/projects/mlic/mlic.html) contains link to image test data
* [princeton.edu](https://gfx.cs.princeton.edu/pubs/Fattal_2007_MSA/mlic.pdf)
* [berkeley.edu](http://kneecap.cs.berkeley.edu/papers/mlic/mlic-SIG07.pdf)

Each author is from different university.

## Dependencies

Paper is implemented in Python 3.7.1 with use of:
*  NumPy
*  OpenCV 3.4.2:
    * cv2.cvtColor - RGB <-> YUV
    * cv2.Sobel - to get gradient magnitude
    * cv2.convertScaleAbs - to get gradient magnitude
    * cv2.addWeighted - to get gradient magnitude
    * cv2.imread - in tests
    * cv2.GaussianBlur - during construction of I Detail
* SciPy:
    * scipy.ndimage.filters.minimum_filter - during construction of I Detail
*  Pytest
*  Jupyter Notebook (only for evaluation)

## How to use
This paper implementation is not finished.
So take this only as informative overview.

Fusion algorithm is implemented in single python class. Fusion class is located in *bilateral_fusion_MLIC.py* file and can be imported into python project via:

```
from bilateral_fusion_MLIC import Bilateral_fusion_MLIC
```

Instantiate and call fuse method:

```
mlic_fusion = Bilateral_fusion_MLIC(image_set=None, kernel_size=None, scale_depth=None, alpha=None, beta=None)
fused_image = mlic_fusion.fuse()
```

* *image_set*: list of 8bit RGB MLIC images each as numpy array [row, column, channel]
* *kernel_size*: bilateral decomposition step kernel size
* *scale_depth*: bilateral decomposition depth
* *alpha*: weight used during construction of I_base
* *beta*: used to trade-off emphasis of the detail image versus the base images (during construction of I_detail)
* *fused_image*: one 8bit RGB image as numpy array [row, column, channel]

## StackExchange questions about paper / implementation
* [I couldn't understand the meaning of eq. 11 on page 5](https://dsp.stackexchange.com/questions/26069/multiscale-shape-and-detail-enhancement-from-multi-light-image-collections)
* [Multi-light Image Collections fusion - not defined parameter](https://dsp.stackexchange.com/questions/57982/multi-light-image-collections-fusion-not-defined-parameter?noredirect=1#comment115395_57982)

## Licence

[MIT](https://github.com/ToKraTheSecond/Implementation-of-MLIC-fusion/blob/master/LICENSE)
