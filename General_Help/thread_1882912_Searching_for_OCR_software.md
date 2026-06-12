---
title: "Searching for OCR software"
date: 2011-11-18
forum: General Help
---

### Post by rahulzz on 2011-11-18
dear friends,

I just started to use ubuntu i need a software i searched for it for last 2 days but i cant find such a tool so suggest me a software to do the following

I want to convert A image OR PDF to text .  ( OCR tool is the software can be used in windows )
In other words PDF to ascii or Image to Ascii plz provide such a software

---

### Post by jjex22 on 2011-11-18
well if you've got a windows tool you really love try running it under wine - either from the software centre, or open a terminal and type

sudo apt-get install wine

Wine runs lots of (but not quite all) windows programs in linux - very useful tool.

for open source ocr please read

[ubuntu]("https://help.ubuntu.com/community/OCR")

[Independent]("http://code.google.com/p/easy-ocr/") 

By the way welcome to the forums!):P

---

### Post by WasMeHere on 2011-11-18
Hi rahulzz,

Try pdftotext! It is in the repositories. You install it from the terminal ctrl + alt +t with the command
```
sudo apt-get install pdftotext
```
I have not used any OCR software (yet). Browse the internet for ***linux OCR***
You may find what you need to read from picture files that way.

Have fun finding out about Ubuntu :-)

Olle

---

### Post by ajgreeny on 2011-11-18
Version 3 of tesseract which can be installed from a ppa is getting much better than the old version from the standard repos, and is much less fussy about the format of the image on which the OCR is carried out.

I am using Lucid 10.04, and the tesseract v3 for that comes from [http://ppa.launchpad.net/alex-p/notesalexp/ubuntu](http://ppa.launchpad.net/alex-p/notesalexp/ubuntu) so have a look and you may find that it is also available for later Ubuntu versions.  It is a command line application, but very easy to use with the simple command ```
tesseract image.tif outfilename
```Do not add the .txt file suffix to the outfilename or it can confuse the system.

---

### Post by Jacobonbuntu on 2011-11-18
...also scan2pdf is handy, you can combine it with several ocr engines, available in the repositories (including the ones already mentioned).

* handy to install synaptic, if you didn't do that already, there you can make your own choice of ocr engines

---

### Post by NikolayKhl on 2011-11-21
You may want to look at [ABBYY OCR for Linux]("http://ocr4linux.com"). It provides a really simple CLI interface, here’s how it works:

*abbyyocr [open image and analysis options] -if <image file> [export options] -of <export file>*

All options are very flexible and nicely described in documentation at ocr4linux.com. It’s not free, but it provides the best quality of OCR. For example check out [http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison](http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison), or try it yourself, trial can be requested [here]("http://ocr4linux.com/en:trial"). If you are concerned about OCR quality, you should try it out. 

I work @ ABBYY and can provide you additional info if necessary. Feel free to contact me if you have any questions.

---

