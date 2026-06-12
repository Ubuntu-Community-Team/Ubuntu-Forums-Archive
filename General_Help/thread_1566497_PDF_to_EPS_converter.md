---
title: "PDF to EPS converter"
date: 2010-09-02
forum: General Help
---

### Post by frs89 on 2010-09-02
I need EPS figures to include in a latex project but most of them are in PDF. It's a good idea to convert PDF to EPS or it's very lossy?
Which application would you recommend to accomplish that?
Thanks.

---

### Post by 2New on 2010-09-02
You can do this (and much more) with ImageMagick ([http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)).  Converting from PDF to PostScript should be lossless, and PostScript files are vector rather than bitmap, which means graphics can be scaled without pixelation.

---

### Post by frs89 on 2010-09-02
> **2New said:**
> You can do this (and much more) with ImageMagick ([http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)).  Converting from PDF to PostScript should be lossless, and PostScript files are vector rather than bitmap, which means graphics can be scaled without pixelation.

I'll try it. Thanks!

---

### Post by Autodidact on 2010-09-02
ImageMagick actually uses Ghostscript to do this.
Using Ghostscript directly gives you much more options and flexibility.

---

