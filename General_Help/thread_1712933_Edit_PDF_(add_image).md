---
title: "Edit PDF (add image)"
date: 2011-03-23
forum: General Help
---

### Post by Nonno Bassotto on 2011-03-23
I would like to edit a PDF file I have; in particular I'd like to overlay a JPG image at a certain position.

I have tried PDFEdit, but it seems it is not able to add images into a page. Any alternatives?

---

### Post by HermanAB on 2011-03-23
The Gimp can import PDFs and then you can do whatever you want, but is treated as an image per page.  Eventually, you can use imagemagick to put the images back together in a single PDF file again.

---

### Post by Nonno Bassotto on 2011-03-23
Unfortunately there is a significant loss of quality on text. But I will try it if no other solution comes. Thank you.

---

### Post by dingodog on 2011-03-27
> **Nonno Bassotto said:**
> I would like to edit a PDF file I have; in particular I'd like to overlay a JPG image at a certain position.

I have tried PDFEdit, but it seems it is not able to add images into a page. Any alternatives?
use the power of **overlay** and pdftk

**FIRST STEP:** create a pdf document (from, for instead, opneoffice doc)

place your image where you want

save your doc as pdf and name this as **stamp.pdf**

**SECOND STEP:** invoke pdftk

```
pdftk yourfile.pdf stamp stamp.pdf output stamped.pdf
```

and you will have your two pdfs flattened into one with picture onto first pdf

---

### Post by Nonno Bassotto on 2011-03-28
Thank you very much! :-)

---

