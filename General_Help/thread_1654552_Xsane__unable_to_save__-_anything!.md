---
title: "Xsane : unable to save  - anything!"
date: 2010-12-28
forum: General Help
---

### Post by craigx on 2010-12-28
When ever I try to save a scanned image with Xsane i get the following message:

Child process error
failed to execute OCR command: gocr
No such file or directory.

I have tried several different directories and file names with the same resut.
Any ideas what I am doing wrong.

---

### Post by ajgreeny on 2010-12-28
Xsane is apparently trying to use OCR as the default, so go to xsane Preferences and see if you can change anything there, though I admit I can not see why this would happen, unless you are trying to save as .txt files

What do you see in the filename save box of the main xsane window; the window where you set the dpi, scanner type etc etc?  Mine usually shows empty, then if I save as a picture file of some type from the viewer window all is OK.  However, if I try to save anything as a .txt file, I get the same error as you do, not having gocr installed.

If I need to do any OCR I always use tesseract which is much more accurate, but it does need the scan saved as a tif file, not tiff or it will throw an error, and then that tif to be OCRed as a separate action in terminal.

---

### Post by craigx on 2010-12-29
Thank you - I got it working now!
However, the OCR accuracy it not the best,

---

### Post by ajgreeny on 2010-12-29
> **craigx said:**
> Thank you - I got it working now!
However, the OCR accuracy it not the best,
Agreed!

I think gocr is a waste of space, or it was the last time I looked at it.  Try tesseract as I suggested, and it should be more accurate than gocr, though it is more palaver to use, I agree, but unfortunately I know no way of using it direct from xsane.

I suppose a shell script could do it, but I use it so seldom that it is not worth the hassle of writing a workable script.

Perhaps someone has already done that for you (us) if we search.

---

