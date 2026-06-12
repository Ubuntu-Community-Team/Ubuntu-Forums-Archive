---
title: "VirtualBox install: 165 MB free space but I installed an 8 GB hard drive"
date: 2010-11-22
forum: General Help
---

### Post by just164MB on 2010-11-22
I have Win XP, 80 GB hard drive, of which 25 GB are unused. I installed the latest VirtualBox, and then I installed inside it the latest Ubuntu, version 10.10.

I selected the default 8 GB dynamic hard drive, and when it finished installing I found out I had only 165 MB free space. Selecting all folders in root and clicking properties reveals I have 320,000 items occupying 5.4 GB. Is this normal?

But there's something else going on here, because if I install another instance of Ubuntu through VirtualBox, this time selecting 3 GB or 16 GB hard drives, it always ends up telling me that I have only 165 MB free space.

I read this thread:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

In point 5. it explains how to check your drive stats, and I did that. I checked System > Administration > System Monitor: File Systems tab. The strange things that appeared in my readout were: the directory isn't /home, it's /rofs, it has 660 MB instead of the 8 GB I created when installing Ubuntu, and it's using up 100% of the disk space.

This is what VirtualBox says about my storage:
IDE Secondary Master (CD/DVD): ubuntu-10.10-desktop-i386.iso (693,16 MB)
SATA Port 0: ubuntu-in-winxp.vdi (Normal, 8,00 GB)

The folders with all the items and GB usage are proc, rofs, and usr. Their properties tab includes a note that "some content unreadable".

If I try to copy a file from a shared Win XP folder that is greater than 200 MB into Ubuntu it says there's not enough disk space.

---

