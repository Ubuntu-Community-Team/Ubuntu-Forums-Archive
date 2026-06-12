---
title: "Dual Booted with Windows 7 from a USB stick WIndows is dependent on the USB to boot"
date: 2011-01-19
forum: General Help
---

### Post by ledd on 2011-01-19
I recently moved and didnt have internet. Out of a fit of boredom i  decided to get me Ubuntu 10.10 disk and dual boot. My laptop has a SD  slot in the front of it that has never been used so i decided that itd  be cool to have ubuntu on an SD card that i could boot any time. I used  the default installer to install it onto the SD card instead of using  the Universal USB Installer (i imagine this is where i went wrong). It  installed and everything works fine and when i boot up it lets me choose  between Linux and Windows when the SD card is inserted. When it is not i  get this screen [http://imgur.com/gg63v]("http://imgur.com/gg63v.").  The only really problem is me worrying that the sd card will be lossed  or get broke and i will no longer be able to access Windows. Is there anyway i can set the windows boot loader back t the default bootloader (i think this is what need to be done i may be completely wrong>

---

### Post by lithopsian on 2011-01-19
Is Grub on the SD?  I can't see the image so I'm kind of guessing.

---

### Post by Quackers on 2011-01-19
As lithopsian said, it is likely that grub has been installed to the sd card.
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by garvinrick4 on 2011-01-19
With sd card removed If you have your Windows cd reinstall windows boot manager to internal drive: Easy to do follow this guide:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

If you do not have your windows cd use this in Ubuntu install cd using TRY UBUNTU.
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda
```
will say errors ignore we only need mbr part.

---

