---
title: "display command error"
date: 2012-04-15
forum: General Help
---

### Post by deepaknaik143 on 2012-04-15
i had installed imagemagick 6.7.6 and i tried to run display command but it give error message as below

Version: ImageMagick 6.7.6-5 2012-04-16 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2012 ImageMagick Studio LLC
Features: OpenMP    

Usage: display [options ...] file [ [options ...] file ...]

Image Settings:
  -alpha option        on, activate, off, deactivate, set, opaque, copy
                       transparent, extract, background, or shape
  -antialias           remove pixel-aliasing
  -authenticate password
                       decipher image with this password
  -backdrop            display image centered on a backdrop
  -channel type        apply option to select image channels
  -colormap type       Shared or Private
  -colorspace type     alternate image colorspace
  -comment string      annotate image with comment
  -compress type       type of pixel compression when writing the image
  -define format:option
                       define one or more image format options
  -delay value         display the next image after pausing
  -density geometry    horizontal and vertical density of the image
  -depth value         image depth
  -display server      display image to this X server
  -dispose method      layer disposal method
  -dither method       apply error diffusion to image
  -endian type         endianness (MSB or LSB) of the image
  -filter type         use this filter when resizing an image
  -format string     output formatted image characteristics
  -geometry geometry   preferred size and location of the Image window
  -gravity type        horizontal and vertical backdrop placement
  -identify            identify the format and characteristics of the image
  -immutable           displayed image cannot be modified
  -interlace type      type of image interlacing scheme
  -interpolate method  pixel color interpolation method
  -label string        assign a label to an image
  -limit type value    pixel cache resource limit
  -loop iterations     loop images then exit
  -map type            display image using this Standard Colormap
  -monitor             monitor progress
  -page geometry       size and location of an image canvas
  -profile filename    add, delete, or apply an image profile
  -quality value       JPEG/MIFF/PNG compression level
  -quantize colorspace reduce colors in this colorspace
  -quiet               suppress all warning messages
  -regard-warnings     pay attention to warning messages
  -remote command      execute a command in an remote display process
  -repage geometry     size and location of an image canvas (operator)
  -respect-parentheses settings remain in effect until parenthesis boundary
  -sampling-factor geometry
                       horizontal and vertical sampling factor
  -seed value          seed a new sequence of pseudo-random numbers
  -set property value  set an image property
  -size geometry       width and height of image
  -texture filename    name of texture to tile onto the image background
  -transparent-color color
                       transparent color
  -treedepth value     color tree depth
  -update seconds      detect when image file is modified and redisplay
  -verbose             print detailed information about the image
  -visual type         display image using this visual type
  -virtual-pixel method
                       virtual pixel access method
  -window id           display image to background of this window
  -window-group id     exit program when this window id is destroyed
  -write filename      write image to a file

Image Operators:
  -auto-orient         automagically orient image
  -border geometry     surround image with a border of color
  -clip                clip along the first path from the 8BIM profile
  -clip-path id        clip along a named path from the 8BIM profile
  -colors value        preferred number of colors in the image
  -contrast            enhance or reduce the image contrast
  -crop geometry       preferred size and location of the cropped image
  -decipher filename   convert cipher pixels to plain pixels
  -deskew threshold    straighten an image
  -despeckle           reduce the speckles within an image
  -edge factor         apply a filter to detect edges in the image
  -enhance             apply a digital filter to enhance a noisy image
  -equalize            perform histogram equalization to an image
  -extract geometry    extract area from image
  -flip                flip image in the vertical direction
  -flop                flop image in the horizontal direction
  -frame geometry      surround image with an ornamental border
  -fuzz distance       colors within this distance are considered equal
  -gamma value         level of gamma correction
  -monochrome          transform image to black and white
  -negate              replace every pixel with its complementary color
  -normalize           transform image to span the full range of colors
  -raise value         lighten/darken image edges to create a 3-D effect
  -resample geometry   change the resolution of an image
  -resize geometry     resize the image
  -roll geometry       roll an image vertically or horizontally
  -rotate degrees      apply Paeth rotation to the image
  -sample geometry     scale image with pixel sampling
  -segment value       segment an image
  -sharpen geometry    sharpen the image
  -strip               strip image of all profiles and comments
  -threshold value     threshold the image
  -thumbnail geometry  create a thumbnail of the image
  -trim                trim image edges

Image Sequence Operators:
  -coalesce            merge a sequence of images
  -flatten             flatten a sequence of images

Miscellaneous Options:
  -debug events        display copious debugging information
  -help                print program options
  -list type           print a list of supported option arguments
  -log format          format of debugging information
  -version             print version information

In addition to those listed above, you can specify these standard X
resources as command line options:  -background, -bordercolor,
-borderwidth, -font, -foreground, -iconGeometry, -iconic, -mattecolor,
-name, -shared-memory, -usePixmap, or -title.

By default, the image format of `file' is determined by its magic
number.  To specify a particular image format, precede the filename
with an image format name and a colon (i.e. ps:image) or specify the
image type as the filename suffix (i.e. image.ps).  Specify 'file' as
'-' for standard input or output.

Buttons: 
  1    press to map or unmap the Command widget
  2    press and drag to magnify a region of an image
  3    press to load an image from a visual image directory
display: delegate library support not built-in `' (X11) @ error/display.c/DisplayImageCommand/1908.

---

### Post by sudodus on 2012-04-15
Welcome to the Ubuntu Forums :-)

Did you install imagemagick from the repositories with the terminal window command
```
sudo apt-get install imagemagick
``` or did you download a file and install from it, or did you download a file and compile + install from it?

Unless you know, that you need the latest and greatest features, I recommend the sudo apt-get install method, because you get a version that is tested in your particular version of Ubuntu.

If you need more help, please let us know about your present version of Ubuntu, 11.10 or something else, test with ```
lsb_release -a
``` if you are not sure.

---

### Post by llamabr on 2012-04-15
Also, you only posted the output, not the command you tried.  Tell us what command you typed, and also what you're trying to do.  The output you posted is not an error message.  It's just a help output when you havn't included enough information in your command.

---

### Post by deepaknaik143 on 2012-04-15
i have 11.10 version of ubuntu and i have installed it in my sony vaio i5-64bit processor.
I have installed it from a file by using commands i)./configure ii)make iii)sudo make install...but it fails when i want to display an image through terminal by using the command :    display.

---

### Post by deepaknaik143 on 2012-04-15
now i installed imagemagick by using the command ;     sudo apt-get install imagemagick.
But still when i use the command ;   display in the teminal to display an image it gives the error message as;


display: delegate library support not built-in `' (X11) @ error/display.c/DisplayImageCommand/1908.



so now please give me a strong solution how to fix this froblem and i will be grateful to you....
thanks...

---

### Post by sudodus on 2012-04-16
> **llamabr said:**
> Also, you only posted the output, not the command you tried.  Tell us what command you typed, and also what you're trying to do.  The output you posted is not an error message.  It's just a help output when you havn't included enough information in your command.
+1
Please tell us what command you typed, and also what you're trying to do! Otherwise it is hard to help you.

*Edit: does it work if you use display without options, with only a picture file as parameter? For example*
```
display my-picture.jpg
```

---

### Post by deepaknaik143 on 2012-04-16
yes when i want to run the command 
display flower.png
then it shows the error message as 
display: delegate library support not built-in `' (X11) @ error/display.c/DisplayImageCommand/1908.


and i am doing my thesis work on IMAGE PROCESSING.So it very important to fix this problem as soon as possible

---

### Post by sudodus on 2012-04-16
> **deepaknaik143 said:**
> yes when i want to run the command 
display flower.png
then it shows the error message as 
display: delegate library support not built-in `' (X11) @ error/display.c/DisplayImageCommand/1908.


and i am doing my thesis work on IMAGE PROCESSING.So it very important to fix this problem as soon as possible
I have been using imagemagick a lot in Ubuntu 10.04 LTS and Ubuntu Studio 11.04. I just tried it in 10.04. I can try it in 12.04 beta and post back. This next version will be LTS (long time support), and already a beta stage it is very good :-)

*Edit: I tried it in Ubuntu 11.10 and it works for me. I also tried it in 12.04 beta, where I have several desktops. Right now Unity is not working, but the other desktops work (typical during the development stage).*

---

### Post by sudodus on 2012-04-16
I tried ```
display my-picture.jpg
``` in Ubuntu 11.10 and it works for me. You probably have some bad dependency. Try
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get check
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

sudo apt-get purge imagemagick
sudo apt-get install imagemagick
```
Run one command line each time and watch the output (for errors)

*Edit: By the way, did you remove the first imagemagick package, that you installed? Try to do that too!*

---

### Post by ianhaycox on 2012-04-16
You'll almost certainly have to do a,

```
$sudo make uninstall
```

from the original directory you unpacked imagemagick in.

It look like your are using the version hand installed into /usr/local rather than the apt-get version in /usr/bin

---

### Post by deepaknaik143 on 2012-04-16
i install all the command one by one and now it works.....
many many thanks for your support and now i am so relax...
again thanks alot..

---

### Post by sudodus on 2012-04-16
I'm glad it works for you. Good luck with your thesis :KS

Finally, please click on **[COLOR="Red"]Thread Tools[/COLOR]** at the top of this page and mark this thread as SOLVED!

---

