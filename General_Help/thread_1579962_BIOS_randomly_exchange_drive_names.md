---
title: "BIOS randomly exchange drive names"
date: 2010-09-22
forum: General Help
---

### Post by ntenev on 2010-09-22
Hi all,

my system have two SATA disks and sometimes BIOS change their names and /dev/sda become /dev/sdb and vice versa. Is there some kernel / grub parameter to fix and stick drive names ?

Thanks !

---

### Post by CharlesA on 2010-09-22
If you are using fstab, use the UUID to mount them.

Grub should use UUID by default

---

### Post by ntenev on 2010-09-22
@CharlesA
Unfortunately this can't completely solve my problem, because some of partitions does not support UUID (fat32 etc.).

---

### Post by blur xc on 2010-09-22
> **ntenev said:**
> @CharlesA
Unfortunately this can't completely solve my problem, because some of partitions does not support UUID (fat32 etc.).


Doesn't fat32 support dive labels?  Might be the next best thing to uuid.

There is one caveat though- I've got a compact flash card for my dslr, and if I format it in camera it changes the label to a bunch of gibberish characters...  don't exactly know what to do about that, except not format it in camera and just delete the pictures after they have been transferred to the pc.

BM

---

### Post by CharlesA on 2010-09-22
You can try to mount it by label as blur xc suggestions.

---

### Post by ntenev on 2010-09-22
And this still can't handle more complex cases ... let's say:

(/dev/sda1 & /dev/sdc1 ) -/dev/md1 (software raid 1)
(/dev/sdb1 & /dev/sdc2 ) -/dev/md2 (software raid 1)

software raid uses disk names (no UUID nor labels) and if disk names changes it will be mess.

lvm's pvcreate also work with device names and I'm not sure that is good idea to change drive name later. 

So ... I think that there is kernel options to say to which drive what name to be assigned no matter on what channel / IDE bus is attached ... but can't find it with google.

---

### Post by bab1 on 2010-09-22
> **ntenev said:**
> And this still can't handle more complex cases ... let's say:

(/dev/sda1 & /dev/sdc1 ) -/dev/md1 (software raid 1)
(/dev/sdb1 & /dev/sdc2 ) -/dev/md2 (software raid 1)

software raid uses disk names (no UUID nor labels) and if disk names changes it will be mess.

lvm's pvcreate also work with device names and I'm not sure that is good idea to change drive name later. 

So ... I think that there is kernel options to say to which drive what name to be assigned no matter on what channel / IDE bus is attached ... but can't find it with google.

The kernel does not.  You will never find it with google.  Linux enumerates and names the devices in the order it discovers them.  

Run the command ```
sudo blkid
```
This will show you the UUID for the RAID array.  You can use that in fstab to mount the array.

---

