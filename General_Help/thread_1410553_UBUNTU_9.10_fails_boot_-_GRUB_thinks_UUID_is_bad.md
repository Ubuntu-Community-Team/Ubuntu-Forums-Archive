---
title: "UBUNTU 9.10 fails boot - GRUB thinks UUID is bad"
date: 2010-02-18
forum: General Help
---

### Post by fgluck on 2010-02-18
Whammo! I just spent three hours figuring out how to get around an error that was preventing 9.10 from booting. 

This system has been working fine since it was upgraded a month ago. I have made no changes and all of a sudden, the boot was failing and I was being dropped into a shell where I could enter GRUB commands.

Turns out that the problem was that the UUIDs specified in the GRUB boot file (/mnt/boot/grub/menu.lst) were not matching what was on my boot disk. Why?? I have no idea. (I am not even sure why UUIDs are important??)

The way I fixed it was to boot off of the Ubuntu distribution disk and edit the menu.1st file to remove all references to the UUIDs.

Folks and Ubuntu lovers... this is one NASTY bug. I sure would like to understand better how to prevent this from happening again. I anticipate that the next time I upgrade, the menu.lst file will get overwritten and I will be right back where I started from.

Bugs like this don't make Ubuntu very "user friendly"!

---

### Post by n0dix on 2010-02-18
i don't have this problem yet.

---

### Post by plucky on 2010-02-19
> **fgluck said:**
> Whammo! I just spent three hours figuring out how to get around an error that was preventing 9.10 from booting. 

This system has been working fine since it was upgraded a month ago. I have made no changes and all of a sudden, the boot was failing and I was being dropped into a shell where I could enter GRUB commands.

Turns out that the problem was that the UUIDs specified in the GRUB boot file (/mnt/boot/grub/menu.lst) were not matching what was on my boot disk. Why?? I have no idea. (I am not even sure why UUIDs are important??)

The way I fixed it was to boot off of the Ubuntu distribution disk and edit the menu.1st file to remove all references to the UUIDs.

Folks and Ubuntu lovers... this is one NASTY bug. I sure would like to understand better how to prevent this from happening again. I anticipate that the next time I upgrade, the menu.lst file will get overwritten and I will be right back where I started from.

Bugs like this don't make Ubuntu very "user friendly"!

This is not a bug.

You have to use the Ubuntu Live CD to retore the Grub boot loader.

 See this [Tutorial](http://ubuntuforums.org/showthread.php?t=1014708&highlight=restore+grub) and many others in the "Tutorials and Tips" section.

Takes time to learn these things.

Good Luck

---

