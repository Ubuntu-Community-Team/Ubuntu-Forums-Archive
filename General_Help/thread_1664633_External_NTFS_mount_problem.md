---
title: "External NTFS mount problem"
date: 2011-01-11
forum: General Help
---

### Post by Departed on 2011-01-11
Error mounting: mount exited with exit code 12: Failed to read last sector (2930275119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


This is the error i got when tried to mount external WD 1.5tb HDD 
unfortunately tried bunch of options and did not helped , anyone can help, idea maybe ?:(

---

### Post by vanadium on 2011-01-11
A common problem with ntfs partitions is that the volume is "dirty", i.e. it was not properly closed (removed without properly unmounting in MS Windows, having MS Windows in hibernation, then removing the drive ...). That is easily corrected by checking the drive under Windows and then removing it properly.

Your error messages look more serious, and hint to the system not recognizing an ntfs partition on the volume you try to mount.

Which leads to the questions
* How are you trying to mount?
* Are you addressing the correct volume?

With the drive inserted, issue a "sudo blkid" command and post it here. This will tell what drives the system sees, and what their format is.

---

### Post by Departed on 2011-01-11
> **vanadium said:**
> A common problem with ntfs partitions is that the volume is "dirty", i.e. it was not properly closed (removed without properly unmounting in MS Windows, having MS Windows in hibernation, then removing the drive ...). That is easily corrected by checking the drive under Windows and then removing it properly.

Your error messages look more serious, and hint to the system not recognizing an ntfs partition on the volume you try to mount.

Which leads to the questions
* How are you trying to mount?
* Are you addressing the correct volume?

With the drive inserted, issue a "sudo blkid" command and post it here. This will tell what drives the system sees, and what their format is.
I try to mount it regulary and both with ntfs but soimhow does not work 

here is the response on blkid:

/dev/sda1: UUID="92e04569-f449-4b90-8b3c-13deef90f61f" TYPE="ext4" 
/dev/sda5: UUID="6c4ba780-cc81-42d8-870e-f873fd6b5c6c" TYPE="swap" 
/dev/sdb1: LABEL="Elements" UUID="7EBC39C1BC39752D" TYPE="ntfs"

---

### Post by vanadium on 2011-01-11
sdb1 indeed is reported as an ntfs volume. Check whether you got the command right (you did not post it), i.e. you used /dev/sdb1 and not perhaps /dev/sdb.

If indeed the error persists, then I am not sure. The error messages suggest severe damage to disk and/or file structures. I would certainly try to inspect and check this ntfs partition using MS Windows.

---

### Post by Departed on 2011-01-11
> **vanadium said:**
> sdb1 indeed is reported as an ntfs volume. Check whether you got the command right (you did not post it), i.e. you used /dev/sdb1 and not perhaps /dev/sdb.

If indeed the error persists, then I am not sure. The error messages suggest severe damage to disk and/or file structures. I would certainly try to inspect and check this ntfs partition using MS Windows.
sudo mount -t ntfs-3g /dev/sdb1  /media/Element

also all other ways of mounting and i still get the same response

disk is working perfect under all Windows

---

### Post by coffeecat on 2011-01-11
> **Departed said:**
> disk is working perfect under all Windows

Even so, it would be a good idea to run a chkdsk from Windows.

---

### Post by Mark Phelps on 2011-01-11
Try running a CHKDSK on it under MS Windows.  Even if that does not find any errors, it will reset it so that when you get back to Ubuntu, the "dirty bit" should not be set anymore.

---

### Post by Departed on 2011-01-11
> **Mark Phelps said:**
> Try running a CHKDSK on it under MS Windows.  Even if that does not find any errors, it will reset it so that when you get back to Ubuntu, the "dirty bit" should not be set anymore.
already tried that :( does not help

---

### Post by vanadium on 2011-01-11
Can you post the partition table of the drive, 

```

sudo fdisk -l

```

---

### Post by vanadium on 2011-01-11
Can you post the partition table of the drive, 

```

sudo fdisk -l

```

---

### Post by Departed on 2011-01-11
lost my nerves, got back to Windows 7 , will install inside of it :(

---

