---
title: "mount ntfs drives @ startup"
date: 2010-06-06
forum: General Help
---

### Post by chrismitt2002 on 2010-06-06
i would like to have all my ntfs drives mount @ start up here is the command im currently useing sudo mount -t ntfs-3g /dev/sdc1 /media/D -o force
i have made the folders D E F etc now i know that the command for starting restarting and stoping samba changed in 10.04 so did something change with mounting ntfs drives ? what am i doing wrong? plez help

---

### Post by oldfred on 2010-06-07
If you want to mount all the time just add to fstab. 

You really should not use the force as if it does not mount it says it needs chkdsk and that may recover data from its journal. Force gets you in but then you will may destroy the capability of recovering the damage. 

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)


this is my entry in fstab for the shared folder I had created.
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0

---

