---
title: "Help with mounting NAS via fstab"
date: 2010-03-14
forum: General Help
---

### Post by masonnj on 2010-03-14
I have an HP Media Vault NAS that I want to mount automatically via entries in fstab.

I've created mount points in /mnt - MV-FileShare, MV-MediaShare, MV-Backup and MV-Data

I've added the required lines to get them to mount at startup into fstab and three of them work fine, one doesn't, MV-Data. 

There are two disks in my Media Vault, Volume1 and the second is Data 2 

I can mount MV-Data manually from the the terminal with the following;

mount -t nfs hpmediavault:/shares/'Data 2'/Data/ /mnt/MV-Data

I can't get it to mount via fstab though, it seems to be the space in Data 2 that's giving me the problem.

I've tried the following

hpmediavault:/shares/'Data 2'/Data/ /mnt/MV-Data nfs

gives no error but the disk doesn't mount.

hpmediavault:/shares/"Data 2"/Data/ /mnt/MV-Data nfs

gives the error; 

mount: mount point 2"/Data/ does not exist

hpmediavault:/shares/Data 2/Data/ /mnt/MV-Data nfs

gives the error;

mount: mount point 2/Data/ does not exist

Putting Data 2 in single quotes works fine from the command line but not in fstab. Can someone tell me what the correct syntax is?

Nick

---

### Post by masonnj on 2010-03-15
> **masonnj said:**
> I have an HP Media Vault NAS that I want to mount automatically via entries in fstab.

I've created mount points in /mnt - MV-FileShare, MV-MediaShare, MV-Backup and MV-Data

I've added the required lines to get them to mount at startup into fstab and three of them work fine, one doesn't, MV-Data. 

There are two disks in my Media Vault, Volume1 and the second is Data 2 

I can mount MV-Data manually from the the terminal with the following;

mount -t nfs hpmediavault:/shares/'Data 2'/Data/ /mnt/MV-Data

I can't get it to mount via fstab though, it seems to be the space in Data 2 that's giving me the problem.

I've tried the following

hpmediavault:/shares/'Data 2'/Data/ /mnt/MV-Data nfs

gives no error but the disk doesn't mount.

hpmediavault:/shares/"Data 2"/Data/ /mnt/MV-Data nfs

gives the error; 

mount: mount point 2"/Data/ does not exist

hpmediavault:/shares/Data 2/Data/ /mnt/MV-Data nfs

gives the error;

mount: mount point 2/Data/ does not exist

Putting Data 2 in single quotes works fine from the command line but not in fstab. Can someone tell me what the correct syntax is?

Nick

After getting nothing useful via Google I was prodded into reading to read the man pages for fstab by a work colleague and found the answer in there.

Spaces need to be escaped with \040 so the fstab entry looks like this;


hpmediavault:/shares/Data\0402/Data/ /mnt/MV-Data nfs

The above line works perfectly. A classic case of RTFM if ever there was one! :oops:

Nick

---

