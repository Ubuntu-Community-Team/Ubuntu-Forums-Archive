---
title: "Ubuntu won't detect Momentus® XT Solid State Hybrid Drives"
date: 2011-09-16
forum: General Help
---

### Post by Lukasz Tarkowski on 2011-09-16
Ubuntu won't detect Momentus® XT Solid State Hybrid Drives  [http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/)

I have done the upgrade to 28 firmware and still nothing

I have 2 Primary Partitions and two Logical ones.

---

### Post by dcstar on 2011-09-17
> **Lukasz Tarkowski said:**
> Ubuntu won't detect Momentus® XT Solid State Hybrid Drives  [http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/)

I have done the upgrade to 28 firmware and still nothing

I have 2 Primary Partitions and two Logical ones.

What does "won't detect" mean?

What shows up in gparted, what shows up in the Disk Utility?

---

### Post by mike555 on 2011-09-17
I just put that drive in my Acer netbook and it is much faster , boots Ubuntu in 17 seconds , pretty good for a single atom processor.plus I have the 500 GB storage.

---

### Post by Lukasz Tarkowski on 2011-09-17
It doesn't display my ntfs partitions and one empty one

---

### Post by Mark Phelps on 2011-09-17
> **Lukasz Tarkowski said:**
> It doesn't display my ntfs partitions and one empty one

OK ... but what DOES is show?

---

### Post by Lukasz Tarkowski on 2011-09-17
It doesn't show any partitions at all.  I have Windows 7 HomePremium 64 bit With Service Pack 1

---

### Post by dcstar on 2011-09-18
> **Lukasz Tarkowski said:**
> It doesn't show any partitions at all.  I have Windows 7 HomePremium 64 bit With Service Pack 1

And is the Win 7 partition a "Dynamic" partition?

---

### Post by Lukasz Tarkowski on 2011-09-18
Windows 7 SP1 partition is active and primary, I had no problems installing Ubuntu on External Hard Drive

---

### Post by dcstar on 2011-09-19
> **Lukasz Tarkowski said:**
> Windows 7 SP1 partition is active and primary, I had no problems installing Ubuntu on External Hard Drive

Sigh... Open the Windows Disk Manager and find out if the drive is "Basic" or "Dynamic".

---

### Post by Lukasz Tarkowski on 2011-09-19
The Windows 7 Sp1 partition C:\NTFS is set to Basic.  Is that the problem?

---

### Post by Lukasz Tarkowski on 2011-09-19
by the way I would not suggest converting to a dynamic drive, cause Windows 7 SP1 won't boot then

---

