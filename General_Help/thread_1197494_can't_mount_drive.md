---
title: "can't mount drive"
date: 2009-06-26
forum: General Help
---

### Post by ene_dene on 2009-06-26
I use Ubuntu 9.04, x64bit.
I have two hard drives:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000552e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      489951   83  Linux
/dev/sda2              62        2006    15623212+  82  Linux swap / Solaris
/dev/sda3            2007       60801   472270837+   5  Extended
/dev/sda5            2007       60801   472270806   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006075

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625129281   83  Linux

```

Today I made updates and was required to restart Ubuntu, after restart I got grub, boot starts but it seems that it can't mount sda5.

Now I'm in ubuntu liveCD, I can mount all the drives except sda5:
```

sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5

```
After that I get:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
What seems to be the problem?


I read that some people had a problem that ubuntu mixed up their drives, but I don't understand why can't I mount the drive.

I'm hope it's not a hard drive error.

---

### Post by billgoldberg on 2009-06-26
Are you using EXT4? It still has some bugs.

Did you try running fsck?

Did you check what the system log said, as the last error message told you?

---

### Post by ene_dene on 2009-06-26
> **billgoldberg said:**
> Are you using EXT4? It still has some bugs.
Yes I am, as it said in previous post. I can mount other ext4 partitions, but this one I can't for some reason.

[QUOTE=billgoldberg]Did you try running fsck?[/quote]
No I didn't. I don't know how to use it. Could you help? Is there a danger of loosing data?

[QUOTE=billgoldberg]Did you check what the system log said, as the last error message told you?[/QUOTE]
When trying to mount I get this in syslog:
```
Jun 26 12:01:01 ubuntu kernel: [ 9797.720738] EXT4-fs: ext4_check_descriptors: Block bitmap for group 1152 not in group (block 4279052320)!
Jun 26 12:01:01 ubuntu kernel: [ 9797.720743] EXT4-fs: group descriptors corrupted!

```
It doesn't help me how to solve a problem. Can you make something out of it?

---

### Post by ene_dene on 2009-06-26
I started gparted in live cd and checked disk, that helped, everything is working now.

---

