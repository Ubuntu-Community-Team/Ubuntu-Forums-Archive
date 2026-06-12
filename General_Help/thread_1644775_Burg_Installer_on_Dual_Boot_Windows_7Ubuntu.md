---
title: "Burg Installer on Dual Boot Windows 7/Ubuntu"
date: 2010-12-13
forum: General Help
---

### Post by marley07 on 2010-12-13
So Here's the History:

I recently was introduced to the concept of the Burg Loader. After doing some research, I decided that I wanted it. After continually installing and uninstalling it because the splash screen would not come up...just the boring old text screen at startup, I installed Burg (from Synaptic Package Manager) and Burg manager (via the deb file).

Immediately after installing the two, I went into burg manager and saw that it had options for my default OS (this was previously not the case...it wouldn't even let me click for a dropdown menu). The only two things it will let me select are my Ubuntu image and the recovery version of it...but not Windows 7. 

Well, this was fine by me because I like Ubuntu as my default already. So, I restarted...and instead of doing the Burg menu or the old one...it errored out and showed the grub-recovery.

I solved this by loading my windows 7 recovery cd and fixed the bootloader and mbr.

So longer story short...I'm stuck. How in the world do I successfully set up burg without freaking my laptop out?!

By the Way: I have Ubuntu 11.04 and Windows 7 partitioned on one disk.

---

### Post by jvacek996 on 2010-12-29
Hey, I had the same problem, i had WUBIed Ubuntu on my Windows partition and all that.

Get yourself an installation CD of Ubuntu and just select thr "try" thingie.

See my solved thread over [here]("http://ubuntuforums.org/showthread.php?t=1610882")

BCBC's reply (#4) helped me out. Once again, ue the Ubuntu CD to do this, coz you won't get a terminal anywhere else, duuh.

---

