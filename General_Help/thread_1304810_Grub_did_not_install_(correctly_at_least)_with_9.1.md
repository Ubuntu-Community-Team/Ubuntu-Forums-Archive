---
title: "Grub did not install (correctly at least) with 9.10"
date: 2009-10-29
forum: General Help
---

### Post by shador on 2009-10-29
Just finished my Karmic install and all I can do is boot straight to Windows 7 wich is the other OS I have installed. I get no grub menu to choose wich OS to boot. 

Both Win7 and Karmic are installed on the same HDD, before installing Karmic i freed up diskspace so I chose the automatic install (use first free space to install or something like that)

I googled on how to install grub from liveCD but none of the tutorials seem to work for me. Anyone knows my options from here on? I really would like to get into Karmic today.

---

### Post by P4man on 2009-10-29
I can only imagine you have more than 1 harddisk and grub installed on the wrong one. Ive seen that happen when you have both sata and pata drives, the bios boot order seems to be interpreted differently by grub.

If you have more than one drive, disconnect all drives except the one with ubuntu (and windows). Then run any of the reinstall grub how-to's with a livecd. However make sure you follow one for grub**2** as that is the new default in karmic.

---

### Post by philinux on 2009-10-29
> **shador said:**
> Just finished my Karmic install and all I can do is boot straight to Windows 7 wich is the other OS I have installed. I get no grub menu to choose wich OS to boot. 

Both Win7 and Karmic are installed on the same HDD, before installing Karmic i freed up diskspace so I chose the automatic install (use first free space to install or something like that)

I googled on how to install grub from liveCD but none of the tutorials seem to work for me. Anyone knows my options from here on? I really would like to get into Karmic today.


Did you watch the install? 

Did you use the advanced option and install grub to a partition? 

Did you see it saying install grub?

---

### Post by shador on 2009-10-29
Umm a few reboots later and a really unsucessful repair of the windows 7 boot files and Grub is up and running by some reason. This seems like it's gonna be a problem free install :/ 

Well I guess this solved itself, thanks though for the replies.

---

### Post by philinux on 2009-10-29
Make a note of the grub2 link in my sig.

---

### Post by P4man on 2009-10-29
> **shador said:**
> Umm a few reboots later and a really unsucessful repair of the windows 7 boot files and Grub is up and running by some reason.

Wild guess: the windows bootloader got shot by your attempts to fix this, therefore the BIOS was unable to boot from harddrive X (which had windows bootload) and therefore tries booting Y, on which you installed grub from the beginning.

Should that wild guess be correct then just keep in mind your booting may depend on that second drive being there (until you fix it properly) as well as on windows bootloader being .. shot.

Anyway have fun with 9.10 :)

---

