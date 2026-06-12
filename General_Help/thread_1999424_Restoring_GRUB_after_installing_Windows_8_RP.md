---
title: "Restoring GRUB after installing Windows 8 RP"
date: 2012-06-08
forum: General Help
---

### Post by samjad51 on 2012-06-08
Hey guys, 

I am using Ubuntu 12.04, just installed Windows 8 Release Preview. I lost GRUB from being my default boot manager, how can I restore this?

Before installing Windows 8 RP, I checked where my Ubuntu files were from gparted and they are as follows;

On drive "/dev/sdb"
linux-swap /dev/sdb1        |FLAGS: BOOT
extended   /dev/sdb2
  ext4     /dev/sdb5        |MOUNT POINT: /

I have the live cd, however am not sure what to do, and nor do I wish to reinstall ubuntu.

Thanks in advance :)

---

### Post by wilee-nilee on 2012-06-08
> **samjad51 said:**
> Hey guys, 

I am using Ubuntu 12.04, just installed Windows 8 Release Preview. I lost GRUB from being my default boot manager, how can I restore this?

Before installing Windows 8 RP, I checked where my Ubuntu files were from gparted and they are as follows;

On drive "/dev/sdb"
linux-swap /dev/sdb1        |FLAGS: BOOT
extended   /dev/sdb2
  ext4     /dev/sdb5        |MOUNT POINT: /

I have the live cd, however am not sure what to do, and nor do I wish to reinstall ubuntu.

Thanks in advance :)

Take a look at the boot-repair app, run the recommended fix, and if you have problems, post the HTTP of the bootinfo summary.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

