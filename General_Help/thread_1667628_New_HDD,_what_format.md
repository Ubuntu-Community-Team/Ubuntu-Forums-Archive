---
title: "New HDD, what format?"
date: 2011-01-15
forum: General Help
---

### Post by Howy on 2011-01-15
I bought this lovely Iomega Prestige HDD with 2TB. It looks good on the outside, but the disk is formatted as NTFS... possibly for Windows compatibility, but it wont do when i want to use it for system backups. (Thats what i intend to use it for. Because, last weekend, i almost lost all my data, so its in its place to go for a safe backup solution that is external.)
So my question is... which filesystem do you recommend? Should i just go for Ext4 or is there something better suited?
The HDD will be turned off most of the time, and i want backup-time to be minimal. (NTFS is a snail in comparison to Ext4...)
I've used Ext4 for my internal backup-partition, but i cant use an internal one because its not as safe as one i unplug externally.

Also, i want to know... is there any way that i could make it an even better backup-solution? Like installing a micro-OS on a small partition of the external drive? I could use it for restoring the data if my OS goes to hell. (Which it might do at any boot, because the partition table is screwed up so much that Disk Manager doesnt want to look at it, or doesnt start, and GParted pukes when seeing it, aka. doesnt show the part table.)

Thanks in advance. :popcorn:

---

### Post by vanadium on 2011-01-15
No doubt. ext4.

There is no better backup-solution than having a very regular backup to your drive.

---

### Post by bikodog on 2011-01-15
i have ext4 on an external 800GB. rsync /home monthly and no worries!

---

### Post by zeroseven0183 on 2011-01-15
If you're not going to share your files on a Windows computer, then I say, yes, go for EXT4.

You can check out Deja Dup Backup Tool in the Software Center.

---

### Post by zeroseven0183 on 2011-01-15
If you're not going to share your files on a Windows computer, then I say, yes, go for EXT4.

You can check out Deja Dup Backup Tool in the Software Center.

---

### Post by Howy on 2011-01-15
Ok, so its obviously Ext4 ill go for.
Personally i use Back in Time. It works better for me. (I back up all of my system files, and it does that.)

---

