---
title: "burn dvd"
date: 2006-02-23
forum: General Help
---

### Post by trecciolino on 2006-02-23
I've tried to use gnomeBaker to burn DVD but when the writing is complete the disk is empty...or better in not empty but all my computer can't read into and says that is an empty disk.
I've tried K3b but is the same. I write cd without problem.

I've changed the the permission in this file
sudo chmod +s /usr/bin/growisofs

sudo chmod +s /usr/bin/dvd+rw*

sudo chmod +s /usr/bin/dvd-ram*

and I've the dvd-tool....

what I can do???
 thanks:confused: :-D

---

### Post by procras on 2006-02-23
Try the disc in another computer or drive and see if it can read it.

I had problems with my dvd writer only recognising certain discs.

A written disk would appear as a blank disk. Some mix up in the automatic recognition of discs probably.

Maybe try to turn off automatic things in gnome-volume-manager and then
use the old fashioned 
mount -t iso9660 /mnt/mydisk /dev/hdc
Or something

---

### Post by trecciolino on 2006-02-23
I've tried in other dvdreader but in linux it seem empty in window get an error message! I have tried to use mount...but nothing to do

---

