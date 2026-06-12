---
title: "Scan to ODT, DOC, etc"
date: 2011-04-15
forum: General Help
---

### Post by duranl on 2011-04-15
Can anyone suggest an application that will allow me to scan to an odt, doc, or any other workable format?

I have a long tangible document that I would like to edit without typing the whole thing up.

Any advice would be appreciated. ):P


Also, I apologize if this is in the wrong forum.  I'm still relatively new to Ubuntu.

---

### Post by Cheesehead on 2011-04-15
No. 

You must perform Optical Character Recognition (OCR) on the scan, then import that text into your .odf file. Depending on the quality and font of your original, OCR quality can vary. You will also lose most special formatting (indents, columns, etc)

One example of how to do it:
1) Scan each page into a tiff file.
2) Use the 'tesseract-ocr' package to perform OCR on each tiff, outputting a text file for each page.
3) Import (or copy-and-paste) the text into your .odt file.

Much of this can be automated with a simple bash script or two...but it may not be worthwhile to automate much since you must still review and correct each page carefully - since OCR can make a lot of mistakes.

If you really must move from paper-to-electrons, plan on plenty of time for proofreading and corrections and reformatting. It's faster than retyping whole pages, but still slow and tedious.

---

