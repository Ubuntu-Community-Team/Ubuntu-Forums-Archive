---
title: "Upgrade to 64bit and Pulse Audio Question"
date: 2009-09-30
forum: General Help
---

### Post by Catalyst2Death on 2009-09-30
Rather than starting two threads, I thought I would ask a couple questions here.

1st: 

I want to upgrade to 64bit version when Karmic comes out, and I have some related questions:

1)  Can I preserve my home area?  I have them on separate partitions, so reformatting the system is easy, but are there going to be settings conflicts etc?

2)  Can I mount my home as ext4 safely without losing data?

2nd:

I have my speakers set up through a stereo receiver, and I play vinyl through the receiver as well.  The volume for the vinyl is much higher than the volume that I want for the pc output, so what I'm wondering if there is anyway to force Pulse Audio to output at a higher volume.

---

### Post by Catalyst2Death on 2009-10-05
Friendly bump,

Is there anyone who can answer my file system questions?  The PA question is more of an annoyance thing than a real issue, but the upgrade to 64bit with my current setup could be a deal breaker...  Here is how my computer is partitioned:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc78fd82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9809    78786560    7  HPFS/NTFS
/dev/sda2            9810       11721    15358140   83  Linux
/dev/sda3           11722       11852     1052257+  82  Linux swap / Solaris
/dev/sda4           11853       60801   393182842+   5  Extended
/dev/sda5           11853       60801   393182811   83  Linux

```

sda1 -> windows
sda2 -> system partition "/"
sda3 -> swap (probably will grow to size of ram so that I can hibernate)
sda5 -> /home/

---

### Post by NoaHall on 2009-10-05
1)
Yes, you can keep your home.

2) 
There is a way of upgrading it, but it's risky - it's best to stick to ext3 if you want to keep it.

---

