---
title: "Locked Partition"
date: 2010-02-19
forum: General Help
---

### Post by SpartanStevo on 2010-02-19
So, I work for Cisco and I have a Lenovo T61p through work.  It comes with Cisco's XP image (loaded with crap, specifically security crap).  I run Karmic on my home computer and there are many reasons why I would like to add a dual boot to my work computer.  The biggest is that the T61p has 4gb of memory and I can't even use it (which is very important to me, because I run high memory CAD applications).  

What I would like to do is shrink the XP partition down so that I can actually put an ubuntu + swap partition on the computer.  

The problem is that when I boot my gparted disk, it tells me the xp partition is locked.  (It won't let me do anything).  

Supposedly there is a storage partition also on my computer (at least I hope because the xp partition is labeled at only 100gb and my older laptop at home has more space), but gparted can't even see that partition.  

Does anyone know how I could unlock the xp partiton (I imagine it is locked with some cisco security something or another that I can't mess with), or if there is a better way to partition it. 

Also, would wubi be a good option?

---

### Post by pricetech on 2010-02-19
Uh, leave it alone so you don't get fired for tampering with company equipment ?????

If you're having trouble changing the laptop, it should be obvious your employer doesn't want it messed with.

Just a thought.

---

### Post by efflandt on 2010-02-19
You might consider an external USB drive or flash, if you can get it to boot from that.

One possible issue with an actual USB hard drive (vs. flash) is that it might not spin up and be recognized right away by the BIOS even if set before hard drive in BIOS boot order.  So sometimes it seems like I have to go into CMOS setup with some computers, just to give it time before rebooting into USB.

My work laptop already has 4 partitions (2 Dell, and a multimedia partition that can play media without running Windows).  So I use an external drive to avoid messing anything up.

Note: If you install to external drive, pay attention to **Advanced** button at summary screen just before actual installation proceeds, to put grub on mbr of external drive, instead of default to main hard drive mbr.

---

### Post by SuperSonic4 on 2010-02-19
> **pricetech said:**
> Uh, leave it alone so you don't get fired for tampering with company equipment ?????

If you're having trouble changing the laptop, it should be obvious your employer doesn't want it messed with.

Just a thought.

Ask yourself [OP], do you think putting ubuntu on your laptop is more valuable than your job and any future jobs in that sector?

Of course the sensible answer is no

Besides, why can't you use your home PC at home and your work PC at work?

---

### Post by akakingess on 2010-02-19
> **efflandt said:**
> You might consider an external USB drive or flash, if you can get it to boot from that.

One possible issue with an actual USB hard drive (vs. flash) is that it might not spin up and be recognized right away by the BIOS even if set before hard drive in BIOS boot order.  So sometimes it seems like I have to go into CMOS setup with some computers, just to give it time before rebooting into USB.

My work laptop already has 4 partitions (2 Dell, and a multimedia partition that can play media without running Windows).  So I use an external drive to avoid messing anything up.

Note: If you install to external drive, pay attention to **Advanced** button at summary screen just before actual installation proceeds, to put grub on mbr of external drive, instead of default to main hard drive mbr.

+1 on the booting off of an external, just to keep from getting into trouble at work ;)

---

