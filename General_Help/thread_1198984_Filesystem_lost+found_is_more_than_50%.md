---
title: "Filesystem lost+found is more than 50%"
date: 2009-06-28
forum: General Help
---

### Post by parson983 on 2009-06-28
I was looking in my root folder today and i noticed a peculiarity, in my 34GB drive, the lost and found folder takes up 33.1GB. How can this be possible as I have 17GB of other files on the disk. Is this data listed twice or what? 

The properties of the lost+found folder are
349,083 items, totalling 33.1 GB
(some contents unreadable)

Is this folder taking up considerable disk space or is it saying that 33.1Gb of my drive is dodgy? Is there any way i can resolve this as the folder is out of bounds for me!

On this note, why am I, the only user, and thus the administrator who installed ubuntu, getting this msg:

You do not have the permissions necessary to view the contents of "lost+found". 

As well as other folders, who does?

---

### Post by swisstone198 on 2009-06-28
Lost+found is used to keep corrupt files from the filesystem. If you run fsck on the filesystem it should sort it out. You will need to umount the filesystem to run fsck.

---

### Post by parson983 on 2009-06-28
How can i do this if this is the partition i'm running ubuntu from?

---

### Post by swisstone198 on 2009-06-28
you will need to boot from the liveCD, then run 

sudo fsck /dev/sda1 (or what ever partition your install in on).

---

