---
title: "Broken libtiff libraries"
date: 2006-05-17
forum: General Help
---

### Post by Jimorie on 2006-05-17
A few days ago I noticed that my libtiff libraries aren't working anymore. I vaguely recall the Ubuntu updater updated these libraries some week ago or so. Correct?

The problems I get is when using for example the ImageMagick tool convert or the libtiff tool tiffcp:

> convert file.jpg file.tiff
convert: tif_jpeg.c:1505: JPEGCleanup: Assertion `sp != 0' failed.
Aborted

> tiffcp -c jpeg:r:50 file.tiff file.jpg
tiffcp: tif_jpeg.c:1505: JPEGCleanup: Assertion `sp != 0' failed.
Aborted

I have tried compiling and installing other versions of libtiff, both more recent and older than the 3.7.3 version installed by Ubuntu - but without any results. I also tried re-installing libjpeg and ImageMagick. And now I'm out of things to test. I really need these tools to work for me. Does anyone have a clue?

Thanks!

---

### Post by slimdog360 on 2006-05-17
I could be wrong but the line
sudo apt-get -f install
has worked for me a couple of times when things go wrong, perhaps im completely worng and this is used for something else though.

---

### Post by Jimorie on 2006-05-17
[quote="slimdog360"]sudo apt-get -f install[/quote]
Yep, but it just tells me it needs to do nothing. But thanks for the reply. =)

---

