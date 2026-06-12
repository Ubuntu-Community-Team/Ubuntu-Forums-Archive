---
title: "triple boot problem"
date: 2009-12-18
forum: General Help
---

### Post by jakebot on 2009-12-18
hello i recently installed Windows 7 and decided to install Ubuntu 9.04 and give it a try. Yesterday i needed XP on my computer so i installed it (not knowing i could run in XP mode so technically i already had it on there.) so i suppose i have XP on there twice now. I am unable to choose Windows 7 or Ubuntu with GRUB and now all i can do is choose the 2 Xp installs. How do i get it back to the way it was before? (i already deleted the partition that had the nex XP install on it) PLEASE HELP!!!

---

### Post by amsterdamharu on 2009-12-18
I guess when you install xp it writes over grub and now you don't have a grub menu at all untill you install grub again. you can try grub4dos, install that to boot into Ubuntu and restore grub. Add an entry for the new winxp in your menu.lst or grub.conf (in /boot/grub/.

I hope this makes sense if it doesn't I will be happy to clarify.
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)[FONT=monospace][/FONT]

---

### Post by amsterdamharu on 2009-12-18
To clarify, I don't think you have to install grub4dos just make sure something like this is in your boot.ini
[boot loader] 
timeout=3 0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
C:\grldr="Start GRUB4DOS"

This is what my boot.ini looks like and it'll give you a menu to choose from the only line you add is the last one so you have grub4dos in your startup menu. What you need if you don't already have it is the timeout the default (for your xp not the one shown here) and the [operating systems] or it won't show menus. Make  a backup copy of boot.ini before editing it.

copy grldr and menu.lst to c:\

When you boot and choose grub4dos you should get a new menu 
in this menu press c for command line and type
find /boot/vmlinuz-2
don't press enter but press tab to see what kernel you have. If I know what 
version of ubuntu you have we can figure out what to put in menu.lst on c:\
to start ubuntu in recovery and install grub again.

---

