---
title: "Grub2 - alter automenu behaviour"
date: 2011-08-19
forum: General Help
---

### Post by jago25_98 on 2011-08-19
Grub2 was a bit of a shock. 

I have various kernels on my menu and Windows too. I need Windows to auto boot for anyone who turns the computer on but doesn't understand the menu, but I also need all those old kernels present because I don't want to delete them until I've tested them for a few months - kernel v3 is handy for me but I can't get Virtualbox modules working with it. 

 How can I keep those scripts for finding OS'es but get them to make a different menu order so I don't have to scroll thuogh to find the right kernel. 

 I need:

1) Windows
2) Preferred linux kernel
3) Everything else

At the moment I've managed to rearrange Windows to the top but I couldn't get kernel 2.6 (preferred kernel at the mo) to option 2. 

 ```
j@laptop:~$ ls /etc/grub.d/
00_header           10_os-prober             31_linux     README
00_header.dpkg-old  20_linux_xen             35_custom
05_debian_theme     20_memtest86+.dpkg-dist  41_custom
10_linux.dpkg-dist  30_os-prober.dpkg-dist   deactivated
j@laptop:~$ 
```

---

### Post by oldfred on 2011-08-19
What version of Ubuntu? Grub customizer does much of what you want but I understand with the new nested menus in grub 1.99 with Natty it does not work well. 
You can customize scripts or just the entries by adding them to 40_custom  or an 06_custom and turning off os-prober.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

