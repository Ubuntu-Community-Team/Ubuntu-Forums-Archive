---
title: "need to convert images to pdf"
date: 2010-03-09
forum: General Help
---

### Post by Meow27 on 2010-03-09
i have alot of images that need to be printed into a pdf. 

i am not aware of any software that allows me to do this. and searching on the web is bringing to to alot of propitiatory garbage.

aside from openoffice, what alternatives do i have?

i do not prefer open office because it doesn't let me utilize the whole page smack-off-the-bat.

if it pasted images to the size they were meant to be (the whole page) it would be good enough for me (but its not :( )

the images need to be in a particular order.

---

### Post by richardjh on 2010-03-09
ImageMagick is made for jobs like this.

There are plenty of good sites on this topic but [something like this will]("http://etutorials.org/Linux+systems/pdf+hacks/Chapter+4.+Creating+PDF+and+Other+Editions/Hack+48+Create+a+PDF+Album+of+Your+Digital+Pictures/") get you on your way.

---

### Post by sybille on 2010-03-09
Maybe gscan2pdf will work for you. Although it's primarily for scanning, it can import image files too. You can rearrange page order as needed and then export to PDF.

It's one option, anyway.

---

### Post by kaibob on 2010-03-09
I agree that Imagemagick is a good tool for this. If the source images are JPEG's, be sure to use the "-compress JPEG" option. Otherwise, the PDF's will be huge.

---

### Post by sybille on 2010-03-09
Gscan2pdf uses ImageMagick, by the way.

---

### Post by Meow27 on 2010-03-09
well using imagemagick smack off the bat too way too many resources (2.5 gigs of ram!)

i was using tif images though :x


anyhow Gscan2pdf worked perfectly! it was exactly what i needed


thanks so much guys!

[/solved]

---

