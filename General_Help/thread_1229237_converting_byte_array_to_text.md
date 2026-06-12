---
title: "converting byte array to text"
date: 2009-08-01
forum: General Help
---

### Post by rtrdom on 2009-08-01
After pdftotext, the result is a 1 byte array. How can I convert it back
to the scanned image so I can read it?
Thanks for any help.

---

### Post by shp on 2009-08-01
What command are you using for pdftotext? The 1byte array is obviously not the output you wanted.

---

### Post by niteshifter on 2009-08-01
Hi,

pdftotext won't work on pdf files containing scanned (image) text. Handling that type of pdf is a two step process:

Extract the image.
OCR the extracted image.

---

### Post by rtrdom on 2009-08-02
Thanks for the response. I am using
pdftotext allpages.pdf allpages.txt

Seems no matter what I do, when I try to open the allpages.txt, the page has only a
small block in the upper left corner, which I think is an array of the scanned single
page.

---

### Post by ridetheteapot on 2009-08-02
i would test another pdf. pdftotext should just spit out a plain text file with no other conversion necessary.

---

### Post by niteshifter on 2009-08-03
Hi,

What does the program pdffonts output when you feed it the PDF?

---

