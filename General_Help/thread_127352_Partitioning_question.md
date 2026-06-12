---
title: "Partitioning question"
date: 2006-02-08
forum: General Help
---

### Post by aseem_mal on 2006-02-08
Hi. I am planning to do a dual boot install of Win XP and Ubuntu. And this below is the partitioing setup i am planning for my 60 GB Hard Disk:
> 

Total Size: 60 GB:

 / - Ext3 - 10GB - Bootflag On
 /Home - Ext3 - 19GB - Bootflag Off
 /swap 1GB - Bootflag - On
 WinXP - Fat32 - 30GB



My Questions here are:

1. Do I really need to allocate 10 GB for the root? Or can I set it to 5 GB?
2. Are my Bootflag settings ok?

Thanks,
A

---

### Post by aysiu on 2006-02-08
5 GB should be sufficient.

---

### Post by aseem_mal on 2006-02-08
Can someone comment on my bootflag settings too? And I hope having 5 GB for the / partition  won't create any issues in future?

Again, here's what i am planning:
> 

Total Size: 60 GB:

/ - Ext3 - 10GB - Bootflag On
/Home - Ext3 - 19GB - Bootflag Off
/swap 1GB - Bootflag - On
WinXP - Fat32 - 30GB



Thanks,
A

---

### Post by az on 2006-02-08
The windows partition should come first, since it does not play well with the other kids.

Forget about the bootflags - they are irrelevant.

---

### Post by dcstar on 2006-02-08
[QUOTE=azz]The windows partition should come first, since it does not play well with the other kids.
......[/QUOTE]
Have to disagree here, sometimes Grub don't like being put too far up the disk, and having the Windoze partition first runs the risk of that.

---

### Post by aysiu on 2006-02-08
If I had 60 GB of hard drive (can we assume you also have 512 MB of RAM, since you allocated 1 GB for swap?), this is what I'd do:

8 GB Windows XP (NTFS)
45 GB Shared files (FAT32)
1 GB /home (Ext3)
1 GB swap (swap)
5 GB / (Ext3)

My reasoning: 
1. I agree with Azz, Windows likes to be first.
2. XP runs better on NTFS, not FAT.
3. The FAT32 partition should be the largest, since presumably a dual boot means you'll be sharing files between both operating systems.
4. A separate /home partition is good because you may have to reinstall Ubuntu at some point (when I first started, I reinstalled probably every few days or so because I kept screwing up my system, experimenting), but it basically just stores your settings and preferences--it doesn't have to be that large.
5. 5 GB is plenty for the rest of the Ubuntu operating system.

---

### Post by aysiu on 2006-02-08
[QUOTE=dcstar]Have to disagree here, sometimes Grub don't like being put too far up the disk, and having the Windoze partition first runs the risk of that.[/QUOTE] Maybe that's true, but I've not found that to be the case. My Grub is currently on /dev/hdb1 and my Windows partition is at /dev/hda1. /dev/hda totals 160 GB. Never had a problem. I've put Grub on /dev/hda5, /dev/hda7. Again, never had a problem.

---

