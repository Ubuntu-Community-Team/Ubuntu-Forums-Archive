---
title: "Gocr"
date: 2009-12-04
forum: General Help
---

### Post by jesuisbenjamin on 2009-12-04
Hello forum,

the following question i had already entailed to [this thread]("http://ubuntuforums.org/showthread.php?t=1333095") but it may be the wrong place after all. So here it comes again:

I am interested in GOCR, but [the Debian Packages link]("http://jocr.sourceforge.net/download.html") is not working. I cannot find GOCR with synaptic. How can i get GOCR or any good OCR program?
(i have to convert large amounts of scanned pages).

Also can it convert roman unicode, or letters with diacritics such as &#257; &#275; ect?

Thanks
B.

---

### Post by hwttdz on 2009-12-04
Why not try compiling from source, their options as far as packages are limited.  To do this you'll likely need to install the package "build-essential".

cd ~
mkdir gocr
wget [http://www-e.uni-magdeburg.de/jschulen/ocr/gocr-0.48.tar.gz](http://www-e.uni-magdeburg.de/jschulen/ocr/gocr-0.48.tar.gz)
tar -xzf gocr-0.48.tar.gz
cd gocr-0.48
./configure
make
sudo make install
cd ~
rm -rf gocr

---

### Post by maximilianyuen on 2009-12-04
> **hwttdz said:**
> Why not try compiling from source, their options as far as packages are limited.  To do this you'll likely need to install the package "build-essential".

cd ~
mkdir gocr
wget [http://www-e.uni-magdeburg.de/jschulen/ocr/gocr-0.48.tar.gz](http://www-e.uni-magdeburg.de/jschulen/ocr/gocr-0.48.tar.gz)
tar -xzf gocr-0.48.tar.gz
cd gocr-0.48
./configure
make
sudo make install
cd ~
rm -rf gocr

i am just a by-passer....randomly ran in to learn terminal

I followed your guided and tried the programme, and find that it's too high level for me...
anyway I tried the programme and I have no need of an OCR

so, how can I uninstall it? 

sorry if I shouldn't make this post

---

### Post by hwttdz on 2009-12-04
To "uninstall", "sudo rm -rf /usr/local/bin/gocr"

---

### Post by maximilianyuen on 2009-12-04
thanks

---

### Post by coffeecat on 2009-12-04
> **jesuisbenjamin said:**
> I cannot find GOCR with synaptic. How can i get GOCR or any good OCR program?

GOCR is in the Universe repository - which should be enabled by default so you should have no problem finding it in Synaptic. Make sure the Universe repository is enabled.

However, the accuracy of gocr is poor. You are much better off with tesseract - also in the Universe repository. You can only use tesseract from the terminal, and there are two limitations you should know about. It will only scan from TIFF images and the file must have the .tif extension. It will error if the file has a .tiff extension.

I don't know about diacritics and tesseract.

---

### Post by jesuisbenjamin on 2009-12-19
hello there,

sorry for this late reply, i was much busy.
My Universe Repositories are enabled but i apt cannot find the packages.
What can i do?

Thanks
B.

---

### Post by coffeecat on 2009-12-19
Which packages? gocr, gocr-tk and various tesseract-ocr-* are all there in Synaptic for me.

---

### Post by jesuisbenjamin on 2009-12-19
OK my mistake.
i needed to type *tesseract-ocr *not *tesseract* alone.
thanks.
B.

---

