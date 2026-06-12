---
title: "Anyone have an Ocropus tutorial?"
date: 2010-09-07
forum: General Help
---

### Post by wesg on 2010-09-07
I want to use OCR software to convert a long list of .tif files into text so I can process it further, but I can't seem to find any information about how to do it. I've installed ocropus and tesseract already.

Does anyone know how to use ocropus for document analysis and interpretation?

---

### Post by tkoco on 2010-12-12
> **wesg said:**
> I want to use OCR software to convert a long list of .tif files into text so I can process it further, but I can't seem to find any information about how to do it. I've installed ocropus and tesseract already.

Does anyone know how to use ocropus for document analysis and interpretation?

Here is the skinny on the ocropus and such:

ocropus is not an application. It is an OCR engine for a framework.
gnomescan is not an application. It is a framework/library which uses ocropus.
gegl is not an application. it is a framework addon.

So, the big question here is **where's the beef?**

Answer: gnome applications like GIMP, inkscape, abiword, etc.

---

