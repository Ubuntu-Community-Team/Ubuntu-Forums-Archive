---
title: "Ocr"
date: 2009-10-21
forum: General Help
---

### Post by DrWho8 on 2009-10-21
Xsane regognizes my scanner correctly. But when I use the choice for text, it seems to download as an image file. I have searched Google and can't find an answer. How do you scan and then use OCR in Linux?

Thanks,

Gnu-B

---

### Post by bwang on 2009-10-22
Tesseract: [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/)
After you install it, you have to run it in a Terminal:
```
tesseract <imagefile> <outputfile>
```
There are a bunch of other OCR programs like gocr and Kooka, but Tesseract is the most accurate.

---

