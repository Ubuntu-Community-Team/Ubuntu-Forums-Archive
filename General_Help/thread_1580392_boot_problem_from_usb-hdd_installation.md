---
title: "boot problem from usb-hdd installation"
date: 2010-09-23
forum: General Help
---

### Post by TOM_C_A_T on 2010-09-23
I just installed ubuntu 10.04 on my usb-hdd.

I partitioned it as follows,

1st primary partition 134 gb as secondary storage, ntfs.

2nd primary partition of 16gb where I installed ubuntu,
i.e., sda2...

I did not partitioned /swap n /boot and kept only / partition while formatting.

Since I don't want a multiboot or grub...

( I don't want any contact of xp and my linux...want it to keep limited to the only partition, not even the other partition where I store data. My family uses the computer, too. So, I disconnected internal HDD while installing)

I checked to install boot files on sda2 instead of just sda
Installer showed a successful installation.
but could not boot later.

It showed just " operating system missing " when I restarted the PC.

I want to just connect the UsB-HDD, boot by selecting from the boot device list in bios (F11 key) and use ubuntu.

Help needed guys !

Thanks in advance !

---

### Post by C.S.Cameron on 2010-09-23
I think the boot files should go on sda not sda2.
You should be able to just reinstall grub to there.

---

