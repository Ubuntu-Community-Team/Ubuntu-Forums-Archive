---
title: "Trying to recover data with slax"
date: 2009-09-18
forum: General Help
---

### Post by Jago6060 on 2009-09-18
So I may have accidentally effed things up...therefore I'm trying to recover some data with Slax.  I have a live USB all set and working, but I cant seem to find my files on the harddrive.  In fact, it doesn't show the harddrive, any ideas?

---

### Post by csi_guy on 2009-09-18
You need to mount your hard drive, you can then copy that needed data off to a separate storage media.

This command will show all of your partitions
fdisk -l

Make a new folder in the /mnt directory

ie.  /mnt/sda2

# mount /dev/sda2  /mnt/sda2

# cd /mnt/sda2


You can then copy out the data with the "cp" command


Hope this helps

---

### Post by Jago6060 on 2009-09-18
> **csi_guy said:**
> You need to mount your hard drive, you can then copy that needed data off to a separate storage media.

This command will show all of your partitions
fdisk -l

Make a new folder in the /mnt directory

ie.  /mnt/sda2

# mount /dev/sda2  /mnt/sda2

# cd /mnt/sda2


You can then copy out the data with the "cp" command


Hope this helps

Hmmm.  I did fdisk -l and it shows the HDD as /dev/sda.  I tried mount /dev/sda /mnt/sda and it said the mount point didn't exist, so I made the folder and changed the permissions.  Then it tells me no such file or folder.  any ideas?

---

### Post by rbc on 2009-09-18
How did you create the folder/directory. Additionally, you cannot mount the hard drive (sda). You should be mounting a partition on the hard drive (sda1, sda2, etc.) do you know which partition it is? And what file type is it?

---

