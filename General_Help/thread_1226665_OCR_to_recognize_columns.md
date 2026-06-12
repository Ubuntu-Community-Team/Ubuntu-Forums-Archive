---
title: "OCR to recognize columns"
date: 2009-07-29
forum: General Help
---

### Post by rtrdom on 2009-07-29
[Solved] (more or less) Tesseract is very good as an OCR tool. It does not keep columns separate
and I need to keep columns separate after conversion from PDF to txt.
Does anyone have a suggestion, other than commercial?

Thanks for a response.

---

### Post by JKyleOKC on 2009-07-29
> **rtrdom said:**
> Does anyone have a suggestion, other than commercial?
My solution to the problem was to use the Gimp to copy each column to a new file, then after doing the OCR on the separate files, paste them back together using mousepad to copy and paste them. It's tedious but it works, and Tesseract is by far the best OCR program I've come across in nearly 20 years of searching for them...

---

### Post by JKyleOKC on 2009-07-30
Here's an update that I just tested on Jaunty: There's a program installed (at least as part of the Xubuntu distro) called pdftotext that will convert the entire PDF file to a TXT file, respecting the reading order and columns. Thus there's not any need to OCR it at all. Hope this helps you and others as well.

The program is part of the poppler-utils package that can be installed via Synaptic if you don't already have it...

---

