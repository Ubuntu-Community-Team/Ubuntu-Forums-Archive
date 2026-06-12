---
title: "Reactivate Grub after Windows Reinstall"
date: 2011-05-26
forum: General Help
---

### Post by jfluckey on 2011-05-26
I have (had) a dual boot system of Ubuntu (11.04) and Windows 7.  I was forced to reinstall Windows over itself and it installed its boot loader.  How do I get my Grub boot loader back?  I googled it and found instructions, but they were from 2007 so I thought it might only be for Grub Legacy.  The instructions were as follows:

Boot from a live cd
run "sudo grub" in a terminal
then, "root (hd0,0)", "setup (hd0)", and "exit"
reboot and grub should be present

While I wait for ubuntu to download so I can create a live cd, can someone confirm if this is correct for Grub 2?  Also, what commands will tell me which hard drive and partition I need to put in the above commands (hd0,0)?  I have (4) internal hard drives and boot drive has a few partitions on it.

TIA,
Juston

---

### Post by ubume2 on 2011-05-26
It sounds like you are using grub1 installation instructions.

11.04 is grub2, which is a whole different ball game.

I've used this to recover my grub2 after a windows install or have lost my grub. You will need a live cd.

[http://ubuntuforums.org/showthread.php?t=1752186](http://ubuntuforums.org/showthread.php?t=1752186)

---

### Post by oldfred on 2011-05-27
A couple of more links.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If you did install grub legacy over grub2 that can cause even more problems. Hopefully the grub2 fixes work, but if not then you will have to chroot into your system and uninstall both grub & grub2 and reinstall cleanly grub2.

---

### Post by ubume2 on 2011-05-27
> **oldfred said:**
> 

If you did install grub legacy over grub2 that can cause even more problems. Hopefully the grub2 fixes work, but if not then you will have to chroot into your system and uninstall both grub & grub2 and reinstall cleanly grub2.

You can check from the terminal
$gedit /boot/grub/menu.lst   ##if it comes up blank, close it and try
$gedit /boot/grub/grub.cfg   ## if that comes up with a lot of text in it, chances are good that grub2 was installed, and it is okay to go ahead with  url in my thread.

Did you try to install grub legacy (grub1)?  You said that you were following a post made in 2007.  At that time grub1 (legacy) was the only game in town, other than lilo, which has not been used as a grub in Ubuntu, at least since I started in Ubuntu in 2006.  Grub2 has been the standard for a couple of years.

---

### Post by jfluckey on 2011-05-31
Thanks for the responses!  It was a late night and I got it working and decided to go to sleep rather than reporting back here.  Then I forgot about it.  

I was booting from a persistent live USB so it took forevvvvvvvver to boot (>45 minutes), but that is an issue for another day.  Once I got the live version running, I followed the instructions found here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).  The instructions I had (in the OP) were for Legacy, so they would not work.  I did not install Legacy over Grub 2.  Thanks again.

---

