---
title: "read-only filesystem errors"
date: 2006-05-22
forum: General Help
---

### Post by tkang on 2006-05-22
I am running the regular Breezy Badger (not 64) build on an AMD64.  I posted there earlier but was unable to get any help and I'm not sure that the error has to do with the fact that I am running an AMD64.  

Anyways, when my laptop is running, it occassionally turns to a read-only filesystem and I can't do anything but reboot.  I usually then have to manually run an fsck and there are tons of inode and HDA errors.  Has anyone experienced anything similar and what steps can I take to remedy the situation?

Thanks.

---

### Post by nanotube on 2006-05-22
sounds like you have a bad hd. 

try installing package smartmontools:
```
sudo apt-get install smartmontools
```
and then run command
```
sudo smartctl -a /dev/hdc
```
(replace hdc with whatever device your disk resides)
and see if it shows any errors on the drive.

---

