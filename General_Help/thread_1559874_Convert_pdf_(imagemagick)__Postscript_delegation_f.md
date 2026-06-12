---
title: "Convert pdf (imagemagick) : Postscript delegation failed"
date: 2010-08-24
forum: General Help
---

### Post by pseudomino on 2010-08-24
Hello,
When I try converting a pdf in jpeg files, I get this error :
```
domino@domino-desktop:~$ convert Foundation.pdf Foundation.jpg
^Cconvert: Postscript delegation failed `Foundation.pdf': No such file or directory.  @ pdf.c/ReadPDFImage/634.
convert: missing an image filename `Foundation.jpg' @ convert.c/ConvertImageCommand/2838.
```(The path to the file Foundation.pdf is good.)

I tried to reinstall Imagemagick, but with no success!

I checked the convert config and I see that DELEGATES don't have "gs". However, "ghostscript" seems installed in Synaptic !

Please help

I'm on Lucid.

---

### Post by pseudomino on 2010-08-25
up ?

---

