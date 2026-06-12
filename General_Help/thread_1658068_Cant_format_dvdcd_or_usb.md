---
title: "Cant format dvd/cd or usb"
date: 2011-01-02
forum: General Help
---

### Post by craigx on 2011-01-02
I have U10.10 installaed and am please with it. However, it will not format dvds, cd or usds which is a problem. I keep getting an error saying the device is in use. Then when I unmount the device it comes back with the  error;

Error creating file system: helper exited with exit code 1: Error calling fsync(2) on /dev/sr0: Input/output error

What am I doing wrong.

Cheers

---

### Post by ajgreeny on 2011-01-02
You can not format DVDs or CDs; they are completely different from other writeable media, so you can put that problem aside.

USB drives should be formatable just like any other drive as long as it is not mounted.  Have you tried gparted?

---

### Post by craigx on 2011-01-02
Thank you. The usb will format provided I unmount it - good. The DVD is a -RW and I cant do anything with it except read it. When I try to copy a file to it it says its a read only. This is the reason why I wanted to format it.

---

### Post by ajgreeny on 2011-01-02
You can't just drag files to a DVD-RW or  CD-RW as if they are simple folders.  You have to use a burning application such as brasero.

Similarly you will probably need to use brasero to blank the DVD or CD as they will have most likely been finalised when burned last time.

---

### Post by jhthayer on 2011-09-22
You can treat a CD-RW or DVD-RW just like a floppy if you use packet writing, and this has worked in earlier versions of Kubuntu/Ubuntu, but doesn't seem to be working in 10.04.  There have been other complaints about this, but no apparent action, or none, at least that Google will admit to.

---

