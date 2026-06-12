---
title: "Problem adding new hard drive"
date: 2010-10-23
forum: General Help
---

### Post by teropita on 2010-10-23
Hi,

I am having a problem booting my PC after adding a new SATA drive.

The PC has 3 drives.

SDA is a 500Gb SATA drive
SDB is a 1Tb SATA drive
SDC is a 160Gb IDE drive

The PC boots from the 160Gb IDE drive.

If I now install a 2Tb SATA drive the boot fails, it starts off OK as in the Motherboard boots from the IDE drive but sometime into the boot the / directory cannot be found.

If I boot from a live disk and check out the disks with gparted, I find that the new 2 Tb SAta drive is SDC and he 160Gb IDE drive is now SDD. I expect this is my problem but I cannot work out how to change it.

Note fstab is using UUID designations - not sure if this is relevant.

I would appreciate any help.

Thanks Steve

---

### Post by TeoBigusGeekus on 2010-10-23
> **teropita said:**
> Hi,
Note fstab is using UUID designations - not sure if this is relevant.


It is very relevant and bravo for that.
You should also check whether grub finds the correct partitions on startup.

---

### Post by jmszr on 2010-10-23
teropita,

Perhaps this will be of some help: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by teropita on 2010-10-23
Solved - Thank you for your replies - mentioning grub was the clue I needed. It was a matter of modifying /boot/grub/grub.cfg.

As it seemed that the OS would assign the sd? as it wished I couldn't get my boot drive to be assigned sdc, so I just changed all references in boot.cfg to sdd.

---

### Post by Quackers on 2010-10-23
Please mark the thread as solved using the Thread Tools near the top in red so that others may benefit. Thank you :-)

---

