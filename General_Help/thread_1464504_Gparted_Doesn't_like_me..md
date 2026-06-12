---
title: "Gparted Doesn't like me."
date: 2010-04-28
forum: General Help
---

### Post by PhilMize on 2010-04-28
**Update: I think I figured out why it was not working. It's a micro SD card so I was using one of those adapters for them. I pulled the micro sd out and mounted it via my phone instead and now I can edit the micro sd without any errors or complications. So maybe it's a bad adapter?**



I'm having issues with Gparted in Ubuntu 9.10. I'm trying to resize a sd card to use 2 partitions. But I keep getting an error that's saying the sd card is read only. I've tried booting into Gparted Live and opening gparted from terminal. I tried mounting and un-mounting. I can't seem to do anything with it. Heres my error I keep getting:

```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Delete /dev/sdb1 (fat32, 3.69 GiB) from /dev/sdb  00:00:00    ( ERROR )
    	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
    	
path: /dev/sdb1
start: 63
end: 7743329
size: 7743267 (3.69 GiB)
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
    	
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Can't write to /dev/sdb, because it is opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
========================================
```

I tried searching the forums a bit, so I hope this isn't a double post. Everything I find on google doesn't help any. I checked the Gparted forums and couldn't find anything but developer stuff thats way over my head.

So any insight would be much appreciated.

---

### Post by lordbux on 2010-04-28
> **PhilMize said:**
> I'm having issues with Gparted in Ubuntu 9.10. I'm trying to resize a sd card to use 2 partitions. But I keep getting an error that's saying the sd card is read only. I've tried booting into Gparted Live and opening gparted from terminal. Heres my error I keep getting:

```
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Delete /dev/sdb1 (fat32, 3.69 GiB) from /dev/sdb  00:00:00    ( ERROR )
    	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
    	
path: /dev/sdb1
start: 63
end: 7743329
size: 7743267 (3.69 GiB)
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
    	
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Can't write to /dev/sdb, because it is opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
========================================
```

I tried searching the forums a bit, so I hope this isn't a double post. Everything I find on google doesn't help any. I checked the Gparted forums and couldn't find anything but developer stuff thats way over my head.

So any insight would be much appreciated.

In gparted , First try deleting the existing partition completely 
Right CLick>Delete 

and then try creating 2 new partitions of smaller size

---

