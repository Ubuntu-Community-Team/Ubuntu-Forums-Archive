---
title: "Need fast help sudo: grub command not found"
date: 2011-08-10
forum: General Help
---

### Post by Bart92 on 2011-08-10
Hi,                                                      '' Ubuntu 11.04''

I have used G-parted to make some free space for my windows partition '' 100 GB ''
But before windows is installed the Grub loader is already broken .
So i decided to restore the GRUB in the live CD en start with sudo grub 

and i get this:
-------------------------------------------------------------------------------------------------------------
**sudo grub**

sudo: grub: command not found

**sudo /sbin/grub**

sudo: /sbin/grub: command not found

--------------------------------------------------------------------------------------------------------------

PLEASE HELP ](*,)

Thanks

---

### Post by Bart92 on 2011-08-10
Nobody ?

---

### Post by ajgreeny on 2011-08-10
That command is for the old legacy version of grub;  11.04 uses grub2.

Use the **Grub2 Basics** link in my signature to find out how to restore grub2 using a live CD/USB.  You need to scroll down to section 13.

---

### Post by Bart92 on 2011-08-10
> **ajgreeny said:**
> That command is for the old legacy version of grub;  11.04 uses grub2.

Use the **Grub2 Basics** link in my signature to find out how to restore grub2 using a live CD/USB.  You need to scroll down to section 13.

Thanks,

I also find out that you can fresh install ubuntu 11.04 and keep all your files
So basically you can install Ubuntu first then windows and then Ubuntu again without deleting 
all your files and programs/packages.

---

### Post by ajgreeny on 2011-08-10
> **Bart92 said:**
> Thanks,

I also find out that you can fresh install ubuntu 11.04 and keep all your files
So basically you can install Ubuntu first then windows and then Ubuntu again without deleting 
all your files and programs/packages.
Yes, you certainly can, though it's easier to have windows first, then install ubuntu, as there is then no need to restore the grub bootloader.

---

