# TESTIMAGES

     Name          : TESTIMAGES
     Version       : 4.0.000
     Starting date : 2011-04-03
     Release date  : 2014-10-17
     Author        : Nicola Asuni

Copyright (c) 2011-2017:

    Nicola Asuni
    Tecnick.com LTD
    www.tecnick.com
    info@tecnick.com


## License

Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)

 * HUMAN-READABLE SUMMARY: http://creativecommons.org/licenses/by-nc-sa/4.0/
 * LEGAL CODE (THE FULL LICENSE): http://creativecommons.org/licenses/by-nc-sa/4.0/legalcode
 * See the [LICENSE](LICENSE) file for more information.


## URL

https://testimages.org


## Cite

Please cite the following papers when using any image in this archive:

* ASUNI N, GIACHETTI A, "[TESTIMAGES: A Large Data Archive For Display and Algorithm Testing](http://www.tandfonline.com/doi/abs/10.1080/2165347X.2015.1024298?journalCode=ujgt21)", Journal of Graphics Tools, Volume 17, Issue 4, 2015, pages 113-125, DOI:10.1080/2165347X.2015.1024298
* ASUNI N, GIACHETTI A, "[TESTIMAGES: a large-scale archive for testing visual devices and basic image processing algorithms](https://nicola.asuni.xyz/papers/20140923_STAG_ASUNI_TESTIMAGES.pdf)", STAG - Smart Tools & Apps for Graphics Conference, 2014.

Please note that since the original publication the SAMPLING and SAMPLING_PATTERNS archives where updated to start from the 2400 pixels resolution instead of 1200 pixels.

## Description

To avoid common issues related to the use of images with unknown origin or protected by restrictive copyright or license, all the images in the TESTIMAGES archive are copyrighted by Nicola Asuni and distributed under the Creative Commons license "Attribution-NonCommercial-ShareAlike 4.0 International" (CC BY-NC-SA 4.0).

All images were generated using a range of custom Octave/MATLAB software scripts specifically written for this purpose to guarantee the precise positioning and value of every pixel. The same image is generally available in 8bpp and 16bpp (bit-per-pixel or bit-dept) in 3-Channel Red-Green-Blue (RGB) and 1-Channel Grayscale format.

The 8bpp images were always generated by their 16bpp counterparts by normalizing the intensity values.

In the SAMPLING dataset the Grayscale images were obtained by their RGB counterparts by applying the SMPTE 295M-1997 standard coefficients to the RGB intensities:

	Gray = (0.2126 * Red) + (0.7152 * Green) + (0.0722 * Blue)

The images were saved using the patent-free Portable Network Graphics (PNG) format and optimized using OptiPNG.

In the PATTERNS dataset, to achieve a good quality anti-aliasing effect, the intensity value of the pixels is always proportional to the portion of the pixel covered by the maximum intensity surface.

The images are generally organized in folders and subfolders, where every folder indicates one common feature of the contained images (i.e. bit-depth, number of channels, resolution). Due to the large size of the archive, the images are aggregated for common features and compressed using bzip2.

The file names of the individual images are designed to follow a common pattern:

	img_[W]x[H]_[NCH]x[BPP]bit_[EX].png

where:

	[W]   : image width in pixels or number of image columns;
	[H]   : image height in pixels or number of image rows;
	[NCH] : number of channels or primary colors (i.e.: 1 for grayscale, 3 for RGB);
	[BPP] : bit-per-pixel for each channel (also know as color depth or bit depth);
	[EX]  : extra information used to identify the specific image, as described in the later chapters.

This common pattern makes it easy to select images with specific charateristics.

In the following sections we will only refer to the [EX] portion of the file name.


### SAMPLING

The main purpose of this dataset is providing natural images to test resampling algorithms (i.e. interpolation, zooming, enlargment and superresolution).
This dataset uniquely provides a base of 40 RBG 2400x2400 reference images with a bit-depth of 16bpp and high dynamic range (HDR).
The reference images were processed to obtain different sub-resolutions and variation with 8bpp and grayscale, for a total of more 220K images.

The test images were chosen to be square for simplicity and symmetry.
The value 2400 was chosen because it is approximately the vertical resolution of a common 10 Megapixel SLR Camera, it is the vertical resolution of standard WQUXGA displays and can be divided by 2, 3, 4, 5, 6, 8, 10, 12, 15, 16, 20 and 24 (reduction factors).

Since currently there are no 16bpp capable photographic cameras in the consumer market, to acquire 16bpp natural images an approach involving multiple exposures was used.

This archive contain 40 16bpp RGB "uncropped" images with a resolution of 2448x2448 pixels. A border of 24 pixels was further cropped from these images to get the reference resolution of 2400x2400 pixels, so the top left pixel in the reference image correspond to the pixel in position (25,25) of the uncropped image.

For each reference image, additional resized images were generated.
The intensity value of each pixel in the resized image was obtained by averaging the values of RxR sub-arrays (where R is the reducing factor).
The reduction factors were chosen to perfectly divide the 2400 width and height values of the reference images:

  Reduction     Resolution      Variations
   factor    [Width x Height]    (shifts)

      1         2400x2400             1
      2         1200x1200             9
      3          800x800             25
      4          600x600             49
      5          480x480             81
      6          400x400            121
      8          300x300            225
     10          240x240            361
     12          200x200            529
     15          160x160            841
     16          150x150            961
     20          120x120           1521
     24          100x100           2209


The resized images were always generated starting from the uncropped image but always cosidering a sub-sampling mask of 2400x2400 pixels at the time.
For each resizing resolution, all the possible variations obtained by moving (shifting) the sub-sampling mask were saved.
The image names contain a shifting indicator, a string composed by two groups of one letter and two numbers. The letters indicates the direction of the shift (C: center, T: top, B: bottom, L: left, R: right) while the numbers indicate the number of pixels. The images aligned with the reference image, or the pixel in position (25,25) of the uncropped image, are identified by the "C00C00" shifting indicator.


### SAMPLING_PATTERNS

This is an extension of the SAMPLING archive containing 424 artificial Grayscale reference images, generated as described in the PATTERNS section for the 2448x2448 pixels resolution.
The main purpose of this dataset is to test in isolation specific features of resampling algorithms.


### COLOR

The main purpose of this dataset is providing images to test the color rendering on different displays and facilitate color adjustments.

This and the PATTERNS archive contain 8bpp and 16 bpp (bit-per-pixel) 3-Channel Red-Green-Blue (RGB) images for the following 114 standard and non-standard resolutions for computer monitors, televisions, cinema projectors, mobile phone screens, camera sensors and other generic displays:

100x100, 120x120, 150x150, 160x120 QQVGA, 160x128, 160x144, 200x160, 200x200, 208x176, 220x176, 226x170, 230x172, 240x160 HQVGA, 240x180, 240x240, 300x300, 320x200 CGA, 320x240 QVGA, 320x256, 352x288 CIF, 360x240 WQVGA, 384x240 WQVGA, 384x288 SIF, 400x240 WQVGA, 400x400, 416x352, 420x292, 432x240 FWQVGA, 480x272 WQVGA, 480x320 HVGA, 480x360, 512x342, 512x384, 528x436, 600x600, 640x200, 640x256, 640x350, 640x360 nHD, 640x400, 640x480 VGA, 640x512, 720x348 Hercules, 720x350 MDA, 720x480 WVGA, 720x576, 768x576 PAL, 800x480 WVGA, 800x600 SVGA, 832x624 SVGA, 854x480 FWVGA, 864x480, 960x540 qHD, 960x640 DVGA, 984x738, 1024x480, 1024x600 WSVGA, 1024x768 XGA, 1136x640, 1152x768 WXGA, 1152x864 XGA+, 1152x870, 1152x900, 1200x824, 1200x1200, 1280x720 HD720, 1280x768 WXGA768, 1280x800 WXGA800, 1280x854, 1280x960 SXGA-, 1280x1024 SXGA, 1360x768, 1366x720, 1366x768, 1440x900 WXGA+, 1440x960 WSXGA, 1400x1050 SXGA+, 1600x768, 1600x900 HD+, 1600x1200 UXGA, 1680x944, 1680x1050 WSXGA+, 1920x1080 FHDTV, 1920x1200 WUXGA, 1920x1440, 2048x1050, 2048x1080 2K DC, 2048x1152 QWXGA, 2048x1536 QXGA, 2560x1440 WQHD, 2560x1600 WQXGA, 2560x2048 QSXGA, 2880x1620, 2880x1800 QWXGA+, 3200x1800 WQXGA+, 3200x2048 WQSXGA, 3200x2400 QUXGA, 3840x2160 4K SHDTV, 3840x2400 WQUXGA, 4096x2160 4K DC, 4096x2560 4K, 4096x3072 HXGA, 5120x2880 UHD+, 5120x3200 WHXGA, 5120x4096 HSXGA, 6400x4096 WHSXGA, 6400x4800 HUXGA, 7680x4320 8K FUHDTV, 7680x4800 WHUXGA, 8192x4320 8K DC, 8192x4608, 10000x7000 IMAX, 15360x8640 16K QUHDTV, 16384x8640 16K DC.

These resolutions include the ones used for the SAMPLING dataset and the ones proposed as standards for very high resolution television and digital cinema.

For every resolution listed above and for both 8bpp and 16bpp, the following 7 images were generated:

* **color_bars_CMYKWRGB** : Eight vertical bars at maximum intensity (255 for 8bpp and 65535 for 16bpp) representing different colors in the following order:  Cyan (Green + Blue), Magenta (Red + Blue), Yellow (Red + Green), Black, White (Red + Green + Blue), Red, Green, Blue.
* **color_bars_CMYKWRGB_100IRE** : Variation of the color_bars_CMYKWRGB where the minimum intensity level is set to 7.5IRE (16 for 8 bit, 4096 for 16 bit) and the maximum intensity level is set to 100IRE (235 for 8 bit, 60160 for 16 bit).
* **color_bars_CMYKWRGB_75IRE** : Variation of the color_bars_CMYKWRGB where the minimum intensity level is set to 7.5IRE (16 for 8 bit, 4096 for 16 bit) and the maximum intensity level is set to 75IRE (180 for 8 bit, 46144 for 16 bit).
* **color_bars_CMYKWRGB_gradient** : Variation of the color_bars_CMYKWRGB where intensity levels varies linearly from top 0% to bottom 100%.
* **color_rainbow** : Six vertical color sections with the following intensity variations to obtain a "rainbow" effect: 1. red=MAX, green=0 to MAX, blue=0; 2. red=MAX to 0, green=MAX, blue=0; 3. red=0, green=MAX, blue=0 to MAX; 4. red=0, green=MAX to 0, blue=MAX; 5. red=0 to MAX, green=0, blue=MAX; 6. red=MAX, green=0, blue=MAX to 0.
* **color_rainbow_gradient** : Variation of the color_rainbow where intensity levels varies linearly to obtain a black to white variation from top to bottom.
* **color_SMPTE_RP_219_2002** : This image is generated as described in SMPTE RP 219:2002 and resized to perfectly match different resolution.


### PATTERNS

The main purpose of this dataset is providing images to test the rendering of standard geometrical patterns by displays, monitors, televisions and projectors.
These patterns facilitate the adjustment of geometrical parameters and helps identify defects of the rendering device.
The broad range of simple geometrical patterns also helps to optimize or identify specific issues in some image processing algorithms.
For example, by verifying if the patterns are preserved when applying an image compression algorithm, by testing the effects of different texture filtering and resampling approaches programmed in shaders, or by evaluating the printing quality of a particular device.

This archive contains 8bpp and 16bpp (bit-per-pixel) 3-Channel Red-Green-Blue (RGB) images for the 114 standard and non-standard resolutions previously listed in the COLOR dataset.

For every resolution listed above, the following image variations were generated:

**GRAY**: (1-Channel Grayscale) These are the reference images containing the geometric patterns as described below. These images are then used to generate the following 3-Channel RGB variations by copying the grayscale layer in one or more color channel: **RED**, **GREEN**, **BLUE**, **RED_GREEN**, **RED_BLUE**, **GREEN_BLUE**, **RED_GREEN_BLUE**.


For every resolution, color variation and for both 8bpp and 16bpp, the following image types and variations were generated:

* **bars_[ORIENT]_[TYPE]_[BW]_[PHASE]xhalfPI** : Constant size bars with the following characteristics: [ORIENT] bars orientation (vertical, horizontal); [TYPE] intensity curve perpendicular to the bar orientation (square = step curve; sin = sinusoidal; triangle = sawtooth wave); [BW]  witdh of an entire curve period - the bars period is always a power of 2; [PHASE] the curve phase expressed in number of PI/2 (0-3).      
* **bars_[ORIENT]_[TYPE]_progressive** : Variable size bars. The smallest bars starts at the image center and increase their size as power of 2. The variation option are: [ORIENT] bars orientation (vertical,horizontal); [TYPE] intensity curve perpendicular to the bar orientation (square = step curve; sin = sinusoidal; triangle = sawtooth wave).
* **grid_square_progressive** : Grid of rectangles obtained by combining (XOR) the bars_horizontal_square_progressive and bars_vertical_square_progressive images.
* **bars_45deg_tlbr_[BW]** : Solid bars oriented at 45 degrees, from top-left to bottom-right. [BW] is the witdh of an entire curve period; the bars period is always a power of 2.
* **bars_45deg_bltr_[BW]** : Solid bars oriented at 45 degrees, from bottom-left to top-right. [BW] is the witdh of an entire curve period; the bars period is always a power of 2.
* **rectangles_concentric_[BW]_0** : Concentric rectangles. [BW] is the witdh of the rectangle border (power of 2).
* **rectangles_concentric_[BW]_1** : Inverse of rectangles_concentric_[BW]_0.
* **grid_rectangle_[BW]x[BH]_0** : Grid with alternate black and white rectangles with the [BW] width and [BH] height. The rectangles dimensions [BW] and [BH] are chosen to perfectly fit the available image space. The image width is a multiple of 2 x [BW] and the image height is a multiple of 2 x [BH].
* **grid_rectangle_[BW]x[BH]_1** : Inverse of grid_rectangle_[BW]x[BH]_0.
* **diagonal_[CORNER]** : Diagonal that divides the images in black and white parts. The [CORNER] values are: tl=top-left, tr=top-right, br=bottom-right, bl=bottom-left.
* **grid_triangle_a_[BW]x[BH]_0** : Grid obtained by combining triangles to form black and white rhombus. The rectangles dimensions [BW] and [BH] are chosen to perfectly fit the available image space, the image width is a multiple of 2 x [BW] and the image height is a multiple of 2 x [BH].
* **grid_triangle_a_[BW]x[BH]_1** : Inverse of grid_triangle_a_[BW]x[BH]_0.
* **grid_triangles_b_[BW]x[BH]_0** : Grid obtained by combining triangles in alternate black and white positions. The rectangles dimensions [BW] and [BH] are chosen to perfectly fit the available image space. The image width is a multiple of 2 x [BW] and the image height is a multiple of 2 x [BH].
* **grid_triangles_b_[BW]x[BH]_1** : Inverse of grid_triangles_b_[BW]x[BH]_0.
* **grid_lines_cross_0** : Central white cross in a black background. The line width is always 2 pixels wide to result perfectly centered when the correspondent resolution dimension is even.
* **grid_lines_cross_1** : Inverse of grid_lines_cross_0.
* **grid_line_45deg_0** : Grid obtained by combining (XOR) the four 45 degrees diagonal surfaces crossing each image corner.
* **grid_line_45deg_1** : Inverse of grid_line_45deg_0.
* **grid_lines_quarters_0** : Grid obtained by dividing the image in 4x4 rectangles using white lines over a black background.   
* **grid_lines_quarters_1** : Inverse of grid_lines_quarters_0.
* **grid_line_thirds_0** : Grid obtained by dividing the image in 3x3 rectangles using white lines over a black background
* **grid_line_thirds_1** : Inverse of grid_line_thirds_0.
* **grid_line_intersections_0** : Grid obtained using four 45 degrees lines passing in each image corner, and horizontal and vertical lines passing in each intersection.
* **grid_line_intersections_1** : Inverse of grid_line_intersections_0.
* **rays_radial_corner_[CORNER]** : Alternating black and white ray lines starting at image edge positions covering an angle of 1 degree each. The [CORNER] values are: tl=top-left, tr=top-right, br=bottom-right, bl=bottom-left, t=top, b=bottom, l=left, r=right.
* **rays_radial_allcorners** : Grid obtained combining (XOR) the images rays_radial_corner_tl, rays_radial_corner_tr, rays_radial_corner_br, rays_radial_corner_bl.
* **rays_radial_center** : Alternating black and white ray lines starting at image center covering an angle of 1 degree each.
* **circles_corner_[CORNER]_[BW]** : Alternating black and white concentric circles with constant [BW] tickness, centered in one of the image corners. The [CORNER] values are: tl=top-left, tr=top-right, br=bottom-right, bl=bottom-left, t=top, b=bottom, l=left, r=right.
* **circles_progressive_a_corner_[CORNER]** : Alternating black and white concentric circles with variable tickness, centered in one of the image corners.
* **circles_progressive_b_corner_[CORNER]** : Variation of the circles_progressive_a_corner_[CORNER].
* **grid_circles_progressive_a** : Grid obtained combining (XOR) all the circles_progressive_a_corner_[CORNER] images.
* **grid_circles_progressive_b** : Grid obtained combining (XOR) all the circles_progressive_b_corner_[CORNER] images.
* **circles_center_[BW]** : Alternating black and white concentric rings with constant ([BW] / 2) tickness.
* **gray_level_crossing** : Uniform intensity transition form zero to maximum value, from left to right in the upper half image and from right to left in the lower half image.
* **gray_level_bits** : The vertical space is divided in 16 rows representing intensity quantization from 1 bit (top row - 2 values) to 16 bit (bottom row - 65536 values). In the 8bpp variation of this image, due to the normalization, the rows from 9 to 16 are identical to the row 8.
* **gray_level_all** : Uniform transition from zero to maximum intensity, distribuited across all pixels from left to right and from top to bottom.
* **color_full** : All pixels are set to the maximum intensity value.
* **color_16th** : The horizontal space is divided in 16 vertical bars representing intensity variation from zero (black) to maximum value (white).


### OLD_SAMPLING

The OLD_SAMPLING ARCHIVE is deprecated, please use the new SAMPLING archive instead.
