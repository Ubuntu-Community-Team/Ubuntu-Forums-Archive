---
title: "Reinstalled grub2, but Windows 7 still loads and bypasses grub2"
date: 2010-05-04
forum: General Help
---

### Post by devosion on 2010-05-04
On this dual-boot machine I have Ubuntu installed on hd0 (/dev/sda), Windows 7 is installed on hd1 (/dev/sdb). The mbr for Ubuntu is on /dev/sda1. After installing Windows I went through the steps to reinstall grub2 on /dev/sda1, but Windows 7 kept loading. So I went ahead and upgraded to 10.04, expecting the upgrade to overwrite the correct MBR, but this didn't work either. When I was looking at the advanced options in the 10.04 installation I noticed Windows 7 had an MBR in /dev/sdb2. If I installed grub2 to this partition should it overwrite 7's bootloader and allow me to load from grub2? Or is there something else I should be looking for to resolve this problem?

---

### Post by lechien73 on 2010-05-04
I would suggest you check your boot order in the BIOS, or do you have a "Boot Options" prompt when starting up your PC? It looks like your system is automatically attempting to boot from the second hard drive.

---

### Post by devosion on 2010-05-04
Wow, can't believe I missed that. I suppose after messing around the bios as much as I have been for the last couple of days made me forget something I should have checked out the first time. Thanks!

---

