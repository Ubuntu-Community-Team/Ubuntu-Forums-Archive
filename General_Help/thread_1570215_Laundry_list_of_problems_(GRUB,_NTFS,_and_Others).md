---
title: "Laundry list of problems (GRUB, NTFS, and Others)"
date: 2010-09-07
forum: General Help
---

### Post by Uruz on 2010-09-07
Long story as short as I can make it:

I had Ubuntu installed on my 500GB harddrive. I installed Windows XP (all of this was a long time ago, but still affects here and now) rebuilt GRUB, got the dualboot working fine. My Windows partition (hereafter referred to as XP1) died (as Windows partitions often do) to viruses. I cleaned the drive of viruses, but it would no longer boot.

SO, after a very long time I messed around and got a second XP partition running (XP2) which I have been using for games and such. I decided to turn XP1 into a storage partition and so I began deleting things things from it. My goal was to make it purely a storage partition, but something went wrong. XP2 was using files from XP1, and GRUB was pointing at XP1 for initial boot files and then switching to XP2 when I selected which partition to use.

When I found this out, I edited grub to point at what I KNOW to be XP2's location, (hd0,4) (GRUB even gives it as an auto-complete option) But when I try to load that, GRUB spits out "12 : Invalid device requested" which I've learned to be a general error with multiple causes. I can find no problem.

ADDITIONALLY, I can no longer edit (or execute) files on XP1 from my Ubuntu partition. I did not have problems with this in the past, but now it says only root has permissions for the filesystem and chmod and chown have done nothing to fix this. 

I'm running Ubuntu 10.04
Anyone have any ideas?

Thanks,
Uruz

---

### Post by bodhi.zazen on 2010-09-07
IMO, wipe the hard drive , re-partition, make a partition for windows and a data partition to be shared with Ubuntu, both NTFS

Install Windows.

Install Ubuntu.

Restore your data from a known good backup. If you do not have a known good backup, start making backups.

Otherwise hard to know what the problem is from your post. You say it is a virus problem, but it could be your hard drive is failing or who knows what.

---

### Post by Uruz on 2010-09-07
> **bodhi.zazen said:**
> IMO, wipe the hard drive , re-partition, make a partition for windows and a data partition to be shared with Ubuntu, both NTFS

Install Windows.

Install Ubuntu.

Restore your data from a known good backup. If you do not have a known good backup, start making backups.

Otherwise hard to know what the problem is from your post. You say it is a virus problem, but it could be your hard drive is failing or who knows what.

The drive is fine. Last time I ran XP1 I was bombarded with virus-generated popups before it froze and I shut down. Afterwards it stopped working. All diagnostics show that the drive is in good condition. Either way the problem is with GRUB giving me an error when trying to boot my working XP2 partition.
Thanks for the advice, though.

I don't have the resources to back things up either.

---

### Post by ezsit on 2010-09-07
Your problem is this:
> XP2 was using files from XP1, and GRUB was pointing at XP1 for initial boot files and then switching to XP2 when I selected which partition to use.


The only way to solve this is to delete the partition that XP1 uses and leave it as empty space. Then reinstall Windows XP to the XP2 partition. When you install Windows XP, it places boot files on the first visible partition and chain loads the rest of the operating system from what is called the system partition. Normally, this is one and the same partition, but you had a previous installation, so the the boot loader stays on the first visible (either FAT or NTFS) partition.

You may be able to use the boot.ini file from the XP1 partition and copy it to the XP2 partition (the boot.ini file will probably need some editing to correctly identify the partitions), then set the XP2 partition as active and reinstall a DOS MBR. Then afterwards, reinstall GRUB2. This might work???

---

### Post by Uruz on 2010-09-07
> **ezsit said:**
> Your problem is this:


The only way to solve this is to delete the partition that XP1 uses and leave it as empty space. Then reinstall Windows XP to the XP2 partition. When you install Windows XP, it places boot files on the first visible partition and chain loads the rest of the operating system from what is called the system partition. Normally, this is one and the same partition, but you had a previous installation, so the the boot loader stays on the first visible (either FAT or NTFS) partition.

You may be able to use the boot.ini file from the XP1 partition and copy it to the XP2 partition (the boot.ini file will probably need some editing to correctly identify the partitions), then set the XP2 partition as active and reinstall a DOS MBR. Then afterwards, reinstall GRUB2. This might work???

Oh, I didn't mention (this being an Ubuntu forum and all, not the place for Windows help) that I got a new NTLDR and boot.ini (I'll have to reconfigure boot.ini AFTER I get XP2 working in GRUB)

Theoretically, I could just wait until I have access to my XP CD, reconfigure boot.ini with that and leave it and NTLDR on XP1 so that it acts like it did before. I want to make XP2 independent though, so I need GRUB to recognise it properly.

**EDIT**
Fixed the Read/Write issues. I removed a bunch of options that were on it in Fstab and it works fine now.

All I'm looking for now is to fix Grub.

---

