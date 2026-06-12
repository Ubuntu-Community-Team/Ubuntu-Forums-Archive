---
title: "Cannot mount external hard drive (10.04)"
date: 2010-05-10
forum: General Help
---

### Post by hihihi100 on 2010-05-10
I run 10.04 lucid in a laptop with EXT4 as filesystem, and I tried to mount an external hard drive from a Windows that, obviously, uses FAT32. Its the first time I try to mount a hard drive (external) since the upgrade to 10.04. Do I have to download some packages via synaptic? If not, what do I have to do?

Plus, I have run ```
sudo fdisk -l
```and this is what I get

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00034e3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38162   306536233+  83  Linux
/dev/sda2           38163       38913     6032407+   5  Extended
/dev/sda5           38163       38913     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbe41da9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2431    19526976    c  W95 FAT32 (LBA)
```

The 320 GB section makes reference to the internal hard drive, the external hard drive I cannot mount is the 20 GB one, right below the first section (/dev/sdb)

And, could any of you explain why I cannot run just "fdisk" to make changes via terminal as "me" and not as "root"?

CHEERS

---

### Post by dino99 on 2010-05-10
yes check synaptic for the "ntfs"* packages and usbmount too, usually they are installed by default. Then install mountmanager and tweak it as you need, you should see all your devices and partitions into the left pane.

sudo update-pciids && update-usbids

---

### Post by hihihi100 on 2010-05-14
OK, I found the root of the problem:

GEM memory leak from  GLX 1.3/1.4 backport, it seems to be a quite common bug in 10.04

Anyway, in synaptic I looked for those packages, which were already installed. Since fixing the bug I can mount externals without problems.

---

### Post by jkoval on 2011-11-25
> **hihihi100 said:**
> OK, I found the root of the problem:

GEM memory leak from  GLX 1.3/1.4 backport, it seems to be a quite common bug in 10.04

Anyway, in synaptic I looked for those packages, which were already installed. Since fixing the bug I can mount externals without problems.
I have been trying for days to solve my USB mount problem,
and I suspect something different from all the current suggestions.
Can you clarify the
"GEM memory leak from GLX 1.3/1.4 backport, it seems to be a quite common bug in 10.04"
problem/solution

---

