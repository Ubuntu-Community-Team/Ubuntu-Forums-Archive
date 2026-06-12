---
title: "Adobe Reader"
date: 2011-07-07
forum: General Help
---

### Post by Helveticus on 2011-07-07
Hello

Should I install Adobe Reader about the packages (don't know how the name is in english)? I read that this is not the actual version and there are no updates, so it's better to install directly from adobe.  And if I have to install directly from adobe which format I have to choose, .deb, .bin, .rpm or .tar.bz2?

Is the adobe reader bad for safety in ubuntu?

---

### Post by Potters Son on 2011-07-07
If you install Adobe Reader through the package manager (Software Center/Synaptic/apt-get), you get automatic updates from within Ubuntu. If you are concerned that Reader might have security flaws (I don't know if it does or not) and don't need any advanced features that Adobe might have added recently, Ubuntu does have a built-in PDF reader already installed.

---

### Post by dino99 on 2011-07-07
you dont need Adobe reader (but its avaliable via Canonical Partner Repo into synaptic), ubuntu have pdf reader working fine:

Poppler is a PDF rendering library based on Xpdf PDF viewer.

This package contains command line utilities (based on Poppler) for getting
information of PDF documents or convert them to other formats:
 * pdffonts -- font analyzer
 * pdfimages -- image extractor
 * pdfinfo -- document information
 * pdftohtml -- PDF to HTML converter
 * pdftoppm -- PDF to PPM/PNG/JPEG image converter
 * pdftops -- PDF to PostScript (PS) converter
 * pdftotext -- text extraction

install it with synaptic: popler-utils

---

### Post by Helveticus on 2011-07-07
Thank you very much.

---

