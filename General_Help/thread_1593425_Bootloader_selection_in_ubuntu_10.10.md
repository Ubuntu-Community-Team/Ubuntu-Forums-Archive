---
title: "Bootloader selection in ubuntu 10.10"
date: 2010-10-11
forum: General Help
---

### Post by Ratul Saha on 2010-10-11
Hi,
In the choice of bootloader when installing manually, why should I select dev/sda ( the whole )? I have win7 also and I want to keep it. Is there any chance of formatting the whole?

---

### Post by oldfred on 2010-10-11
When it says sda, that is the MBR where the grub boot loader will be installed. It does not mean the sda drive will be reformated. (Of course if you install Ubuntu to the entire drive that will erase everything.) Grub will give you a choice to boot windows as long as your windows is bootable.

Computers boot from the MBR or the first sector before the partitions start. Old computers with IDE drives booted from the primary master's MBR as the BIOS was only smart enough to know which drive was on the primary channel and which drive was master. Now with SATA you can usually select which drive to boot from, but that is still booting from the MBR of that drive.

---

