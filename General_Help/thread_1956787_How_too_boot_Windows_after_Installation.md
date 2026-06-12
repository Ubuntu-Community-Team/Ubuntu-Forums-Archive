---
title: "How too boot Windows after Installation"
date: 2012-04-11
forum: General Help
---

### Post by theKingJan on 2012-04-11
Hi,
i like to install ubuntu like this with wubi :
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

So after the instalation i have Windows Vista and Ubuntu, or ?

How can i choose what i like to boot?
Thanks

---

### Post by jadtech on 2012-04-11
up and down arrow key windows should be first do nothing and it will default to window use the down key hit enter and it will boot ubuntu ..

---

### Post by theKingJan on 2012-04-11
Thanks

is it the same method if i install ubuntu with an DVD next to Windows?

---

### Post by bcbc on 2012-04-11
First reboot with Wubi (on Vista/7/8 ) boots straight into Ubuntu to complete install. Thereafter, you get the choice of Windows (default) or Ubuntu.

Installing from the DVD or by booting from a CD/USB will do a proper dual boot (requires separate partitions or will create them - wubi uses a virtual partition).

---

### Post by jadtech on 2012-04-11
its the same like bcbc said boot ubuntu  first I don't think the first time it give you an option it goes right to  installing and to the login  for ubuntu.. 

if you  partition to share next to windows be sure to have your window recovery disk ready to fix the Master boot record, its not unusual to have to make a fix when you set up dual boot and make partition changes.

---

### Post by Mark Phelps on 2012-04-12
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by theKingJan on 2012-04-13
:N itThank you all ;)

So i like Tor install Ubuntu with a DVD and with another Partition.
Next To Windows Vista with a Dual Boot

So First i make a Partition under Vista, now i have C: For Vista (ca.100 GB) ans D: (ca. 120 GB). 
I will make E: For Ubutu with 20 GB

Then i take a DVD and Boot Ubuntu and install it on E:.

I have three questions: 

1. Can i do it like i Tell you ?
2. I have the asus Recovery CD. But i don't understand why i need it .
3. How ca i change between Vista and Ubuntu?

Thank you

Jan

---

