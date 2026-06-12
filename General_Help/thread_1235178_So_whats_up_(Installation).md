---
title: "So whats up? (Installation)"
date: 2009-08-08
forum: General Help
---

### Post by Refreshment on 2009-08-08
Greetings fine people:

Quick recap:
-First inept rookie here. Im sorry :)
-2 HDs: 1 for Windows XP, other for Ubuntu.
-1 TB HD just with Ubuntu.
-Installed 9.04 32 bit.
-Was downloading some packages after install.
-Reboot it after packages. Stopped working didn't boot anymore.
-Decided to install 9.04 64 bit instead.
-Started from zero. Complete reformat of the 1 TB hard disk.

Works fine... BUT at boot up it shows: 
-Ubuntu 2.6.something.11
-Ubuntu 2.6.something.13

Was checking some folders and some files from the old installation remain there. Plus the 1 Tera HD was showing high 800 something Gigabytes. So obviously is the old Ubuntu 32 bit install is eating hard Disk space.

What can i do?

Secondly, im thinking about putting windows 7 in this same HD. I made a quick superficial read of the tutorial of how to do it when Ubuntu is installed first on the HD. To me, is really complex. So should i install windows 7 first and then Ubuntu? Its lets complex, correct?

And how do i do it properly so i don't have left overs from previous installs eating up HD space?

Really thanks if anyone can lend some words of advice.

---

### Post by perrti-y02 on 2009-08-08
If you get a live CD for Ubuntu and open the partition editor (System >> Administration >> Gparted I think) The delete every partition on the 1TB hard drive. this will completely remove any remnants of any installation.

You are better off installing Windoze first so that the entry is automatically in the grub menu. Otherwise you have to fiddle with grub-update which is more complex.

---

### Post by Refreshment on 2009-08-08
as

---

### Post by Refreshment on 2009-08-09
Sorry. How do you delete a post?

---

### Post by Refreshment on 2009-08-09
> **perrti-y02 said:**
> If you get a live CD for Ubuntu and open the partition editor (System >> Administration >> Gparted I think) The delete every partition on the 1TB hard drive. this will completely remove any remnants of any installation.

I think thats what i did. Remember after the 32 bit install failed to boot, took the live CD of the 64 boot version, boot it from there, erased all previous partitions and repartitioned the HardDisk. Yet it shows 2.6.something.11 and 2.6.something.13 every time i boot.

---

### Post by oldos2er on 2009-08-09
Can you post the output of **sudo fdisk -l** ?

---

### Post by Refreshment on 2009-08-10
Sorry for the delay. Heres an screen cap:

[IMG]http://img195.imageshack.us/img195/7691/tablaparticiones2.png[/IMG]

---

