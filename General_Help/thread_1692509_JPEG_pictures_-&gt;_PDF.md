---
title: "JPEG pictures -&gt; PDF"
date: 2011-02-21
forum: General Help
---

### Post by Godspell on 2011-02-21
Hi there folks,

I've got a set of scanned pictures that I'd like to convert into one PDF file but I really don't know how to do so. I've searched on the Internet but found nothing.

Could you please give me some suggestions?
These are fairly important pictures so it would be great if I could get any software that is quite reliable :)

Cheers and regards,
GS

---

### Post by Script Warlock on 2011-02-21
cd to the folder where you put the image and try this in the terminal:

cd Pictures 
convert sample_image.jpg somename.pdf

---

### Post by cjhabs on 2011-02-21
> **Script Warlock said:**
> cd to the folder where you put the image and try this in the terminal:

cd Pictures 
convert sample_image.jpg somename.pdf

Just make sure you have imagemagick installed as that is where the convert command comes from. There are LOTS of options you can pass to the convert command.

---

### Post by keithpeter on 2011-02-21
Hello All

Imagemagic is ace

Alternative low rent solution is to import the images into OpenOffice Impress one by one (with any captions you want) then to export the lot as a PDF. Not as elegant as the imagemagic route.

---

### Post by Godspell on 2011-02-21
> **cjhabs said:**
> Just make sure you have imagemagick installed as that is where the convert command comes from. There are LOTS of options you can pass to the convert command.

Using ImageMagick, how do I convert a batch of pictures into one PDF? Like this?
```
cd Pictures 
convert image1.jpeg, image2.jpeg, and so on... somename.pdf
```
Or is there another command?

> Alternative low rent solution is to import the images into OpenOffice  Impress one by one (with any captions you want) then to export the lot  as a PDF. Not as elegant as the imagemagic route. 	

I think I'll stick with imagemagick, mate. I tried the OpenOffice thing but it just seems to be harder as there is no batch import for pictures.

Thank you all for your suggestions :)

Regards,
GS

---

### Post by Script Warlock on 2011-02-21
convert "*" somename.pdf

---

### Post by Godspell on 2011-02-21
> **Script Warlock said:**
> convert "*" somename.pdf

Thanks for replying and it partially worked.
Trouble is, although the file names are in order, it brings up the last page to the first page.

Is there a way to enforce the conversion in the order that files are named?

Cheers and regards,
CS

---

