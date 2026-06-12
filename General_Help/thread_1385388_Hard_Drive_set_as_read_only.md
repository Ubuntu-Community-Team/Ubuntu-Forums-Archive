---
title: "Hard Drive set as read only"
date: 2010-01-19
forum: General Help
---

### Post by danlab825 on 2010-01-19
I set up a server using ubuntu 9.10, with two hard drives in a hardware Raid 1 setup and with two more drives for recurring backups. The problem is that the two drives for backup are set to read only and won't allow me to change the permissions even when logged in as root. I have tried putting "rw" into the "fstab" file with no luck, I have also tried running "gksudo nautilus" and "fsck -r /dev/sdc" but still have the same message that I don't have the necessary permissions to complete the task. Any help would be greatly appreciated.

**I just tried erasing the data on the disk and creating a new partition, the disk utility allowed me to erase the data and create FAT32 partitions with the same permission problems but would not allow an EXT partition or NTFS partition (it would give and error message stating:"Error creating file system: helper exited with exit code 1: helper failed with:mke2fs 1.41.9 (22-Aug-2009)")**

***I fixed the problem by fixing a formating problem in fstab and reformatting the drives to ext4.(the fstab had a problem with the way that I broke up the lines when I input the info for the new drives, and I didn't realize it until I maximized the window in gedit.)***

---

### Post by ChrisB111 on 2010-01-19
You could try booting of a live cd, this would allow you to access your files and you could run a filesystem check from there.

Might help,

Chris

---

