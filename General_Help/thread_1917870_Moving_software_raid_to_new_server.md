---
title: "Moving software raid to new server"
date: 2012-01-30
forum: General Help
---

### Post by paddyjoy on 2012-01-30
Hi,

Hope someone can help me out here. I'm having some problems moving a software raid 1 set up to a new server.

situation is as follows:

**Old system had**
*Connected to first sata card*
/dev/sda1 = / unbuntu + /boot
/dev/sdb1 = /data (some non critical data)
[I]
Connected to second sata card[/I]
/dev/sdc1 = formated ext4
/dev/sdd1 = formatet ext4

/dev/md0 = Software raid 1 with partitions sdc1 and sdd1

Motherboard on old server (poweredge 2850) failed so picked up a second hand Dell SC1435.

New server only has physical space for 3 drives so have the following setup:

**New server**
*Connected to motherboard*
/dev/sda1 = / unbuntu + /boot

Connected to internal pci card are the two drives that formed the software raid in original setup.

When I boot the server with just /dev/sda1 connected it boots and everything works fine however as soon as I connect either or both of the raid drives the server fails to boot.

With a normal boot I get a blinking cursor and server doesn't respond to any key strokes.

When I try a recovery boot I can see the console text which give some mdadm errors before crashing like:

Bad disk dropped from array
Array unexpected increase in size from 0 to 200......
Unknow partition table

But then becomes completely unresponsive.

Is there a way I can boot ubuntu without starting mdadm so I can inspect the disks? If I could do this maybe I could try and recreate the array again, or at least mount the disks and copy the data somewhere else and start again.

Any thoughts?

---

