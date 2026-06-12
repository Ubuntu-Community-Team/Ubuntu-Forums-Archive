---
title: "Please help me, i'm recovering lost job related data"
date: 2009-09-14
forum: General Help
---

### Post by topolinuxx on 2009-09-14
hello, please help me as soon as possible...
my external drive crashed under windows yesterday and i used microsoft's chkdsk to recover data, and now i have more than 8000 files named file0001.chk, filexxxx.chk
i'm using ubuntu to find out what kind of content have those files, and the nautilus preview is VITAL for me to do that.
But one hour ago i don't know what mess i did triyng to open one of these files with gedit (a file with unknown content) and now ALL the *.chk files seems to be unknown type, the files that i've already found and moved to their respective folders (e.g. audio files in audio folder, video files in video folder et cetera)
please help me i have some documents that need to send to my office, they expect those doc for thursday and i don't know HOW retrieve them within a folder of almost 4000 small sized files *.chk please help me please please

---

### Post by P4man on 2009-09-14
This might help:

[http://www.raymond.cc/blog/archives/2008/01/07/how-to-recover-chk-files-created-by-chkdsk-and-scandisk/](http://www.raymond.cc/blog/archives/2008/01/07/how-to-recover-chk-files-created-by-chkdsk-and-scandisk/)

However, before doing anything else, i would advice you to clone the disk. Use clonezilla or dd or anything, but make a bit for bit exact copy to an external drive, so you can experiment with the copy (or original) without risking even more data loss.

---

### Post by topolinuxx on 2009-09-14
thank you a lot. i've already did it, and the soft found many pdf files, many avi and many wave files, everything but documents. my last solution is working with linux...

---

### Post by P4man on 2009-09-14
Also, if its images you are look for, this will be a life saver:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) 

you can install it on a live cd (sudo apt-get install testdisk).
But I still advice you to make a backup first.

edit: scratch that, as you already recovered the images

---

### Post by topolinuxx on 2009-09-14
no, images and other media files are not important. i need to find all the documents. they are in .pwi and .docx format

---

### Post by topolinuxx on 2009-09-14
OKAY. thanks a lot for your support.
I found out the way to restore the nautilus file preview: i deleted the folder /home/.local/.share and now the preview is working again.
Found a possible answer to my problem here:
[http://forum.ubuntu-it.org/index.php?topic=208580.msg1445886](http://forum.ubuntu-it.org/index.php?topic=208580.msg1445886)

THANK YOU ^__^

---

### Post by P4man on 2009-09-14
You only got yourself to thank :) But good luck. and make a backup next time.. seriously :)

---

