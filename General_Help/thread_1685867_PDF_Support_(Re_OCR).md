---
title: "PDF Support (Re: OCR)"
date: 2011-02-11
forum: General Help
---

### Post by xtremezj on 2011-02-11
I have spent the last few days doing a lot of searching for Linux solutions for using OCR in PDF's. From everything I have read it requires scripts, converting, etc and quite honestly is far too much effort with everything else I have to do when trying to get my assignments done for 6 classes.

My question is has anyone released a PDF reader in more recent times that supports OCR? I have installed and tried so much stuff. I was honestly hoping OpenOffice would support it, but don't see it there either.

How come there is such a lacking support for this?

---

### Post by Grenage on 2011-02-11
In my experience, there isn't a great demand for OCR software.  If it's scanning a printed document, then a digital copy likely exists already; if it's hand-written, then I've yet to see software that was any good at interpreting it.

There are some good options and comparisons here:

[http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison](http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison)

---

### Post by manclip on 2011-02-11
> **xtremezj said:**
> I have spent the last few days doing a lot of searching for Linux solutions for using OCR in PDF's. From everything I have read it requires scripts, converting, etc and quite honestly is far too much effort with everything else I have to do when trying to get my assignments done for 6 classes.

My question is has anyone released a PDF reader in more recent times that supports OCR? I have installed and tried so much stuff. I was honestly hoping OpenOffice would support it, but don't see it there either.

How come there is such a lacking support for this?

I did read that libreoffice supports pdf files. Did you tried libreoffice?

---

### Post by xtremezj on 2011-02-11
> **Grenage said:**
> In my experience, there isn't a great demand for OCR software.  If it's scanning a printed document, then a digital copy likely exists already; if it's hand-written, then I've yet to see software that was any good at interpreting it.

There are some good options and comparisons here:

[http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison](http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison)

I'll take a look at that. The problem with scanned documents is some of my professor's use them exclusively from self generated material, or original documents we can't get our hands on. Since I am a Psychology major it's a **lot** of reading and I can't search it.

---

### Post by xtremezj on 2011-02-11
> **manclip said:**
> I did read that libreoffice supports pdf files. Did you tried libreoffice?

Lots of things support PDF, it's the OCR thats missing.

---

### Post by Grenage on 2011-02-11
> **xtremezj said:**
> I'll take a look at that. The problem with scanned documents is some of my professor's use them exclusively from self generated material, or original documents we can't get our hands on. Since I am a Psychology major it's a **lot** of reading and I can't search it.

I feel your pain; unfortunately I mis-read your original post, and the link I gave you refers to document formats other than PDF.  If I come across anything that looks suitable, I'll post back.

---

### Post by xtremezj on 2011-02-11
Thanks man

---

### Post by Grenage on 2011-02-11
If your main issue in PDFs that can't be searched (images), this looks like it might be an [option]("http://www.ubuntugeek.com/howto-make-scanned-pdfs-searchable-ocr-using-pdfocr.html").  It still requires a command line, but one could probably make a simply script that converts all documents in a folder (and runs with a link/shortcut).

---

### Post by xtremezj on 2011-02-11
Sweet man, I'll read up on that today and let you know how it works out

---

### Post by ajgreeny on 2011-02-11
There are also some online ocr sites which can "scan and ocr" your pdf files making them into text or word docs, eg
[http://www.newocr.com/](http://www.newocr.com/)
[http://www.onlineocr.net/default.aspx](http://www.onlineocr.net/default.aspx)
I have used both just to try them out with a variety of image formats and they seem very good and accurate, though I think there are number of document limits per user unless you pay or are registered.

I am also now using tesseract v3 for any ocr I do locally.  It is superbly accurate in comparison with gocr, which I find a waste of time generally.  You could always open your pdf files in gimp and save them as tif files to use tesseract in order to make searchable txt files.  A bit of a palaver, but technically possible.

---

### Post by lud666 on 2011-02-11
The only reliable ocr I have found for ubuntu is tesseract and you have to convert pdf to tiff. Works well, but not as good as convincing my wife to just type the stuff manually.

[https://help.ubuntu.com/community/OCR]("https://help.ubuntu.com/community/OCR")

---

### Post by xtremezj on 2011-02-11
> **ajgreeny said:**
> There are also some online ocr sites which can "scan and ocr" your pdf files making them into text or word docs, eg
[http://www.newocr.com/](http://www.newocr.com/)
[http://www.onlineocr.net/default.aspx](http://www.onlineocr.net/default.aspx)
I have used both just to try them out with a variety of image formats and they seem very good and accurate, though I think there are number of document limits per user unless you pay or are registered.

I am also now using tesseract v3 for any ocr I do locally.  It is superbly accurate in comparison with gocr, which I find a waste of time generally.  You could always open your pdf files in gimp and save them as tif files to use tesseract in order to make searchable txt files.  A bit of a palaver, but technically possible.

I can open PDF in GIMP? Oh see this is good news. That makes tesseract the best option. I gotta try it.

---

### Post by xtremezj on 2011-02-11
ok i got tesseract installed after some playing with the compiler, but no idea how to run it

---

### Post by ajgreeny on 2011-02-11
I recommend you install tesseract v3 from the ppa [https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp) making sure you get the one for lucid or maverick, depending on your OS version.  You then run it from terminal with command ```
tesseract infile.tif outfile
```where infile.tif is the name of the tif image, (or even tiff now in tesseract v3) and outfile is the name of the outfile.txt file it produces; do not use .**txt** for the output filename.

Older versions of tesseract that I've used needed a tif, not a tiff, and also needed a lineart scanned tif in just black and white, ie two colours only.  T v3 will work with full colour scans, though is better with lineart, will also work with more than a single column of text on the page scanned, and is wonderfully accurate if you scan at 600 dpi.  When you have a pdf to convert to tif, set resolution to 600 pixels per inch when you load the pdf in gimp, convert to greyscale, save as tif then use the command as above.

---

### Post by frank cox on 2011-03-28
> **xtremezj said:**
> I have spent the last few days doing a lot of searching for Linux solutions for using OCR in PDF's. From everything I have read it requires scripts, converting, etc and quite honestly is far too much effort with everything else I have to do when trying to get my assignments done for 6 classes.

My question is has anyone released a PDF reader in more recent times that supports OCR? I have installed and tried so much stuff. I was honestly hoping OpenOffice would support it, but don't see it there either.

How come there is such a lacking support for this?

I really see no need for it. PDF will allow you to do anything you need and it is well supported in Open  Office Draw,Xsane scanning , and several others.

---

### Post by claven123 on 2011-04-17
> **frank cox said:**
> I really see no need for it. PDF will allow you to do anything you need and it is well supported in Open  Office Draw,Xsane scanning , and several others.


Not every pdf is searchable, still need the OCR functionality.

D

---

