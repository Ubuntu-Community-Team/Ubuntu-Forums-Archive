---
title: "Remove windows, keep Linux"
date: 2009-08-01
forum: General Help
---

### Post by jacklinux on 2009-08-01
Hi
Erm i was wanting to know how do i remove XP from the hardrive and only keep my Ubuntu installation?
i wish to keep all files on the ubuntu part so Format is not an option, Thanks.

---

### Post by lisati on 2009-08-01
> **jacklinux said:**
> Hi
Erm i was wanting to know how do i remove XP from the hardrive and only keep my Ubuntu installation?
i wish to keep all files on the ubuntu part so Format is not an option, Thanks.

Please do not start duplicate threads, it can get confusing for the volunteers who are trying to help.

---

### Post by jacklinux on 2009-08-01
> **lisati said:**
> Please do not start duplicate threads, it can get confusing for the volunteers who are trying to help.
Sorry, wasn't sure what forum it was best in.

---

### Post by Rob_H on 2009-08-01
I assume you're dual booting, so the first task is to remove the Windows entry from the GRUB boot menu. Do this by editing /boot/grub/menu.lst as root. Comment out the block of lines for the Windows partition. Then you can either format the Windows partition and use it as a secondary storage area for Linux, or you can try resizing your existing Ubuntu partition with GParted to recover the unused space.

---

### Post by jacklinux on 2009-08-01
> **Rob_H said:**
> I assume you're dual booting, so the first task is to remove the Windows entry from the GRUB boot menu. Do this by editing /boot/grub/menu.lst as root. Comment out the block of lines for the Windows partition. Then you can either format the Windows partition and use it as a secondary storage area for Linux, or you can try resizing your existing Ubuntu partition with GParted to recover the unused space.
what i wanted to do was to remove XP so the hardrive had more space for ubuntu program/installations however i don't know how to edit most things. i was looking for something like 'boot and nuke' so i could get rid of XP with a simple 'delete'. would i be best just formatting the hardrive and booting ubuntu from a ISO?

---

### Post by Rob_H on 2009-08-01
Oh, so you don't have Ubuntu installed on the PC at all? In that case, just boot up with the Live CD and install Ubuntu that way. One of the options during install is to use all available space on the hard drive for Ubuntu, which will effectively "nuke" XP,

---

### Post by jacklinux on 2009-08-01
> **Rob_H said:**
> Oh, so you don't have Ubuntu installed on the PC at all? In that case, just boot up with the Live CD and install Ubuntu that way. One of the options during install is to use all available space on the hard drive for Ubuntu, which will effectively "nuke" XP,
No, im dual booting Ubuntu and windows XP.

---

### Post by Post Monkeh on 2009-08-01
what rob said.

boot up off a live cd (selecting "try ubuntu without any changes"), go to systrem > administration > partition editor.

delete the windows partition, expand your ubuntu partition using the free space (be patient, it will take a while!) and hey presto, you've made windows disappear.

you can also delete its entry from grub by hitting alt & f2 and entering "gksudo gedit /boot/grub/menu.lst" (once you've booted back into your own ubuntu installation)

immediately save a copy of the file as backupmenu.lst.
then scroll down to near the bottom and add a hash (#) to the start of each line of the windows entry (should be obvious, each seperate entry is in its own paragraph) and next time you boot you should be rid of windows.

if i were you, i would alos look for the section near the top for "timeout" and uncomment the last line of that section (if it is commented) and change the value to 1.  that way, ubuntu will load almost immediately without having to wait 10 seconds for a timeout (you can still bypass this by quickly hitting excape when prompted if you need to load an older kernel for whatever reason.

---

### Post by jacklinux on 2009-08-01
> **Post Monkeh said:**
> what rob said.

boot up off a live cd (selecting "try ubuntu without any changes"), go to systrem > administration > partition editor.

delete the windows partition, expand your ubuntu partition using the free space (be patient, it will take a while!) and hey presto, you've made windows disappear.

you can also delete its entry from grub by hitting alt & f2 and entering "gksudo gedit /boot/grub/menu.lst" (once you've booted back into your own ubuntu installation)

immediately save a copy of the file as backupmenu.lst.
then scroll down to near the bottom and add a hash (#) to the start of each line of the windows entry (should be obvious, each seperate entry is in its own paragraph) and next time you boot you should be rid of windows.

if i were you, i would alos look for the section near the top for "timeout" and uncomment the last line of that section (if it is commented) and change the value to 1.  that way, ubuntu will load almost immediately without having to wait 10 seconds for a timeout (you can still bypass this by quickly hitting excape when prompted if you need to load an older kernel for whatever reason.
Thankyou, will try that now and get back on how it goes.

---

### Post by Post Monkeh on 2009-08-01
> **jacklinux said:**
> Thankyou, will try that now and get back on how it goes.

just remember to back up any important data you have on your ubuntu partition! although this method shouldn't cause any damage, nothing is ever 100% guaranteed to not cause data loss.

---

