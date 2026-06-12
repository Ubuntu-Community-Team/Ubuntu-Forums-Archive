---
title: "scan copy paste"
date: 2009-10-27
forum: General Help
---

### Post by cowboy7305 on 2009-10-27
I have a document and i have scaned it to my desktop now i want to copy the text of this doc and paste it in open office word .so i can edit  text on doc, first can it be done ,second how do i do it 
many thanks

---

### Post by coffeecat on 2009-10-27
You need OCR (optical character recognition) software to "read" the text in the image and output this as a text file which can be used in a word processor. You have 2 choices, gocr and tesseract.

If you install the packages gocr and gocr-tk, you'll find that gocr is automatically incorporated as a plug-in in the scanning app xsane. Scan your document with xsane and after the image has appeared on screen you'll be able to invoke gocr from somewhere within the menus, and then save as a text file. I can't remember where exactly and I'm on the wrong machine to check at the moment, but it's all fairly straightforward.

Unfortunately, the accuracy of gocr is fairly poor.

With  tesseract you get far superior results but it's a command-line app only. Install the packages tesseract-ocr and the packages tesseract-ocr-* for the languages you want, open a terminal and invoke it with:

```
tesseract imagefile.tif outputfile.txt
```Note that tesseract can only read a TIFF file - if you've got a JPEG or PDF or whatever, you'll have to convert it. Also, the filename extension **must** be .tif, not .tiff, otherwise tesseract errors out.

---

