---
title: "LiveCD does not detect partition table"
date: 2009-08-23
forum: General Help
---

### Post by carric on 2009-08-23
Getting bored with windows XP, yesterday I figured I would get back in touch with linux. I installed ubuntu Jaunty (v9.04) and because I gave up getting the wireless card working I thought I'd remove the installation. Because LiveCD/LiveUSB would not boot without freezing, I booted into the existing Jaunty installation and in terminal used fdisk to delete the existing installation (which I was currently booted into). After the operation had reached a certain point, iirc the system reached an error forcing me to reboot, next giving me the mising grub issue (error 22?). I fixed that with WinXP recovery console fixboot+fixmbr and got things back to the state before I installed Jaunty (or so I thought).   
When I booted the ubuntu Gutsy 7.10 (comes stock w/ support for my wireless card) LiveCD/LiveUSB, the installer && fdisk && gparted all would no longer recognize the partition table, perhaps as if there was no HD to read from. I can successfully boot WindowsXP without visible problems. Any ideas?

---

