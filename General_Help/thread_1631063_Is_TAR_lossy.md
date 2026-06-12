---
title: "Is TAR lossy?"
date: 2010-11-26
forum: General Help
---

### Post by sofasurfer on 2010-11-26
If I save a pcture in JPG format, some of the info is lost. Everytime I resave it, some info is lost.
If I backup my image files in compressed form using TAR will I have image lose?
Is "saving" differant than "backing up"?

---

### Post by jim_deadlock on 2010-11-26
No, your jpg file will not be altered in any way when you tar it, you'll get back exactly the same file when you extract it.

---

### Post by Vaphell on 2010-11-26
when you work on some image, save it in the native format of the program you work with so the quality won't degrade as you save/reopen the file for further edits. When you need a lower quality result jpeg/whatever simply use that 'master copy' to produce it.

---

### Post by QLee on 2010-11-26
[QUOTE=sofasurferparse]If I save a pcture in JPG format, some of the info is lost. Everytime I resave it, some info is lost.
If I backup my image files in compressed form using TAR will I have image lose?
Is "saving" differant than "backing up"?[/QUOTE]
I imagine that by "saving" you mean saving after you have done some manipulation on the original. If you were to copy a JPG and paste (save) a copy somewhere it wouldn't degrade.

Give some consideration to Vaphell's advice. Also consider keeping "master copies" in a lossless format like TIF, and/or work with the files in TIF and only save to JPG when you have what you want as the final product. Most, if not all, graphic manipulation allow you to select compression level when you save a JPG.

Use some of those terms as "keywords" in a search engine if you need to research and learn more.

---

### Post by WorMzy on 2010-11-26
When you save an image as a JPEG, it goes through the JPEG compression algorithm, which is where it loses quality. Moving the image around on a hard drive/adding it to an archive/etc doesn't have anything to do with the JPEG compression algorithm, and so the image quality is not affected (unless some form of corruption is encountered for whatever reason)

---

### Post by James78 on 2010-11-26
> **Vaphell said:**
> when you work on some image, save it in the native format of the program you work with so the quality won't degrade as you save/reopen the file for further edits. When you need a lower quality result jpeg/whatever simply use that 'master copy' to produce it.
I prefer PSD for that. It saves the layers and everything really well, without any quality loss (really, I've never seen quality loss). That's the master copy, then when you're done, you just export or save as a real image. Has the added bonus effect of being a perfect backup master copy image where you can tweak the master copy later and then save it as a regular image again. Comparable to having the source code of a program you made, and giving the other people the binary. When you want to edit the program again, you need the master copy, the source code; doing it any other way is just painful.

---

