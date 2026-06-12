---
title: "Blank Screen"
date: 2010-07-01
forum: General Help
---

### Post by rysliv on 2010-07-01
[SIZE="2"]Specs
Intel Core 2 Quad Q8200 2.33Ghz
2Gb 800Mhz DDR2 Mem
Western Digital 800 80Gb Hard Drive, 7200RPM  IDE/ATA
Maxtor 160Gb Hard Drive, 7200RPM IDE/ATA
720Watt KingWinn PSU
Nvidia Geforce 9600GT  Overclocked 
Using DVI Port

Dualbooting Windows 7 and Ubuntu 10.04 Desktop
Using WUBI.exe on Windows to install, Ubuntu Installer for Windows. 

Issues
Booting into Ubuntu 10.04
Install wait 5 Seconds or press esc for information, waited 5 sec
Screen Blank, Monitor detects display
Then Screen Blanks, Monitor turns off due to no display found
Some Hard Disk activity but no display

I really don't understand why it doesn't install
iv'e reinstalled it about 5 times.

I had ubuntu installed once before, I uninstalled it due to MenuBar Issues.[/SIZE]

---

### Post by celldweller1591 on 2010-07-01
Wubi is buggy i guess. When i used it in 10.04, it asked me to download the whole 700mb iso image but i had it in my CD already ! 
Try Ubuntu dedicated install rather than Wubi, boot into livecd and select language and then press F6 and put acpi=off. It may be caused due to faulty(unsupported) hardware. And then follow this [tutorial ]("http://ubuntuforums.org/www.linoob.com/2009/04/landing-on-planet-ubuntu/")

---

### Post by bcbc on 2010-07-02
> **rysliv said:**
> [SIZE="2"]Specs
Intel Core 2 Quad Q8200 2.33Ghz
2Gb 800Mhz DDR2 Mem
Western Digital 800 80Gb Hard Drive, 7200RPM  IDE/ATA
Maxtor 160Gb Hard Drive, 7200RPM IDE/ATA
720Watt KingWinn PSU
Nvidia Geforce 9600GT  Overclocked 
Using DVI Port

Dualbooting Windows 7 and Ubuntu 10.04 Desktop
Using WUBI.exe on Windows to install, Ubuntu Installer for Windows. 

Issues
Booting into Ubuntu 10.04
Install wait 5 Seconds or press esc for information, waited 5 sec
Screen Blank, Monitor detects display
Then Screen Blanks, Monitor turns off due to no display found
Some Hard Disk activity but no display

I really don't understand why it doesn't install
iv'e reinstalled it about 5 times.

I had ubuntu installed once before, I uninstalled it due to MenuBar Issues.[/SIZE]
Press ESC when it says for more options.
Then you'll see a bunch of options.
Press 'e' on the normal option.
Look in the mess of stuff and find 'quiet splash'. Add nomodeset so it reads 'quiet splash nomodeset'.
Then CTRL-X to boot.

This is a graphics card issue. You can try it with the live CD and it'll be the same. Or install it normally. Either way. Once you're in you have to click System, Administration, Hardware Drivers to get one that supports your card.

PS if you reinstall wubi like this, then it will show you the unattended installation and reboot. You'll have to do the same to get in the second time (except editing the entry is easier - a lot cleaner looking). And I don't think you actually need to see the wubi install, but it's nice to know it's actually working I suppose.

---

### Post by rysliv on 2010-07-02
i finally got it into low video mode, so from there i updated the video drivers i checked the start logs and it couldnt find the defualt display or something, i guess this is resolved.
works now, except my WoW gives me the WoW crash reporter when i start it which sucks. idk what else to do.

---

