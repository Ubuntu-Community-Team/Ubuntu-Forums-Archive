---
title: "Grub cannot find Windows 7 after Windows 8 install"
date: 2012-06-04
forum: General Help
---

### Post by x-shaney-x on 2012-06-04
Last night I installed the latest Windows 8 preview which, as expected, wiped out grub.
Afterwards I booted up a live cd and installed grub back to mbr but found it will not find Windows 7 anymore.
I installed the Windows 8 dev preview a while back and had no such trouble.

Further info:

Windows 8 was installed from an iso to it's own partition, NOT installed or upgraded over Windows 7.
I use an 01_custom grub file which displays my custom grub entries with the auto added os-prober entries below.

The os prober entries list Windows 8 loader on /dev/sda2
Windows 8 is actually installed on /dev/sda10
If I boot Windows 8, it gives the option of booting either 8 or 7 but if I choose 7 then the system instantly reboots.

---

### Post by wilee-nilee on 2012-06-04
> **x-shaney-x said:**
> Last night I installed the latest Windows 8 preview which, as expected, wiped out grub.
Afterwards I booted up a live cd and installed grub back to mbr but found it will not find Windows 7 anymore.
I installed the Windows 8 dev preview a while back and had no such trouble.

Further info:

Windows 8 was installed from an iso to it's own partition, NOT installed or upgraded over Windows 7.
I use an 01_custom grub file which displays my custom grub entries with the auto added os-prober entries below.

The os prober entries list Windows 8 loader on /dev/sda2
Windows 8 is actually installed on /dev/sda10
If I boot Windows 8, it gives the option of booting either 8 or 7 but if I choose 7 then the system instantly reboots.

Use the boot-repair tool, just run the bootinfo summary at this point and post the HTTP address to it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

