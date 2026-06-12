---
title: "Can i backup my file system by copying it."
date: 2010-07-03
forum: General Help
---

### Post by v1ad on 2010-07-03
basically want i want to do is copy my whole file system to a different hard drive, then reconfigure my partitions and copy it back. then reconfigure grub.

the reason i want to do this is when on dual boot i gave it only 70gb of space and now i want to add 300 more. and since the 300gb of space is a primary partition and this is a secondary i cant extend them or combine them. if there is an easier way please let me know.

so what i want to do is. sudo cp -rP / /home/me/sshfs-folder

also i have raid 0

---

### Post by freundfire on 2010-07-03
I am not really sure about this, so I would wait for  further replies..

---

### Post by lsutiger on 2010-07-03
Use [clonezilla]("http://clonezilla.org/") in order to clone the partition, then use [gparted]("http://gparted.sourceforge.net/") to resize the partition.

#1 - Make sure you have a backup before you start
#2 - Read the instructions for both thoroughly

Enjoy learning!

---

### Post by v1ad on 2010-07-03
k i will use the clonezilla option. i have done that before with windows. and probably is the best way to go.  but it is still an interesting question, if by moving the files and permissions would it still work.

---

### Post by ezsit on 2010-07-03
I believe that if you tar.gzip the entire filesystem, that would retain the permissions so that when you untar.gzip it should restore all the permissions. I would read the man pages on tar and gzip before attempting this process since saving permissions might require you to use certain switches not necessarily included in the defaults. You would have to do the tarring while booted from a liveCD and have access to a large enough partition to hold the tarred filesystem.

---

### Post by renkinjutsu on 2010-07-03
Also, keep in mind that if you reconfigure your partitions, your UUID's will be different and you'll have to reflect the changes in your /etc/fstab otherwise your computer will not mount your disks at boot.. not even your root filesystem

---

### Post by v1ad on 2010-07-03
k thanks for the info. and also cloneZilla has no raid support. looking into other options.
also my full file system is 1TB and i have multiple partitions so i do have the room to copy it to a local partition.

copying it over sshfs though. just in case.

---

