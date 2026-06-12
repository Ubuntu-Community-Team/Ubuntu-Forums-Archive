---
title: "Windows 7 &amp; GRUB"
date: 2009-11-06
forum: General Help
---

### Post by Sanchopinky on 2009-11-06
I followed various guides and I still can't access Windows 7. It appears in the boot menu, but when I actually choose it the screen turns black and nothing shows up.

I've tried sudo-update grub and I get this:
```
drake@drake-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

I've tried various methods using Live CD and none of them work.

---

### Post by Sanchopinky on 2009-11-06
Can someone help? First only Windows 7 would boot and now only Ubuntu... How can I get Windows 7 back? I need it for work.

---

### Post by Draclvr on 2009-11-07
Wish I could help, Sanchopinski.  I installed Ubuntu 9.10 last night along-side my Windows XP Media Center edition on one my 4 hard drives.  When I start my computer, my Media Center shows up (soon to be upgraded to Windows 7), my ancient XP Home hard drive shows up as does my Windows 7 Release Candidate drive.  I can boot into whichever drive I want.  

Not sure what your setup is, but can you get into your BIOS when you boot up to change the boot order?

---

### Post by Sef on 2009-11-07
How did you partition the hard drive?

---

### Post by Sanchopinky on 2009-11-07
When Jaunty came out I did a fresh install and split it 130 gb for Ubuntu and 70 for Windows. I did it via the Ubuntu partioner. This time around I upgraded from the update manager.

---

### Post by oldfred on 2009-11-07
Because you did an upgrade you still have legacy grub and the menu.lst stanza for windows should not have changed.

To see how your system is configured, download and run this script:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Sanchopinky on 2009-11-07
[http://pastebin.org/51706](http://pastebin.org/51706)

There are the results

---

### Post by oldfred on 2009-11-07
Your install shows the partition for windows starting at 63 which is correct for XP but not Vista or Win7. Did you use gparted and not turn the round to whatever? sectors off.

From Herman's page:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Before doing anything to a modern Windows partition, make sure you remove the tick mark from the 'Round to cylinders' option in GParted.
If you forget, GParted will default to rounding the start and end points of the partition off to align it on traditional hard drive cylinder boundaries.
It won't do too much harm, but if you move Windows, probably it won't boot at first, and you'll have the extra hassle of having to fix the boot loader. Sometimes it fixes itself but requires a few reboots, other times you might you might not be so lucky,
Either way, it's best not to let GParted move the start of the partition if you can.

---

### Post by Sanchopinky on 2009-11-08
oldfred, I suspected something like that. I had to reinstall windows 7 because the mbr was all messed up. It couldn't even be recovered with the install disk. After that I uninstalled grub and reinstalled it, I followed a few guides (including Hermans) and now **everything works**.

Thanks guys!

---

