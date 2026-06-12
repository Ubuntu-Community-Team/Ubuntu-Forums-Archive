---
title: "just about to install ubuntu, but which drive to i install the boot loader to?"
date: 2010-08-15
forum: General Help
---

### Post by princeofnam on 2010-08-15
if I installed Windows 7 on sda and then Ubuntu on sdb partitioned as

sdb1 -swap
sdb2 - /
sdb3 - /home

what do i set for "device for boot loader installation:"

sda
sda1
sdb
sdb2
sdb3

i'm assuming sdb?

---

### Post by Sef on 2010-08-15
I would set the boot loader for the default install.

---

### Post by elliotn on 2010-08-15
> **sef said:**
> i would set the boot loader for the default install.

+1

---

### Post by princeofnam on 2010-08-15
the default was sda, but wouldn't that be installing it on the windows 7 hdd? i thought it was prudent to install it on the hdd containing ubuntu

---

### Post by DeMus on 2010-08-15
> **princeofnam said:**
> the default was sda, but wouldn't that be installing it on the windows 7 hdd? i thought it was prudent to install it on the hdd containing ubuntu

No, it should be on the master boot record of the first disk which boots, mostly SDA. Windows wrote its bootlader there too, Ubuntu has to overwrite this with grub so you will get a list of choices what to boot.

---

### Post by Ginsu543 on 2010-08-15
I like to keep my bootloader on the same drive as the primary OS it boots. So if my Ubuntu is being installed onto /dev/sdb, I put the bootloader there as well. However, if you do it this way, then you MUST change the boot order in your BIOS so that /dev/sdb is the first one. This will take care of the problem DeMus raises. I like doing it this way because it keeps my multiple OSes all on their respective partitions (and I don't overwrite the Windows bootloader with GRUB2, all the while being able to load Windows from GRUB2 if I choose).

---

### Post by mike555 on 2010-08-15
If SDB is an external drive then install grub to it , but if SDB is an internal drive install to SDA .

---

### Post by vttay03 on 2010-08-15
> **Ginsu543 said:**
> I like to keep my bootloader on the same drive as the primary OS it boots. So if my Ubuntu is being installed onto /dev/sdb, I put the bootloader there as well. However, if you do it this way, then you MUST change the boot order in your BIOS so that /dev/sdb is the first one. This will take care of the problem DeMus raises. I like doing it this way because it keeps my multiple OSes all on their respective partitions (and I don't overwrite the Windows bootloader with GRUB2, all the while being able to load Windows from GRUB2 if I choose).

+1

This is exactly what I do.  If anything ever were to happen to the disk Ubuntu is installed on, you'll still be able to boot Windows since you kept the bootloader intact.

---

### Post by topCturV on 2010-08-15
> **Ginsu543 said:**
> I like to keep my bootloader on the same drive as the primary OS it boots. So if my Ubuntu is being installed onto /dev/sdb, I put the bootloader there as well. However, if you do it this way, then you MUST change the boot order in your BIOS so that /dev/sdb is the first one. This will take care of the problem DeMus raises. I like doing it this way because it keeps my multiple OSes all on their respective partitions (and I don't overwrite the Windows bootloader with GRUB2, all the while being able to load Windows from GRUB2 if I choose).

> **vttay03 said:**
> +1

This is exactly what I do.  If anything ever were to happen to the disk Ubuntu is installed on, you'll still be able to boot Windows since you kept the bootloader intact.

+2
I do the same but use the Win7 bootloader(thru a freeware program, EasyBCD) to choose the O.S.

---

