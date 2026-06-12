---
title: "ubuntu/win7/xp triple boot"
date: 2011-01-26
forum: General Help
---

### Post by mtdevans on 2011-01-26
[LEFT]Hey guys,

Just a quick one.

I have win7 and ubuntu dual booted, but i need to add xp for various reasons. Is there anything in particular I need to be aware of before going ahead, or is it literally just a case of following the xp install then re-installing grub from a live cd?

Matt
[/LEFT]

---

### Post by khamil8686 on 2011-01-26
i dont see any issues that may come up as long as you have a partition ready for the new install, just follow instructions to install and then reinstall grub! hard drives can hold up to 4 primary partitions and if you want to install a 4th os you would have to turn one partition into an extended partition (1-2-3-4 OS + 1 swap) :)

---

### Post by JC Cheloven on 2011-01-26
Reinstalling grub is the main point. 
For information please see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

