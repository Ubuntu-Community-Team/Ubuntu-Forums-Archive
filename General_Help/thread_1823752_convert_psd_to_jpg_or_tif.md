---
title: "convert psd to jpg or tif"
date: 2011-08-12
forum: General Help
---

### Post by qwertyjjj on 2011-08-12
What program can I use to convert a PDF file to a JPG image?

I tried convert on 1 PDF but it moves some of the text in odd places.

---

### Post by papibe on 2011-08-12
Gimp. It is in the software center.

Regards.


EDIT: Gimp is a powerful graphical tool, but in this case is like a to use 'tank to kill a fly'.

Try this in the command line:
```
$ convert file.pdf file.jpg
```
It will create a jpg file for each page.

---

### Post by qwertyjjj on 2011-08-12
> **papibe said:**
> Gimp. It is in the software center.

Regards.


EDIT: Gimp is a powerful graphical tool, but in this case is like a to use 'tank to kill a fly'.

Try this in the command line:
```
$ convert file.pdf file.jpg
```
It will create a jpg file for each page.

I did that in the command line but it moves some of the text in the right hand column slightly out in the jpg

---

### Post by papibe on 2011-08-12
Did you try Gimp?

Regards.

---

### Post by TheGuvernor on 2011-08-12
Hi ImageMagick has this capability. Look in the Ubuntu software center to see if you have it installed. If not you can easily install it from there if you'd like.

---

### Post by qwertyjjj on 2011-08-13
> **papibe said:**
> Did you try Gimp?

Regards.

Gimp converts it correctly but ImageMagick doesn't.
Thanks

---

