---
title: "Trouble mounting fat32 usb drive"
date: 2011-03-02
forum: General Help
---

### Post by Rodayo on 2011-03-02
I used this command which normally does the job:

mount /dev/sdb1 ~/usb_mnt

That told me to indicate a filesystem type. I used fdisk and Disk-Utility to check the fs type which is W95 FAT32. 

So I tried the following commands:

mount -t vfat /dev/sdb1 ~/usb_mnt
mount -t msdos /dev/sdb1 ~/usb_mnt

Both of them give me a message that said 
"wrong fs type, bad option, bad superblock on /dev/sdb1"

Formatting is not an option, I want to retrieve a file on the drive...

What do?

If it helps this is the tail end of dmesg:
> [13696.476414] FAT: bogus number of reserved sectors
[13696.476418] VFS: Can't find a valid FAT filesystem on dev sdb1.
[13706.966399] FAT: bogus number of reserved sectors
[13706.966404] VFS: Can't find a valid FAT filesystem on dev sdb1.
[13823.878987] FAT: bogus number of reserved sectors
[13823.878991] VFS: Can't find a valid FAT filesystem on dev sdb1.

---

### Post by seawolf167 on 2011-03-03
See if [this link ]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/")helps you out. If it still doesn't work, you'll probably have to use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")to try and restore your partitions in order to pull data off of it.

---

