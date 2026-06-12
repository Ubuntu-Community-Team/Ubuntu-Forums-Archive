---
title: "Using dd to image an entire disk, and ignore unpartitioned space?"
date: 2011-10-12
forum: General Help
---

### Post by SoCalChris on 2011-10-12
I've got a computer with 2 2TB drives. One drive has a Windows XP installation that I want to image, so that I can mount it as a virtual drive on VirtualBox that is running on the other drive. The Windows drive is only using about 300GB, although the whole drive is partitioned into a single 2TB partition.

If I resize that partition to 350GB leaving 1.65TB of unpartitioned space, is there a way to create an image of the whole disk which ignores the unpartitioned space? According to the VirtualBox directions, I need to image the whole drive, not just the partition.

Basically, I'm trying to follow [these directions]("https://www.virtualbox.org/wiki/Migrate_Windows"), and wind up with an image of the entire drive that is only around 350GB, so that I can convert it to a VirtualBox virtual drive. I want the virtual drive to only be around 350GB in the end, not the ull 2 TB that it is now.

Is this possible? Did my question even make sense?

Thanks

---

