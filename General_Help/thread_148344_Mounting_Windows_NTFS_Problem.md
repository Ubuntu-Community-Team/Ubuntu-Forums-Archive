---
title: "Mounting Windows NTFS Problem"
date: 2006-03-21
forum: General Help
---

### Post by iOsiris on 2006-03-21
My Windows XP died (comes up with a DriveLock HDD Password, in which it just set itself up as I don't have it), but I wanted to try and recover my essay from it so I downloaded Ubuntu LIVE.  I go into the console and followed some guides like this one [Guide](http://www.obharath.net/blog/2005/10/05/reading-files-from-windows-partitionntfs-on-ubuntu-linux/)
In which I try to create a directory and mount the windows partitions.  However whenever I try to do it, I get this error that says "wrong fs type, bad option, bad superblock on /dev/hda"  Any suggestions?  Or is my HDD just !@#%ed ?

EDIT:
Using dmesg | tail it gives me the following
[quote]
NTFS- fs error (device hda): read_ntfs_boot_sector(): Mount option errors=recover not used.  Aborting without trying to recover.
NTFS-fs error (device hda): ntfs_fill_super(): Not an NTFS volume
hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
hda: task_no_data_intr: error=0x04 { DriveStatusError }
ide: failed opcode was: 0xea
hda: wcache flush failed!
hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
hda: task_no_data_intr: error=0x04 { DriveStatusError }
ide: failed opcode was: 0xea
hda: wcache flush failed!

EDIT: Yes, I assure you it is NTFS and not vFAT/FAT/FAT32, etc

---

### Post by chuckyp on 2006-03-21
Are you specifying the type i.e. 
```

sudo mount -t ntfs /dev/hda#  /placeto/mount 

```
change # with the partition of your xp install

---

### Post by iOsiris on 2006-03-21
Can you explain how you find that?
I use fdisk -l and it only shows a 122MB "Disk /dev/sda/ (my usb key).

---

### Post by NewWithoutClue on 2006-03-21
It's probably /dev/hda1 depending on your partiton set up.

p01n7

---

