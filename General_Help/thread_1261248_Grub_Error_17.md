---
title: "Grub Error 17"
date: 2009-09-08
forum: General Help
---

### Post by joec369 on 2009-09-08
I have an Acer Aspire One Netbooks, with Ubuntu Netbook Remix and Windows XP dual booted.  Both worked fine at first.  I went to shrink the XP partion (while in windows) and the Partition manager needed to reboot.  On reboot is when I got the Error 17.

I have been reading around on the forums and it seems that Error 17 means that Grub can't see the hard drive or partitions.

** Also I booted the netbook up with a Windows XP Recovery CD to try and re-install XP and XP Setup also could not see the hard drive.  Did I break my hard drive with the Partition Manager?

Any help would be greatly appreciated.

---

### Post by joec369 on 2009-09-08
LOL, I guess no one has a quick idea :(

---

### Post by rob-ward on 2009-09-08
If you boot into ubuntu using a livecd(assuming you have an external reader) or with a usb pen you can check your HDD is still working, the likely problem is that grub has got a bit trashed, i ran into a similar problem a while ago. I used this tutorials info to get grub working again

[http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)

Have a look and see if that helps you at all.

---

### Post by joec369 on 2009-09-08
This Worked like a charm:

Command line
1.Boot your computer up with Ubuntu CD 2.Open a terminal window or switch to a tty. 3.Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary. 
4.Type "grub" 5.Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines. 6.Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu. 7.Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition. 8.Quit grub by typing "quit". 9.Reboot and remove the bootable CD.

---

