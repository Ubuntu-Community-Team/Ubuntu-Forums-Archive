---
title: "Removing Vista Partition"
date: 2009-09-28
forum: General Help
---

### Post by SNOOPY11 on 2009-09-28
Hi  I have a dual booted 64 bit system setup as follows with Vista Ultimate and Ubuntu 9.04:   


[LIST]
[*]Unallocated - 1.00 MIB
[*] dev/sda1 - ntfs - 78.12 GIB
[*]Unallocated - 2.39 MIB
[*]dev/sda2 - ext3 - 69.85 GIB
[*]dev/sda3 - Linux-swap - 1.07 GIB
[/LIST]

I want to delete the Vista partition and expand Ubuntu to fill the whole drive.  Being a new migrant to Linux I've managed everything so far but this job I want to make sure I'm getting right!  Having read the help file I think all that is needed to remove Vista is: System - Admin - Partition Editor - (select ntfs) - Partition - Delete. 

I need to confirm this is correct and what to do then to expand Ubuntu.  Last, how do I remove the Vista boot menu option (the last in my list) ?

Many thanks in advance.

---

### Post by KlinerDraken on 2009-09-28
> **SNOOPY11 said:**
> Hi  I have a dual booted 64 bit system setup as follows with Vista Ultimate and Ubuntu 9.04:   


[LIST]
[*]Unallocated - 1.00 MIB
[*] dev/sda1 - ntfs - 78.12 GIB
[*]Unallocated - 2.39 MIB
[*]dev/sda2 - ext3 - 69.85 GIB
[*]dev/sda3 - Linux-swap - 1.07 GIB
[/LIST]

I want to delete the Vista partition and expand Ubuntu to fill the whole drive.  Being a new migrant to Linux I've managed everything so far but this job I want to make sure I'm getting right!  Having read the help file I think all that is needed to remove Vista is: System - Admin - Partition Editor - (select ntfs) - Partition - Delete. 

I need to confirm this is correct and what to do then to expand Ubuntu.  Last, how do I remove the Vista boot menu option (the last in my list) ?

Many thanks in advance.


I'm far from an expert on this topic, but you should be able to delete the ntfs partition as you stated and then you should just have one "Unallocated" space left. At which point you can format as ext3 (or other format if you choose to do so). However I do not think there is a way to expand the Ubuntu partition in to the Unallocated area.

You have to [edit your grub list file]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/") in a text editor to remove Vista from the boot menu.


Hope this helps some.

---

### Post by oboedad55 on 2009-09-28
> **KlinerDraken said:**
> I'm far from an expert on this topic, but you should be able to delete the ntfs partition as you stated and then you should just have one "Unallocated" space left. At which point you can format as ext3 (or other format if you choose to do so). However I do not think there is a way to expand the Ubuntu partition in to the Unallocated area.

You have to [edit your grub list file]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/") in a text editor to remove Vista from the boot menu.


Hope this helps some.

You probably can resize the partition by booting up from the LiveCD or better yet using Parted Magic. [http://partedmagic.com/](http://partedmagic.com/) As with all serious operations make sure to back up anything you don't want to lose first. Usually there's no problem but you don't want to take the chance.

---

### Post by hxleet on 2009-09-28
[LEFT]> You have to [edit your grub list file]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/") in a text editor to remove Vista from the boot menu.Disregard that.

Just put the cd you used to install ubuntu and use the gparted partition editor System>administration>Gparted to erase vista then your allocated space will go up and if you resize your ext3 FS you can expand to the size you want or completly use the rest of the allocated space to your ubuntu install.  like oboedad55 said back up your FS just in case but you should'nt have problems if your running from live cd.  if you delete the vista partition theres no need to edit the boot loader as ubuntu will be the only OS there

**NOTE** you can erase and resize your partition all at the same time no need to erase first wait and then resize you can do it at the same time and it will format and resize.

hxleet
[/LEFT]

---

### Post by SNOOPY11 on 2009-09-28
Sorry - should have added that I don't have the Ubuntu CD

---

### Post by oboedad55 on 2009-09-28
> **SNOOPY11 said:**
> Sorry - should have added that I don't have the Ubuntu CD

You're gonna need one of the two suggested CDs because you can't resize a partition that's mounted.

---

### Post by SNOOPY11 on 2009-09-29
Thanks for the advice and information

---

