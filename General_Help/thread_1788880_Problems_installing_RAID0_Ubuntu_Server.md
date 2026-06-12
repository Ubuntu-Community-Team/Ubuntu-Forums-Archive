---
title: "Problems installing RAID0 Ubuntu Server"
date: 2011-06-23
forum: General Help
---

### Post by dirtrider1 on 2011-06-23
I have been having trouble trying to reinstall a RAID0 on my server with two Pata disks on an HP Proliant ml330 G3 with Ubuntu server 10.04 32bit. The setup was working fine until I decided to format and reinstall. I'm using software raid with three raid volumes, one for root,swap and home and a non raid boot partition on the first drive. The installation goes fine until it restarts and I get this error when the computer tries to boot into the newly installed system  error: unknown filesystem. grub rescue>_  ?

---

### Post by dirtrider1 on 2011-11-05
Figured it out it seems on some of the older HP Proliant servers you must specify ext2 for the boot partition as well as I had to update the bios to support booting off a drive that was 1TB

---

