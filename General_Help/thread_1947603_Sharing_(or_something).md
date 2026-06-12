---
title: "Sharing (or something)"
date: 2012-03-26
forum: General Help
---

### Post by m5K5n on 2012-03-26
I've had Ubuntu installed on a partition for a year or two, but it has finally given out.  So before I install Ubuntu on a partition on my new computer, I have to ask something...

When I would go on Ubuntu, there was an option that said "196GB File System" or something, that I could use to access the entirety of the Windows 7 part of the harddrive.  I could delete files, modify them, transfer files from one side to another, and such.

I was wondering: was doing this a bad thing?  Did I mess up my harddrive by "crossing over" between operating systems like that?

Note: I had a HDD on both my "old" computer and my coming new one.  It had Lucid, and I plan on installing the latest version of Ubuntu on my new computer.

---

### Post by yetiman64 on 2012-03-27
The ntfs-3g driver used in Ubuntu can both read and write to NTFS partitions, so you will see your windows partitions in Ubuntu.

I advise against writing to a Windows System partition directly, as any corruption in the writing can potentially stop the Windows OS from booting altogether. 
It is more advisable to set up a shared NTFS data partition for both the systems to access, no risking the Windows OS install that way.

I don't have enough info to go on to say if that is what caused your problems, it is possible if booting Windows 7 became a concern primarily.

---

### Post by m5K5n on 2012-03-28
> **yetiman64 said:**
> The ntfs-3g driver used in Ubuntu can both read and write to NTFS partitions, so you will see your windows partitions in Ubuntu.

I advise against writing to a Windows System partition directly, as any corruption in the writing can potentially stop the Windows OS from booting altogether. 
It is more advisable to set up a shared NTFS data partition for both the systems to access, no risking the Windows OS install that way.

I don't have enough info to go on to say if that is what caused your problems, it is possible if booting Windows 7 became a concern primarily.

Alright, well...

1) How do I set up a shared partition?
2) Can I disable whatever it is that allows me to read/write to the Windows partition?  Is this even a feature in versions later than Lucid?

---

### Post by yetiman64 on 2012-03-28
> **m5K5n said:**
> Alright, well...

1) How do I set up a shared partition?
2) Can I disable whatever it is that allows me to read/write to the Windows partition?  Is this even a feature in versions later than Lucid?
1. When you partition with gparted create a second NTFS formatted partition. This can be a logical partition (as it will not be booted by Windows) inside an extended partition if you do not have spare primaries (limit of 4 primary partitions on an MBR disk). Both Windows and Ubuntu will be able to see it. With Windows, if it doesn't get allocated a drive letter assignment automatically, you may need to go into the Disk Management Console and allocate one manually.

2. That would need to be done in /etc/fstab with an entry to block it being mounted automatically. Normally I use the "defaults" for NTFS mounts and am not sure of the other options you would need. Please wait for further advice re NTFS mount options for blocking automatic mounting.

---

