---
title: "Cannot print PDF files"
date: 2011-06-05
forum: General Help
---

### Post by bdog676 on 2011-06-05
I cannot print pdf files. I have tried using okular and xpdf. The documents display in the program, but print preview shows a blank page. The printer then sends out blank pages. I have tried printing on 2 different printers using usb cables. 
Using terminal to process the commands shows error:
> xxx@xxx:~$ xpdf
***** MediaBox = ll:0,0 ur:611.976,791.968
***** CropBox = ll:0,0 ur:611.976,791.968
***** Rotate = 0
Segmentation fault

Converting to .ps also is blank.
I am using natty.

---

### Post by bdog676 on 2011-06-05
also forgot to mention printing works in firefox and openoffice.

---

### Post by Chronon on 2011-06-05
Can you report what versions of software you are using?  I just printed a PDF with no problems in Kubuntu 11.04 using Okular 0.12.2.

---

### Post by bdog676 on 2011-06-14
> **Chronon said:**
> Can you report what versions of software you are using?  I just printed a PDF with no problems in Kubuntu 11.04 using Okular 0.12.2.
2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux
11.04
okular .0.12.2

---

### Post by bdog676 on 2011-06-17
Really need help here please. I don't want to have to use a vb.

---

### Post by Chronon on 2011-06-17
Sorry but I'm just not sure of what factors are causing problems for you.  Does the behavior vary from PDF to PDF or does printing always cause a segmentation fault?

I still don't know what's causing this but here's another similar topic (though people there are saying that okular performs better than Adobe reader):
[http://ubuntuforums.org/showthread.php?t=1770580](http://ubuntuforums.org/showthread.php?t=1770580)

---

### Post by bdog676 on 2011-06-23
Reporting back that issue is resolved now. I reinstalled CUPS and okular. I'm sure the upgrade messed something up in those packages. Should have tried that first. :guitar:

---

