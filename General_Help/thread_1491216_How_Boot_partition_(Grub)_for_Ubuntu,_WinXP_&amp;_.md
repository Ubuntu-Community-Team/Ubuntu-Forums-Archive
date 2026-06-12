---
title: "How: Boot partition (Grub?) for Ubuntu, WinXP &amp; Win&amp; ?"
date: 2010-05-23
forum: General Help
---

### Post by polarbar on 2010-05-23
Hi,
I would like to have a boot partition with Grub and be able to load Ubuntu, Windows XP and Windows 7....  Is there someone who knows how to create that?  I need complete details...O:)

---

### Post by oldfred on 2010-05-23
You do not have to have a boot partition, that really is for Ubuntu only. I have a grub partition just for older systems that still have grub legacy. It really is grub that controls what systems to show.

Grub2 will give you all the options to choose which system to boot, but windows will not. 

The normal windows install combines its boot into the first install and the second install will not boot on its own. Grub then cannot boot the second install.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by polarbar on 2010-05-23
Hi oldfred,

I will read your links.  Nice stuff.

The reason for the boot partition is to protect Grub in case of a failure of one of the OS.  If it is useless to create a boot partition what can I do to protect Grug against failure?

---

### Post by oldfred on 2010-05-24
What failure to grub are you concerned about. You have to have a boot loader in the MBR and that always can be a issue since other software may corrupt the MBR. I keep several liveCDs, a USB with several rescue ISOs as emergeny ways to boot & repair system. I have 3 drives and a different grub in each. But I never have had a real problem, worst case I had to reinstall grub to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by polarbar on 2010-05-27
Thanks for all oldfred.:-D

I studied the given links and it works!  8)

---

