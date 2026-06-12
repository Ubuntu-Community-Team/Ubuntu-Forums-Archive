---
title: "Help making a NTFS partition in my Ubuntu 10.10"
date: 2011-04-18
forum: General Help
---

### Post by Teiste on 2011-04-18
Hello all from a spanish guy living in Utah.
I did uninstall my Windows 7 from my labtop about a month ago and I installed Ubuntu 10.10. Now I wanna reinstall Windows 7 again,but everytime I try to do it I cant since I need a NTFS partition and I dont know how to make one.
Could somebody please explain me how to make one NTFS partition to re install Windows 7 again alongside Ubuntu?
Thanks a lot.

---

### Post by coffeecat on 2011-04-18
It's easy enough to make a NTFS partition in Ubuntu to install Windows 7 to, but your partition layout may be making this difficult. Open a terminal (Applications > Accessories) and post the output of this command:

```
sudo fdisk -lu
```This will show us the partition layout and someone will be able to help you from there. Please post the output between [noparse]```
 and 
```[/noparse] tags otherwise it is very difficult to read.

**EDIT**: what I should have added is that it is best to use Gparted from the live Ubuntu CD to create the partition, but let's see what your current partition layout is like first.

---

### Post by Mark Phelps on 2011-04-18
> **Teiste said:**
> Hello all from a spanish guy living in Utah.
I did uninstall my Windows 7 from my labtop about a month ago and I installed Ubuntu 10.10. Now I wanna reinstall Windows 7 again,but everytime I try to do it I cant since I need a NTFS partition and I dont know how to make one.
Could somebody please explain me how to make one NTFS partition to re install Windows 7 again alongside Ubuntu?
Thanks a lot.

You don't NEED to make an NTFS partition to install Win7.  All you need is some unallocated space on the drive.

Win 7 will put up a screen allowing you to select from a list of partitions, and will include the unallocated space in that list -- which it will then automatically format to NTFS during the install.

---

### Post by Teiste on 2011-04-18
> **Mark Phelps said:**
> You don't NEED to make an NTFS partition to install Win7.  All you need is some unallocated space on the drive.

Win 7 will put up a screen allowing you to select from a list of partitions, and will include the unallocated space in that list -- which it will then automatically format to NTFS during the install.

Thanks my friend,I already discovered and installed Windows 7 along with Ubuntu.Thanks again.

---

