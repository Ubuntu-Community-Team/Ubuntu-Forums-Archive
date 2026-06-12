---
title: "Sporadic GRUB error 18 prevents boot"
date: 2010-05-12
forum: General Help
---

### Post by macho on 2010-05-12
In the past month or two I've run into a strange problem where Grub gives error 18 "Selected cylinder exceeds maximum supported by BIOS". Strange because:

1) after a few tries it mysteriously starts working again without any change on my part
2) I am not running a dual boot system, which seems to be the usual cause of this problem
3) though I have SATA hard drives, I have the RAID capabilities disabled in the BIOS, which can also apparently lead to this problem.

Any ideas what could be causing this? I'm currently running lucid but it also happened once before I upgraded. It seemed to start happening not too long after I installed a new 1TB drive, though that drive is only mounted under /mnt/backup, and not anywhere else of importance, so it may be a coincidence.

Here are some specs on my machine:

BIOS is ALive NF6G-VSTA P1.80
I have 2 SATA drives (no IDE drives except DVD-ROM):
/dev/sda is a 200GB Samsung drive with two partitions
- sda1 is about 197GB and includes / (including /boot)
- sda2 is about 3GB of swap
/dev/sdb is a 1TB Western Digital Drive
- 1 partition mounted at /mnt/backup

If the problem is that I don't have a separate partition for /boot, shouldn't the error show up every time I boot, not just once in a while? Any thoughts on what the problem could be are appreciated.

---

### Post by macho on 2010-05-24
The problem seems to have been that my hard drive was failing. I'm now getting more varied and more frequent erratic behaviour.

---

