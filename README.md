imgutil
=======

Image operation utility

Installation
------------

Installation using pip::

    pip install imgutil

Prerequesite
------------

- jpegtran
- pngcrush

Usage
-----

### imgoptimize
- `imgoptimize(input_filename, output_filename=None)`
- It reduces jpeg/png file size.
- It converts CMYK to RGB.

**quick example**

    >>> import os
    >>> from imgutil import imgoptimize
    >>> test_img = '/tmp/test.jpg'
    >>> os.stat(test_img).st_size
    81073
    >>> imgoptimize(test_img, '/tmp/opt.jpg')  # output to /tmp/opt.jpg
    >>> os.stat('/tmp/opt.jpg').st_size
    81026
    >>> imgoptimize(test_img)                  # optimize the original file
    >>> os.stat(test_img).st_size
    81026

### imgresize
- `imgresize(input_filename, width=None, height=None, output_filename=None)`
- It can resize image and preserve aspect ratio.
- It can resize image to specified dimension.

**quick example**

    >>> from imgutil import imgresize
    >>> test_img = '/tmp/test.jpg'    # It is a 1024x768 image
    >>> imgresize(test_img, width=600, output_filename='/tmp/resize.jpg') # /tmp/resize.jpg is 600x450
    >>> imgresize(test_img, height=600, output_filename='/tmp/resize.jpg') # /tmp/resize.jpg is 800x600
    >>> imgresize(test_img, width=100, height=100, output_filename='/tmp/resize.jpg') # /tmp/resize.jpg is 100x100
    >>> imgresize(test_img, width=200, height=400) # /tmp/test.jpg is 200x400 now
