---
title: "Mouth NTFS hdd"
date: 2006-06-14
forum: General Help
---

### Post by Ve33iE on 2006-06-14
Hey guys i seen some where on this forum that there is a package where you download and use in the terminal and it auto mounts your other hdd's thats in your system

can some one show me the link for it pls
:)

---

### Post by WhimpyPeon on 2006-06-14
If you are just trying to mount an NTFS drive or partition you can just add an entry to your /etc/fstab to mount it automatically.  NTFS is only REALLY safe as read only.  There is some work on making it R/W but I wouldn't want to risk it myself.

Otherwise:
mount -t ntfs /dev/(NTDEVICE) /mnt/(MOUNTPOINT)

---

