---
title: "CLI partition manager with ext4 support?"
date: 2010-04-02
forum: General Help
---

### Post by Saosin7 on 2010-04-02
Hi all!

I recently bought a new HDD for my server and I now need to create two differently sized ext4 partitions. I tried GNU parted, but it can't create ext4 partitions so I did some googling but couldn't find any CLI partition managers with ext4 support :(

Anyone know of one?

Btw, the server is running Ubuntu 9.10 x64 Server.

Thanks in advance!

---

### Post by sisco311 on 2010-04-02
You can use fdisk to create the partition table & mkfs.ext4 to create an ext4 filesystem in the partition(s).

EDIT:
[uhelp]community/InstallingANewHardDrive[/uhelp]

---

### Post by Saosin7 on 2010-04-04
Thanks for pointing me in the right direction sisco! It works perfectly now :D

---

