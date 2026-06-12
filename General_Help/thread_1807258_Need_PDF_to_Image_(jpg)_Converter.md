---
title: "Need PDF to Image (jpg) Converter"
date: 2011-07-18
forum: General Help
---

### Post by muscl3s on 2011-07-18
Hi,

Does anyone have any software recommendations in Linux for converting multiple pdf files to .jpegs?  The software I'm currently using is Ghostscript [http://pages.cs.wisc.edu/~ghost/](http://pages.cs.wisc.edu/~ghost/) but I'm wondering if anyone here knows of better alternatives.  

Any feedback much appreciated.

Thanks!

---

### Post by flipper T on 2011-07-18
you can import pdfs into gimp and save as any image format you choose.

whilst in gimp, you can of course manipulate the image in any way you choose.

i know this hasnt addressed doing it in batches, but may still be of interest to you.

---

### Post by SoFl W on 2011-07-18
The convert utility....

convert file.pdf file.jpg 

Not sure if wild-cards will work, try:
convert --help

---

### Post by muscl3s on 2011-07-18
> **flipper T said:**
> you can import pdfs into gimp and save as any image format you choose.

whilst in gimp, you can of course manipulate the image in any way you choose.

i know this hasnt addressed doing it in batches, but may still be of interest to you.

Yea the program has to be able to convert multiple pdfs at a time (100+) to jpg files and resize them.  This will be done on Ubuntu server edition.  I'm just trying to find the best application to get the job done (looking for both efficiency and quality).

---

