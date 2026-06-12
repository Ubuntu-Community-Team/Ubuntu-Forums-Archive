---
title: "Grub Error 22"
date: 2006-05-26
forum: General Help
---

### Post by adduds on 2006-05-26
Hi All!!!!

I have a dual HD desktop computer. Master = XP, slave = BB 5.10. I overwrote the XP boot manager w/ grub for the dual boot. Following? :p . I now have a problem, my computer will now not boot, it's worked for months now, everytime I boot it says Grub 1.5 Error 22. and it won't boot, so i cannot get into windows or Linux. Ideally I'd like to remove linux from the slave drive and have it just as storage for XP and to re-install the Windows Boot Manager. How do i do all this? Thanks to all whom help :)

cheers,
ad

---

### Post by Sef on 2006-05-26
> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

Did you keep Windows as the primary boot partition?

HowTo to [Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by mjziegle on 2006-05-26
Your problem may be the way devices are ordered in grub.

Can you get to the grub command line?

Try changing the 

root(hd0,0) to root(hd1,0) 

or from the live CD for your version of Ubuntu do a 

grub-install /dev/(your bootable hard drive)

what's your menu.1st look like?

Grub problems are hard to diagnose.

---

### Post by Mustard on 2006-05-26
Do you have your XP CD?

---

### Post by catlett on 2006-05-26
[QUOTE=Mustard]Do you have your XP CD?[/QUOTE] To follow up on this. If you have an XP install disk or your recovery disks from your computer maker you can fix your windows boot loader. Put the disk in and boot. Choose recovery mode and you will eventually be at a command prompt. Enter this at the prompt C:\ ```
fixmbr
```
This will overwrite the Master Boot Record with the windows bootloader and you will be able to boot to windows like before. You won't be able to boot to ubuntu but it looks like that doesn't matter to you.

---

### Post by adduds on 2006-05-27
[QUOTE=catlett]To follow up on this. If you have an XP install disk or your recovery disks from your computer maker you can fix your windows boot loader. Put the disk in and boot. Choose recovery mode and you will eventually be at a command prompt. Enter this at the prompt C:\ ```
fixmbr
```
This will overwrite the Master Boot Record with the windows bootloader and you will be able to boot to windows like before. You won't be able to boot to ubuntu but it looks like that doesn't matter to you.[/QUOTE]

That's great info! I got up to recover consol and it select 1 Enter for C:\

but then it asks me for an Administrator password???? Is their a default pass?

cheers,
ad

---

### Post by catlett on 2006-05-27
It's whatever your windows password is. Almost all people who make a windows account make an administrator account instead of a user account (you see why windows has so many security issues, everyone is running under administrator priveleges)
Anyways when you enter 1 this is putting you inside your xp install. You are most likely an administrator on that system(as already described). Just type in your regular windows password. If you didn't make a windows password, I don't know what will happen. It may mean leave it blank and just press enter.

---

