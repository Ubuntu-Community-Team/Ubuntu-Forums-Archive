---
title: "Set static mount point for USB drives"
date: 2010-10-20
forum: General Help
---

### Post by muskrat775 on 2010-10-20
I am running Kubuntu 10.10 Maverick Meerkat. I have an Iron Key pen drive that I would like to auto mount in the same place every time. For those of you not familiar with the Iron Key, when you first insert it, it mounts as a cdrom drive. Once it mounts, you access the cdrom drive and run the unlocker which un-encrypts the drive and makes the data partition available. In older versions of Kubuntu I had to setup udev rules with the device manufacturer (also trying to restrict to 2 manufacturers). However, in Meerkat I can't get udevinfo command to work so I can get the device info. Any ideas for this linux noob?

---

### Post by ajgreeny on 2010-10-20
I have no idea if this will work in your situation with that disk, but normally if you give the partition on a disk a Label, using, for example, gparted for a typical windows fat32 of ntfs file system, or tune2fs in terminal for ext2, ext3 or ext4 partitions, the partition/disk will mount automatically at /media/<label>.

My uncertainty is with the encryption and how that may affect labeling of a partition, if at all; I just have no idea about that.

---

### Post by muskrat775 on 2010-11-08
I guess the title of this post may be a little misleading. The problem is that when the Ironkey is inserted, it may be found at dev/sdb and the next time may be at dev/sdc for no particular reason. Then once the unlocker is executed on the Ironkey, the encrypted partition is found sometimes at /dev/sdb or /dev/sdc or wherever it feels like putting it.
I am trying to create a script that auto runs on boot to automount the CDFS partition and run the unlocker. Give the user the chance to enter the password then automount the Fat32 partition and pass it to rdesktop on a win server.
Sorry for the confusion and thanks for the help.

---

