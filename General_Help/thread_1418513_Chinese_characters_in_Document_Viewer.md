---
title: "Chinese characters in Document Viewer?"
date: 2010-02-28
forum: General Help
---

### Post by Tom Collier on 2010-02-28
Is there a way to get Document Viewer to display Chinese characters in a pdf? Adobe Viewer does but I would prefer to avoid proprietary software. I cannot get either Document Viewer or Okular to properly show Chinese characters in pdf documents downloaded from my college class homepage.

I have all the Chinese language support files, bells and whistles (both traditional and simplified) loaded and operational. When I create a Chinese document in OO Writer and save it as a pdf, both DocViewer and Okular display the the Chinese characters properly. I just cannot get either DocViewer or Okular to display Chinese in pdfs that are downloaded from the website of my course's online textbook/workbook.

Running 9.10 full boat version on an EEE 1000HD netbook.

---

### Post by Tom Collier on 2010-02-28
Installed xpdf with Chinese support.  That did the trick.

---

### Post by contents on 2010-05-05
There are some other methods for viewing Chinese pdfs here:
[http://forum.ubuntu.org.cn/viewtopic.php?f=50&t=131480]("http://forum.ubuntu.org.cn/viewtopic.php?f=50&t=131480")

I found that installing poppler-data (I installed it from the repo instead of from source as they advise) and renaming 
> /etc/fonts/conf.d/49-sansserif.conf

to 
> /etc/fonts/conf.d/49-sansserif.conf.backup

worked for me (I had to log out and in again first). Now I can use evince or okular to read Chinese pdfs instead of xpdf.

---

