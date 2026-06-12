---
title: "Updating tips to Lucid from Karmic"
date: 2010-06-29
forum: General Help
---

### Post by shantiq on 2010-06-29
[FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

I upgraded from karmic 2 weeks ago and encountered 2 serious drawbacks

I want to share these here as they may be of use to others[/COLOR][/SIZE][/FONT] [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

Number 1 ( and this was so major that i scuttled back to karmic for a while )   was THAT NONE of my discdrives usb sockets or external drives were picked up[/COLOR][/SIZE][/FONT] [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

Many solutions were suggested but the one which made the difference was to DISABLE the floppy drive in the Bios[/COLOR][/SIZE][/FONT] [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

F8 or F11 then disable it and reload before you install Lucid[/COLOR][/SIZE][/FONT] [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

I do not even have a floppy simply the space for it on my system[/COLOR][/SIZE][/FONT] [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

======================================

the second issue was the desktop freeze which happened irregularly but was annoying.   i have read that for some it was really bad. [/COLOR][/SIZE][/FONT]   [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]


I was presented with many suggestions but again only one seemed important and that was the kernel [/COLOR][/SIZE][/FONT]  [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]issue 


from 2.6.32 the standard issue with Lucid to 2.6.34 the standard issue for Maverick[/COLOR][/SIZE][/FONT] [FONT=Century Gothic][SIZE=3][COLOR=DarkRed]

The way to update is thus[/COLOR][/SIZE][/FONT] [FONT=Arial Black][COLOR=DarkRed]



[/COLOR][/FONT]  





[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][SIZE=3][COLOR=DarkRed]**[Linux Kernel 2.6.34 installation guide for Ubuntu Linux 10.04]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/") **[/COLOR][/SIZE]

Published on 19 May, 2010 in [Linux]("http://www.ramoonus.nl/category/projects/linux-projects/"). [19 Comments]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/#comments") Tags: [Linux]("http://www.ramoonus.nl/tag/linux/"), [nVIDIA]("http://www.ramoonus.nl/tag/nvidia/"), [Ubuntu]("http://www.ramoonus.nl/tag/ubuntu/"). 

This short walkthrough describes how to get the latest linux kernel working under Ubuntu Linux without having to compile it yourself.
This tutorial should work with the latest version of Ubuntu Linux (10.04 ) and all distributions based on these versions of Ubuntu Linux like Mint.
The included kernel files have been compiled using the generic ubuntu configuration. 
**Note:** nVIDIA ForceWare drivers are automatically installed using DKMS
**Installation Guide**

[LIST=1]
[*]Download [linux-headers-2.6.34-020634_2.6.34-020634_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb")
[*]Download your kernel headers package;
I386: [linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb")
AMD64: [linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
[*]Download your kernel compile;
I386: [linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb")
AMD64: [linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb")
[*]Install the files in the same order (else it won`t work!)
[*]In the terminal run:
sudo update-grub
[*]Reboot and select the kernel from the bootloader menu
[/LIST]
[FONT=Comic Sans MS][COLOR=DarkRed]

**I hope both these tips  will help others**[/COLOR][/FONT]
 [/FONT][/FONT][/COLOR]

---

