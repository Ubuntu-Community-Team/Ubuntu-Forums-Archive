---
title: "USB read-only auto-mount"
date: 2011-01-08
forum: General Help
---

### Post by kdb8dm on 2011-01-08
I recently formatted my memory stick in windows. It works properly in windows. I have a dual boot with ubuntu 10.04 and the usb automounts in read-only mode. I cannot write anything to the usb stick in ubuntu. sudo chomod does not work. 

Any suggestions ?

---

### Post by dcstar on 2011-01-08
> **kdb8dm said:**
> I recently formatted my memory stick in windows. It works properly in windows. I have a dual boot with ubuntu 10.04 and the usb automounts in read-only mode. I cannot write anything to the usb stick in ubuntu. sudo chomod does not work. 

Any suggestions ?

Use **gparted** or the Disk Utility to do a Check of the partition.

---

### Post by kdb8dm on 2011-01-08
Thanks David. gparted worked fine. I was unaware of this utility. I managed to format the usb stick to ntfs. It seems to be working fine for the moment. 

There is one small problem though. It is a 8GB stick but the available space is 7.4 GB. How come 600 MB are missing ? gparted tells me that the unallocated space is 3.11 MB and the size of the memory stick is 7.4 GB. What happened to the rest of the space ? 

Also, what should be the default flags ?

---

### Post by dcstar on 2011-01-09
> **kdb8dm said:**
> 
.........
There is one small problem though. It is a **8GB **stick but the available space is 7.4 GB. How come 600 MB are missing ? gparted tells me that the unallocated space is 3.11 MB and the size of the memory stick is **7.4 GiB**. What happened to the rest of the space ? 

Also, what should be the default flags ?

[LIST=1]
[*]GiB <> GB
[*]Filesystems take some space for themselves.
[*]Flags are irrelevant for non-boot drives.
[/LIST]

---

### Post by kdb8dm on 2011-01-09
Thanks, that explains it.

---

