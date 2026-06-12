---
title: "increase image size without quality loss."
date: 2010-02-26
forum: General Help
---

### Post by kmsalex on 2010-02-26
is there a way to zoom in on an image with out as much blur as normal?

---

### Post by joep-vd on 2010-02-26
What do you mean? Are you looking for a way to make the DPI of the images larger, or do you have complaints about the viewer you are using? If so, which?

---

### Post by kmsalex on 2010-02-26
no complainants, I'm also no expert in this area so DPI is over my head, i was wondering if there is a way to take a given image and be able to zoom in or enlarge it, like making a cell phone pic large or zooming in on the background of pic to try and make out an object.

---

### Post by joep-vd on 2010-02-27
Try toying around with Gimp (it's either already installed or available through synaptic. 

But in general: You cannot get around the resolution of your source file, see [http://en.wikipedia.org/wiki/Image_resolution](http://en.wikipedia.org/wiki/Image_resolution)

Good luck!

---

### Post by Vaphell on 2010-02-27
true that, you can't get more information than the original image provides.
Enlarging image is simply about guessing what color should fill the blanks between the 'old' pixels and empty spaces are filled with some kind of average of the adjacent pixels of original image. Zooming in in file previews does exactly same thing.

Don't believe anything you see in CSI - it spreads a lot of bullsh!t with their 'get image from crappy web camera and zoom 10 pixel big image of the guy so you can see what company made his wristwatch' :-)

---

### Post by NightwishFan on 2010-02-27
Raster images cannot be losslessly resized. Vector images (.svg) can but they are only suitable for logos and graphics.

The default settings to resize on Gimp tries to minimize quality loss.

[http://en.wikipedia.org/wiki/Raster_image](http://en.wikipedia.org/wiki/Raster_image)
[http://en.wikipedia.org/wiki/Vector_image](http://en.wikipedia.org/wiki/Vector_image)

---

### Post by Mark Phelps on 2010-02-27
We see this all the time in movies and on TV where they show a picture of a large area (say a neighborhood from a satellite shot) and then "magically" zoom in to read the writing on a credit card!

That's Movie/TV magic -- it's not real.

In the real world, a graphics image has a fixed number of pixels.  You can make the image larger -- as in printing a photo image intended for 4x6 paper on 8x10 paper -- but when you do this, all you will see is that the pixels themselves get larger.

If this is what you mean by getting "fuzzy", that's a limitation due to the fixed number of pixels.

There may be apps out there that will attempt to do interpolation -- increasing the number of pixels and then guessing what goes in the new ones based on the existing ones -- and that will somewhat aleviate the fuzziness -- but you still won't get the magical effect that the movies/TV show.

---

### Post by kmsalex on 2010-02-27
I figured there probly was't a way to do this, but i thought i'd ask anyway. 
thanks every one.

---

