---
title: "Tri-Booting via WinBootMgr, but only one GRUB"
date: 2012-05-23
forum: General Help
---

### Post by rjsec4ever on 2012-05-23
I can already tell that only one GRUB is needed, but...

I am doing a tri-boot: Windows 7 on one disk, Ubuntu and kubuntu on another. I do not want a GNOME/KDE conflict in Ubuntu (especially if I ever need to remove the KDE files), so I'm doing both variants.

My second disk (the Linuxes) is on an MBR with 3 primary and 1 extended (2 logical) partitions: swap with the OSes and their respective /home's (Ubuntu on primaries, kubuntu on extended).

Installed kubuntu first, followed by Ubuntu. I know that whatever is installed most recently has priority over booting. As Ubuntu was second of the two, it boots into the Ubuntu GRUB, whenever I choose either Ubuntu or kubuntu off the Windows Boot Manager.

I have been using EasyBCD on Windows, and I know how to do the setup, just that it isn't working for me!

My Objective:
To boot onto the Windows disk and use its bootloader to boot into either Ubuntu or kubuntu on the other disk. I do not want to use os-prober or list the previous kernels in either GRUB: only normal, recovery, and memtest.

I happen to be customizing the GRUBs using Grub Customizer. To differentiate the two, I have a scheme: two animé wallpapers (one red, one white), and two different highlight colors (light red and light blue). The reds are for Ubuntu (for its Circle of Friends emblem), while the blue/white is for kubuntu (for Plasma).

---

### Post by Mark Phelps on 2012-05-23
IF what you're really after is configuring EasyBCD to do this for you,  you would do better posting your question in the NeoSmart Technologies forum in the EasyBCD Support section.  They can provide you detailed instructions there.

---

