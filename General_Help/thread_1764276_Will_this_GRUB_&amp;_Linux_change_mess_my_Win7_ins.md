---
title: "Will this GRUB &amp; Linux change mess my Win7 install?"
date: 2011-05-21
forum: General Help
---

### Post by cat2005 on 2011-05-21
Right now I have Ubuntu 9.04 on my 1st SATA hdd and Win7 on my 2nd SATA hdd.  I dual boot with GRUB legacy.

I want to replace (not upgrade, but do an actual fresh install) 9.04 to 10.10 on the 1st SATA hdd.  Of course, doing so will require I replace GRUB legacy with GRUB 2.0.

**Question:  Because I will replace GRUB legacy with GRUB 2.0, must I also fresh install Win7?**

Many thanks!

---

### Post by mcduck on 2011-05-21
No, Ubuntu won't even touch your Windows install so you don't need to reinstall it.

Ubuntu's installer will automatically replace the old Grub version with a new one, and it should also detect your existing Windows install and add it to the menu for you.

---

### Post by oldfred on 2011-05-21
No, but some suggest disconnecting the windows drive just to be sure. Which drive are you booting from. Grub2 normally installs its boot loader to sda no matter what drive you install to, so that can be an issue if what you are calling first drive is not what grub2 sees as sda.

I like to keep grub2's boot loader on the same drive as the Ubuntu install, and set BIOS to boot that drive.

If you use manual install so you can overwrite the existing partitions, then you do get the combo box on which drive's MBR to install grub2's boot loader to. All the auto installs install to sda.

While for 10.10 the procedures are otherwise similar:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Have you backed up /home or have it as a separate partition? Have you made any special settings in /etc that you may want to have copies of? Have you exported a list of installed applications from command line or synaptic to make it easy to reinstall all your favorites? This is my normal backup, but I use it for my clean installs.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

