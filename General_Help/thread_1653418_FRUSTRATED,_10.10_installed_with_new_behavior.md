---
title: "FRUSTRATED, 10.10 installed with new behavior"
date: 2010-12-26
forum: General Help
---

### Post by tehno 2 on 2010-12-26
Due to crash of 10.04 grub, I installed it again from a live CD on D drive "C drive has windows 7" , then immediately after install, I upgraded to 10.10 64 bit. Works nicer but with strange behavior. 
Can some one answer my questions about it??

[COLOR="DarkRed"]- Need to change the boot to Windows loader and not directly to Ubuntu as it happens now. I see "windows loader as an alternative option" and it works when I select it. 
[/COLOR]
- [COLOR="Blue"]when I boot to windows, my computer icon reads only one file on D drive "bootsqm.dat"[/COLOR]

[COLOR="Blue"][COLOR="SeaGreen"]- from Ubuntu computer option, I can access all windows files.[/COLOR]
[/COLOR]
Can someone kindly help me to fix those issues

merry Christmas and happy new year to all

---

### Post by Quackers on 2010-12-26
When booted into Ubuntu open up a terminal and run ```
sudo update-grub
```
then watch the screen to se if Windows loader is picked up.

If you are still having other problems please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mikewhatever on 2010-12-27
> **tehno 2 said:**
> 
[COLOR="DarkRed"]- Need to change the boot to Windows loader and not directly to Ubuntu as it happens now. I see "windows loader as an alternative option" and it works when I select it. 
[/COLOR]

Install startupmanager from the repositories. It lets you choose the default OS to boot.
>  
- [COLOR="Blue"]when I boot to windows, my computer icon reads only one file on D drive "bootsqm.dat"[/COLOR]

Icons reading files on drives? Oh well, whatever, it's in Windows.
What filesystem is on that drive? By default, Windows can't see non-Windows filesystems.

> [COLOR="Blue"][COLOR="SeaGreen"]- from Ubuntu computer option, I can access all windows files.[/COLOR]
[/COLOR]

Not sure what needs fixing here. Ubuntu has full access to ntfs filesystem. If you don't want Ubuntu to access Windows files, don't mount the partition.

---

### Post by tehno 2 on 2010-12-27
Thanks to both of you, the installation of startupmangaer solved the issue

---

