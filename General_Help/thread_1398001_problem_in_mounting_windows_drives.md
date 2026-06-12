---
title: "problem in mounting windows drives"
date: 2010-02-03
forum: General Help
---

### Post by bitsuser on 2010-02-03
hi all,
the problem im having is that everytime i reboot, windows drives are mounted with different filenames (eg:first time d: was /media/disk and e: was /media/disk-1 but after reboot they got interchanged - e: was mounted in /media/disk). I cannot afford this as several apps use files from these drives and their path keeps changing after every fresh boot. 
Kindly help.
Thanks

---

### Post by hemimaniac on 2010-02-04
Are there permanent directories and edits in your /etc/fstab file for them

that is lets say for example you mkdir /media/Windows1 

then in fstab add the line    /dev/sdx/                      /media/Windows1                   ntfs             defaults        0   0   (sdx x being your ntfs partition a-b-c-d-etc.)

then restart the box

or for a gui way to do it

sudo aptitude install pysdm 

then Menu > Administration > Storage Manager

and you can set the directories there and apply them, then when the box is rebooted they will auto mount

---

