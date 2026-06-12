---
title: "image manipulation in bash scripting"
date: 2010-07-05
forum: General Help
---

### Post by surrealillusions on 2010-07-05
Hi all,

I have a bash script that inserts some text onto every image at a certain place within a directory.

Heres what I have (from a German friend who appears online once in a blue moon), this is the line that resizes to a maximum of 800 either width or height and puts in the text 'text goes here'.

convert ${bild} -resize "800x800>" -strip -family Arial -pointsize 16 -draw "gravity southeast fill rgba(255,0,0, 1.0) text 10,10 'text goes here'" ${dstdir}/${bild}


Now, I would like to know how to place a PNG image (a watermark, so to speak) over all images  within a directory in a certain place, so how would I go about modifying this line to place an image instead of the text?

Thanks.

---

### Post by DaithiF on 2010-07-05
this may help:
[http://joakim.erdfelt.com/wiki/index.php/AddingWatermarksWithImageMagick](http://joakim.erdfelt.com/wiki/index.php/AddingWatermarksWithImageMagick)

---

### Post by surrealillusions on 2010-07-05
Hm...thanks, but it doesn't seem to work.

I tried that small bash script in a .bash file, in the same folder as both the images and the watermark.png but without success.

Typed ./watermark.bash but I get a 'Permission Denied' in Terminal. All files seem to have the right permissions.

---

### Post by DaithiF on 2010-07-05
> **surrealillusions said:**
> All files seem to have the right permissions.
can you post the output of:
```
ls -l watermark.bash 

```please

---

### Post by surrealillusions on 2010-07-05
-rw-r--r--

is that the bit you need?

---

### Post by DaithiF on 2010-07-05
thanks.  yes, and its not executable, which is why you can't run it.
```
chmod +x watermark.bash

```and try it again.

---

### Post by surrealillusions on 2010-07-05
Ah, thx.

Now it works.

Still more problems :D

Although its more to do with how the script is written. It currently produces another watermark.png image, which is locked. Obviously the script will run what its told to do, so how to change it so it adds the watermark.png image to all other images (which are .jpgs), but keep the image name the same, so either overwriting the original image, or (more ideal) to save the new image in a subfolder.

Would I need to change this

composite -gravity SouthEast watermark.png $PNG ${PNG//.png}-watermarked.png

to something like this?

composite -gravity SouthEast watermark.png $PNG ${PNG//.png} ${dstdir}/${bild}

The last bit is obviously from the other script I have, so would it be something similiar?

---

### Post by DaithiF on 2010-07-05
so i guess you have a loop operating on a bunch of files, and each time through the loop $bild contains the name of one particular file.

if so,
```
composite -gravity SouthEast watermark.png $bild $dstdir/$bild
```

---

### Post by surrealillusions on 2010-07-06
Ah, thanks.

Changed the
for PNG in *.png to for JPG in *.jpg

and the echo PNG part to jpg for it to pick up the jpg's, but it says theres a missing image file:

Adding watermark to image1.jpg
composite: missing an image filename `/' @ composite.c/CompositeImageCommand/1609.

Cant find anything on Google about that error. Any idea on what could cause it?

---

### Post by DaithiF on 2010-07-06
can you post your script, thanks

---

### Post by surrealillusions on 2010-07-06
I had to combine the rest of the other script with the watermark.bash script for it to work properly.

Thanks for the help :D

---

