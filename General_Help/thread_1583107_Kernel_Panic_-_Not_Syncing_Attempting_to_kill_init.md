---
title: "Kernel Panic - Not Syncing Attempting to kill init!"
date: 2010-09-27
forum: General Help
---

### Post by JCollierDavis on 2010-09-27
I'm getting Kernel Panic errors on a new install on a new machine. It works fine with the Live USB, but not from a regular install. I thought it may have been a hardware issue.  From my limited understanding, everything seems ok.

Any suggestions on how I can figure this out?

I recently built a computer and while I was waiting on my OEM copy of Win7 (going to dual boot) I tested my new machine with a Ubuntu Desktop 10.04 Live USB.  It worked just fine off the USB so I went ahead with an install.  I selected the basic install and used ext4.  Instead of rebooting to the OS, I simply got a Kernel Panic message.  After some research and determining it could be a hardware problem, I rebooted off the USB. It again worked fine.  I was unable to mount some of the HDD partitions so I re-installed again, this time with ext3.  It booted to the OS just fine so I ran the system update which took quite a while.  After the next reboot, I got the Kernel Panic again. I used a different Live USB (64bit Alternate Installer) and ran Memtest86+ for about 2 hours.  Everything came up 100% then.

Here's my hardware:

MoBo: Asus M4A88T-M
RAM: F3-10666CL9D-4GBRL
CPU: AMD Athlon II X4 635
HDD: Western Digital Caviar Blue WD10EALS 1TB

All the RAM settings in BIOS are set to [Auto] right now.


dmesg didn't look like there were any errors.

---

### Post by andrewthomas on 2010-09-27
I would start off by reinstalling grub2.  

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

