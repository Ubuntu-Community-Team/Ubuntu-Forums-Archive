---
title: "File odt lost after shutdown"
date: 2011-12-10
forum: General Help
---

### Post by butchertkd on 2011-12-10
Hello everybody, I've a problem.. I was converting a file.odt to pdf from the libre office tool and at that time the machine has powered off (or has hibernate) because the laptot has discharged. When I rebooted the machine the file.odt was empty! (also with du file.odt I've 0) I tryed with fsck, but nothing (even in lost+found there's anything). It seems like the OS has deleted the inodes of that files for some reason...this is the syslog [http://pastebin.com/d3bHgdyb](http://pastebin.com/d3bHgdyb) (strange things from row 700).
Any suggestion? (there's some tool that I can use to recover it? because I think that the datablocks still contain it somewhere).

P.S. I was using Ubuntu 11.10 32bit and LibreOffice 3.4.4. Another strange thing: in .libreoffice/3/user/backup/ there isn't the backup of that file

Thank you,
butcher

---

### Post by papu40000 on 2012-01-31
hi f00fyf00f3r,

is a bug:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/817326](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/817326)

I think you can't recover your document.
I'm using LibreOffice too, the thing I do is to save and move the document in two places, doc_backup1.odt doc_backup2.odt. If I have a shutdown, I have a recover

:/

---

### Post by Mark Phelps on 2012-01-31
Sorry ... your document is permanently GONE!

I got bit by this same "bug" -- even though I had the feature turned on to periodically save the document.

Solution was to save a copy in a different folder (from time to time), that way, when the original got trashed, I could resume from the last saved copy.

---

