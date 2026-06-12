---
title: "Adobe Acrobat pdf capturing in ubuntu?"
date: 2006-03-21
forum: General Help
---

### Post by mtweldon on 2006-03-21
I was wondering if it is possible to install a version of adobe acrobat with the pdf capturing process on it?  Or if there is a good linux alternative to this?  This is about the only feature keeping me from switching from windows to ubuntu at work right now, I have to capture many documents.  Have adobe acrobat standard on the windows machine.

---

### Post by petervk on 2006-03-21
Adobe Acrobat is not needed for pdf creation in Ubuntu. Openoffice.org has a built-in pdf writer and can save any document it can open to pdf. (you can save .doc, .xls, .ppt, and all the openoffice.org formats to pdf)

Also, you can set up a virtual pdf printer in ubuntu and then any application that can print, can also create pdf's. Follow [URL="http://www.ubuntuforums.org/showthread.php?t=140815"]this HOW-TO
[/URL].

Post again if you have any problems.

---

### Post by mtweldon on 2006-03-21
Looking for the Capture process, not change documents into pdf.  The capture process takes a document that is scanned into a pdf and then captures it (makes all of the text highlightable so you can copy/paste it). It is a feature in adobe acrobat standard.

---

### Post by ZylGadis on 2006-03-21
I don't really know what you mean by "highlightable" (isn't that default anyway?) but in evince you can select and copy pdf text. I reckon the same is true for the ubuntu version of acroread. The bad thing about evince is that copied text keeps its formatting, together with end-of-lines.

Edit: just saw you said "scanned." Scanned into pdf? You mean with a scanner? Then you need an OCR (Optical Character Recognition) program, which turns images into text. Maybe Adobe have put one in their thing. I guess you can easily find one for Ubuntu.

---

### Post by mtweldon on 2006-03-21
yup OCR .. or I guess I call it capturing.  Its in Adobe Acrobat Standard :)  do you know of one that is useable in ubuntu?

---

### Post by mtweldon on 2006-03-22
Sorry for the bump, anyone happen to know of any OCR software for ubuntu ?

---

### Post by arnieboy on 2006-03-22
[QUOTE=mtweldon]Sorry for the bump, anyone happen to know of any OCR software for ubuntu ?[/QUOTE]
```
sudo apt-get install gocr-gtk
```
then from terminal run:
```
gtk-ocr
```

---

### Post by mtweldon on 2006-03-22
It said it was unable to find the package when I did that.

---

### Post by arnieboy on 2006-03-22
thats because you dont have universe and multiverse enabled.
```
sudo gedit /etc/apt/sources.list
```
and make it look as follows:
> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse
save and exit
now do:
```
sudo apt-get update
```
followed by the installation instructions outlined above.

---

### Post by mtweldon on 2006-03-22
hmm woops, I forgot this workstation is using hoary and my home pc is using breezy.. doh, so before I do that is there  one for hoary?

---

### Post by mtweldon on 2006-03-23
Working on upgrading to Breezy, will let ya know the results shortly. :)

---

### Post by mtweldon on 2006-03-23
Well the upgrade worked, got the ocr program installed and it dosnt do anything really from what Ive messed around with it, the only thing I can get it to do when I click convert is it renames a new pdf file to .pdf.txt and it is 0 bytes.  I wonder if its possible to use Wine and run Adobe Acrobat Standard with it ?

---

### Post by ZylGadis on 2006-03-23
I have not used that particular program, but ocr programs usually take images as input. Maybe it does not understand pdf? I'd look at the documentation of the program:

```
man gocr-gtk
```

In Synaptic it says:

gocr is a multi-platform OCR (Optical Character Recognition) program.
It can read pnm, pbm, pgm, ppm, some pcx and tga image files.

So, obviously you need to scan your files to something more generic than pdf, or convert the pdf to an image format :) 

Hope that helps.
On the other hand, if the adobe thing works with wine, I see no reason for you not to use it, as you are already used to it. Try it! :) The wine version in the ubuntu reps is really outdated, you want to include wine's own rep (open Synaptic, Settings -> Repositories, Add, Custom, "deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/" without the quotes) and then install it.

---

### Post by mtweldon on 2006-03-23
Thanks for the input, will give it a try once I get back to work tomorrow.

---

### Post by petervk on 2006-03-24
I don't know if there is an easier way to do this, but if you install the imagemagick package:
```
sudo apt-get install imagemagick
```
you can then convert the pdf into png images
```
convert nameofpdf.pdf desiredoutputname.png
```
it will output files:
Page 1: desiredoutputname-0.png
Page 2: desiredoutputname-1.png
etc,

I'm currently trying out gocr-gtk to see if it works on the image files produced.

---

### Post by mtweldon on 2006-03-24
Hmm that would work, except some of my pdfs can have hundreds of pages :(, working on installing adobe with wine, will let ya know if it works.

---

### Post by aysiu on 2006-03-24
[QUOTE=mtweldon]Hmm that would work, except some of my pdfs can have hundreds of pages :(, working on installing adobe with wine, will let ya know if it works.[/QUOTE] If you do end up with 100 .png files, you can probably combine them quite easily:

[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php)

---

### Post by mtweldon on 2006-03-24
Bleh wine is messed up now somehow, when I do winecfg everything is very small and I cannot see any text, not sure what to do it fix it.

---

### Post by petervk on 2006-03-24
Ok, here's what I've tried so far.

Install imagemagick, pdftk, ocrad.

**Take target pdf (original.pdf) and burst into pages**
```

pdftk original.pdf burst

```

[B]Use imagemagick's convert utility to convert page 4 of bursted pdf into *.pgm files.
[/B]```

convert -density 300 pg_0004.pdf image.pgm

```
"-density 300" 
[INDENT]
Means DPI of 300. Be careful with this setting as setting it too high could suck up all your ram and take forever. 300 seems to work for me. I tried 600, but it was taking forever so I killed the process.
Warning: this creates a ~7mb file, if you did it to a set of pdf's you may run out of space.
[/INDENT]
"pg_0004.pdf"
[indent]
The fourth page of the bursted pdf.
[/indent]
"image.pbm"
[indent]
The output filename. Make sure to use *.pgm. 
(*.pbm will also work, but it didn't work as well for me.)
[/indent]
**Use ocrad to reconize the text in the image.**
```

ocrad --layout=2 -o output.txt image.pgm

```
"--layout=2"
[indent]
Layout anaylsis at full.
This is why I'm using ocrad insted of gocr. ocrad has a layout analysis feature that can detect columns and format the output properly. Whereas gocr just melds the columns together into one unreadable mess.
[/indent]

This method works for me. But it's nothing like Adobe's capture. Plain text output is not what most people are looking for. Using wine & adobe acrobat is probably the easiest way. (that is if it runs under wine)

---

### Post by mtweldon on 2006-03-24
any idea of how to fix my wine?  Everything is unreadable

---

### Post by petervk on 2006-03-24
I'm not too good for wine problems. Search the forum for that. If you can't find anything start a new thread detailing your problem.

When it happened, what you did before it happened, what you tried to fix, etc.

---

