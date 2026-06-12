---
title: "Multiple Linux Installs?"
date: 2012-01-30
forum: General Help
---

### Post by chughes27 on 2012-01-30
So, I'm loving my new Ubuntu 11.10, but I would also like to try out other Linux distros. I do not want to lose my Ubuntu install as I like it the way it is, I just want to test my other options.

I am already dual-booting Windows XP and Ubuntu 11.10, so can I install more versions of Linux to test them? And how would I go about doing that?

---

### Post by deserthowler on 2012-01-30
> **chughes27 said:**
> 
I am already dual-booting Windows XP and Ubuntu 11.10, so can I install more versions of Linux to test them? And how would I go about doing that?

All that is necessaary is to make space for them using gparted from a live CD and install just as you did your initial install.  It isn't as complex as it might seem.

Earl

---

### Post by carl4926 on 2012-01-30
> **chughes27 said:**
> So, I'm loving my new Ubuntu 11.10, but I would also like to try out other Linux distros. I do not want to lose my Ubuntu install as I like it the way it is, I just want to test my other options.

I am already dual-booting Windows XP and Ubuntu 11.10, so can I install more versions of Linux to test them? And how would I go about doing that?

You need to understand how to setup multiple partitions.
It's likely that your current scheme will not allow for much to be done. Generally you have to think about this well ahead of time.

Post the result of
```
sudo fdisk -l
```
And if you can, a image of sda in GParted

---

### Post by chughes27 on 2012-01-30
Here's the result, I have little idea what most of it means. Maybe if I can understand some of this better it may help me...


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x54ac320b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8390655     4194304   12  Compaq diagnostics
/dev/sda2   *     8390656   113248255    52428800    7  HPFS/NTFS/exFAT
/dev/sda3       113248256   312578047    99664896    7  HPFS/NTFS/exFAT

---

### Post by carl4926 on 2012-01-30
You have a wubi install?

---

### Post by chughes27 on 2012-01-30
Yes

---

### Post by carl4926 on 2012-01-30
> **chughes27 said:**
> Yes
That's not a proper install.

If you can add another HD, that would be the way to go IMO

---

### Post by chughes27 on 2012-01-30
That's my problem. I don't want to have to get a new HDD or anything difficult. I just want an easy solution.

I suppose I can testdrive each distro in virtualbox and consider a new HDD later or wait for my new laptop.

---

