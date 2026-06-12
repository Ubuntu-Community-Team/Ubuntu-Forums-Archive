---
title: "Hacking tesseract OCR"
date: 2009-09-22
forum: General Help
---

### Post by james.wilde on 2009-09-22
I've done some research on the net about combining xsane scanning software with tesseract ocr software.  Now tesseract requires uncompressed tiff files as its input, and they must have a .tif (ie NOT .tiff) ending.

Now when xsane saves a file in tiff format, it saves it with the .tiff ending.  Is there some generous soul out there who can help point me to where I can hack xsane so that it either offers .tif as an alternative, or uses .tif by default.

The advantage of tesseract over eg gocr or ocrad is that it is reportedly better and it comes with several languages, so can presumably easily be trained in other languages (it's not yet available in Swedish, for example)

TIA

//James

---

### Post by ajgreeny on 2009-09-22
I would love this also.  All my attempts using gocr have been pretty useless, with so many mistakes it would almost be quicker to type the document again, but a manual scan and save as a tif will give an almost perfect output from tesseract.

I have tried using tesseract direct from xsane by altering the setting in xsane's preferences but that does not seem to work at all, presumably because the output from xsane is not actually a tif until saved as one.  If you do manage to get this to work, please show what you did here, as this is one of the few areas where windows still wins hands down over any linux I've tried.  It would be great to beat windows at this as well as most other things.

---

