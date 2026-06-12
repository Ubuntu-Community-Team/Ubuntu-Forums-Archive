---
title: "Problems with PDF shuffler (cannot crop PDFs)"
date: 2011-11-16
forum: General Help
---

### Post by chrisv on 2011-11-16
I installed PDF shuffler using Synaptic because i wanted to crop a PDF file. Everything seems to work fine, I crop the file, I export it, etc. But when I open the exported file it is simply blank. I.e., it is a pdf of a blank page. And yes the original page i wanted cropped has text in its non-cropped portions. 

I looked at the bugtracker for pdfshuffler in the debian forums but there was no mention of an error like this. 

I ran it in a shell and the shell did not mention any errors. It said something when i wanted to save to a new file (it said that the file could not be found), but I assume that is standard.

Has anyone had issues with this? If not can you recommend another software for cropping PDFs?

PS I recently switched from the main Gnome Ubuntu to Xubuntu, may this be the problem?

---

### Post by LewisTM on 2011-11-17
Try [Briss]("http://briss.sourceforge.net/")
It's a java application and has a nice graphical interface for cropping PDFs. Works flawlessly for me.

Just create an executable script called /usr/bin/briss
```
#/bin/bash
cd /where-you-put-the-briss-files
java -jar briss.jar $1

```

---

### Post by oliverjames on 2012-08-30
Yes I've just run into the same problem, with pdf-shuffler in xubuntu 12.04. Yes I can install Briss but it would be more satisfying to get this App working.

Has anyone found a fix for this?

Oliverjames

---

