---
title: "Automount NTFS drive at startup"
date: 2012-02-05
forum: General Help
---

### Post by kanishkdudeja on 2012-02-05
I want to automount an NTFS drive at startup.

I have added this line in fstab.

/dev/sda6  /media/Home/  ntfs-3g  defaults,exec,fmask=000  0  0

I have my Dropbox in that folder. And it says..

```
Downloading File: cannot sync, permission denied.
```

So probably it does not have the permissions to write into that directory.

So how do i accomplish that?

---

### Post by decrepit on 2012-02-05
OK, it's a while since I did this myself, but this is what I have in fstab for my ntfs drive.

UUID=4660502A605022CB	/mnt/stuff ntfs	umask=000         0 	  0


The UUID is used instead of "/dev/sda6" so that any changes do not affect which partition is mounted.
You need to get the number for your partition by using the instructions in fstab.

umask=000 give read/write permissions to user

---

### Post by linoseros on 2012-02-05
try this

/dev/sda6 /media/Home/ ntfs-3g defaults 0 0

---

### Post by kanishkdudeja on 2012-02-09
I found the solution.

Just added uid=1000 to the parameters so that i become the owner.

Then it worked.

---

### Post by Mark Phelps on 2012-02-09
Word of caution ... if the NTFS "drive" is Windows XP or is a Vista/Win7 Data-ONLY drive, then this should be OK.

But, if it's a Vista/Win7 OS partition, you're asking for trouble.  Vista and Win7 are very finicky about changes being made to their filesystems from "outside'.  Doing so can cause filesystem corruption, rendering the OS housed on that partition as unbootable.

A safer approach, in those cases, is to mount the partition read-only.

If you want to SHARE folders and files between Linux and Windows OSs, a better route is to create a shared DATA partition using the NTFS filesystem.  You won't be booting from that, so you won't be running the same risks.

---

### Post by Rafterman414 on 2012-02-09
> **Mark Phelps said:**
> Word of caution ... if the NTFS "drive" is Windows XP or is a Vista/Win7 Data-ONLY drive, then this should be OK.

But, if it's a Vista/Win7 OS partition, you're asking for trouble.  Vista and Win7 are very finicky about changes being made to their filesystems from "outside'.  Doing so can cause filesystem corruption, rendering the OS housed on that partition as unbootable.

A safer approach, in those cases, is to mount the partition read-only.

If you want to SHARE folders and files between Linux and Windows OSs, a better route is to create a shared DATA partition using the NTFS filesystem.  You won't be booting from that, so you won't be running the same risks.

I agree make a shared data partition. Once upon a time I was accessing my Windows 7 OS partition form Linux and somehow all of the permissions that windows had for the files and folders got dropped. I had to manually have Windows take ownership of everything again. From that moment on I decided to just stick to using my shared Data partition.

---

### Post by kanishkdudeja on 2012-02-11
Yes, it is a shared data partition.

---

