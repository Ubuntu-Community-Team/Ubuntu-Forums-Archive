---
title: "Easiest way to reinstall ubuntu"
date: 2010-09-27
forum: General Help
---

### Post by DerekA on 2010-09-27
I have [this]("http://ubuntuforums.org/showthread.php?t=1578709") problem and haven't been able to solve it so I figure I will just start over.

The problem is I have no idea how to do that >_> I have ubuntu (and Windows 7) dual booting from a partition.

---

### Post by andrewthomas on 2010-09-27
Did you install ubuntu from within windows?  [wubi]

---

### Post by DerekA on 2010-09-28
No, it's on a dedicated partition.

---

### Post by Ordes on 2010-09-28
if you just want to know how to reinstall than:

> load up your ubu-live
> choose install
> ubuntu should detect your win7;
  > depending on your skills you have multiple choices here; you can choose to install ubu besides win and let the installer take care of it; or you can manually arrange how to install ( which partitions etc) ubu besides win; i prefer manually cause it gives you more freedom in your setup;
  > in your case you should already have the needed partitions; to choose for manually; if you like you can just choose manually first; to see what you can setup; if you are not comfortable with it, you can always hit >>back<< and choose automatic setup
  > if you like to have a different partition setup; than i would partition my harddrive ahead; reboot; and than start the installation
> finish installation

---

### Post by DerekA on 2010-09-28
I am having trouble getting ubu live to work. The first installation I had no problem, once the boot order was changed it booted right into it fine, but now nothing comes up. Am I missing something obvious?

---

### Post by Ordes on 2010-09-28
not quite sure what u mean..

ubu-live runs from usb or cd directly and needs no installation.

> when u say, it booted in before, but the boot order changed and u have a black screen, u mean:
1. when u boot the installed ubuntu 
2. when booting the live-cd

if its 2 and the disc was working before, it might be your boot settings in bios. check if cd-rom / usb is enabled, depending from where u boot. my bios also has a hotkey ( F8 ), to bring up a seperate device-bootloader.

---

### Post by DerekA on 2010-09-28
It's #2. I don't see any setting about enabling/disabling usb, and I certainly didn't change it since I first installed ubuntu.

---

### Post by Ordes on 2010-09-28
>> did u check if u can boot from another boot-rom? e.g win. or u have any option to test-boot your live on another system?

>> i still dont understand what u mean with "first installation, once the boot order was changed it booted right into fine";

> which boot order did you change than?
  >> do u mean grub, which had been installed... but what did u boot into than? the installed one? or the live one again.. whereas booting in the installed one wouldnt mean much, as its a different boot process than when booting from rom.

> or did u change the boot order from the bios in order to boot the live? 
> is your live on a usb or cd? if usb, than the image might have get corrupted. or for some bios u need to hit a F-key in order to actually start from the usb. its also possible that the rom got corrupted, or as happened to my friend the cd-rom cable got slightly unplugged..and many other sources of cause

> but to actually understand whats going on you should write more details. its hard to follow up your explanation. and therefore cant really see where to look for the problem...

edit:
> if using usb: in bios its not always called usb, but often removable drive. some bios have 2 settings.
1 enable boot from removable drive
2 boot device priority, where rem-drive has to be on top of the others..
those 2 settings are probably not in the same sub-menu, but mostly always in the "boot" main menu

---

### Post by DerekA on 2010-09-28
> **Ordes said:**
> >>2 boot device priority, where rem-drive has to be on top of the others..
those 2 settings are probably not in the same sub-menu, but mostly always in the "boot" main menu

Ah I finally get this! This was my problem. I will go through with the reinstall later but I got to that step.

Thanks!

---

### Post by Ordes on 2010-09-28
^^ welcome... your bios probably resets the boot device order for removable drives when power-up/ restart. had the same issue with one of my friends netbooks.. so whenever u wanna start from usb u probably have to go into your bios first...

---

