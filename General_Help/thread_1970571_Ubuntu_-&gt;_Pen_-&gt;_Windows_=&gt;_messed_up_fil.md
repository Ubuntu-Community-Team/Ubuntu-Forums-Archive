---
title: "Ubuntu -&gt; Pen -&gt; Windows =&gt; messed up filenames and missing files"
date: 2012-05-01
forum: General Help
---

### Post by th1 on 2012-05-01
I moved a few mp3, txt and pdf files to a pen. The pen is 256mb and was filled with 240mb of files. When I connected it to a laptop running XP, it was not recognized, I rebooted, and than XP recognized the pen, however **the pdf and txt files were missing** and **the mp3 files were all duplicated 3 or 4 times if I'm not mistaken**, some with the MSDOS abreviated name (I used the '&#8213;' sign in the filenames..' and others with the proper names. There were also 3 new empty files with only "&#9794;" as the filename, no extension..

I got home and connected the pen back on ubuntu, only the mp3 files remain, no duplicates, correct filenames.

Ubuntu says the pen is 240mb full, but only shows 130mb of files in nautilus (the pdf and txt are not shown)

LS returns 2 mp3 files repeated 9 times with the same name and the others repeated once, no sign of the pdf or txt. NO mp3 files are missing only duplicated

There mas also a DOC file which is missing..

---

### Post by th1 on 2012-05-02
bump

---

### Post by pawhtiobo on 2012-05-02
Hi,

Did the XP do a scan of the USB file-system? That could be one of the reasons of the problem....another one could be a malfunction of the USB Pendrive (bad clusters), or a trojan/malware....it could be a lot of things......
I can advice you to download a recover software and do a deep scan of the USB device, you can try Recuva (MS Windows):

[http://www.piriform.com/recuva](http://www.piriform.com/recuva)

Probably some of the files can be recovered, it will also show a lot of incomplete and old deleted files, just for safeguard, do a backup of the existing files and do not had more files to the USB device, you could risk overwriting a file that could be recovered. If you succeed to recover your files, after that do a full format of the device (FAT32).

See ya......

---

