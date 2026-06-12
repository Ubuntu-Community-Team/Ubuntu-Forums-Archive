---
title: "Live USB Doesn't works"
date: 2012-08-22
forum: General Help
---

### Post by sergi70 on 2012-08-22
Hi guys! I'm having some troubles with a Live USB With Ubuntu 12.04. It works in all computers except the personal mine. It just doesn't start loading, and only shows that:
[IMG]http://desmond.imageshack.us/Himg687/scaled.php?server=687&filename=foto0143kv.jpg&res=landing[/IMG]
My Specs are:
i5 2400
MOBO ASUS P8H67-M LE
4 Gb RAM DDR3
GTX550 Ti
Nox 620W
Grundig Vision 7 TV 22" FULL HD
What can you tell me about this? Thx! It has UEFI and EFI, can that be the problem?

---

### Post by efflandt on 2012-08-22
For 12.04 live/install iso you have to use **nomodeset** boot parameter for nvidia. Hit any key when symbols appear at bottom of first screen, and after selecting your language use F6 and spacebar to X nomodeset.

Once Ubuntu 12.04 is installed, you should not need that parameter.

I don't have a PC with UEFI or EFI, so can't answer anything about that.

---

### Post by sergi70 on 2012-08-22
> **efflandt said:**
> For 12.04 live/install iso you have to use **nomodeset** boot parameter for nvidia. Hit any key when symbols appear at bottom of first screen, and after selecting your language use F6 and spacebar to X nomodeset.

Once Ubuntu 12.04 is installed, you should not need that parameter.

I don't have a PC with UEFI or EFI, so can't answer anything about that.
Thx, but I only use it as an external OS in a pen, I don't wont to install.

---

### Post by oldfred on 2012-08-22
You still need the nomodeset for nVidia. But if using flash drive you can add it to the file on the flash drive like this that was for Intel:

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit “syslinux.cfg”

If you have UEFI and the 64bit version, you should have two options to boot. One is the old BIOS and the other the newer UEFI. If just booting it should not matter, but which every way you boot is the way it will install.

---

### Post by sergi70 on 2012-08-22
How can I exactly do this? I'm a C programer, but i always had windows and I only know the easy terminal comands (sudo, su, etc).

---

### Post by C.S.Cameron on 2012-08-22
> **sergi70 said:**
> How can I exactly do this? I'm a C programer, but i always had windows and I only know the easy terminal comands (sudo, su, etc).

Plug the drive into a computer running linux, open isolinux folder, open txt.cfg with Text Editor and add " nomodeset" after the first "quiet splash --"

Edit:
Then save

---

### Post by sergi70 on 2012-09-01
Thx you so much, but I have a problem with the image. I don't have nvidia drivers installed so the max resolution i can use is 1024x768 and my TV uses native 1920x1080. So, should I install the drivers normaly, or I should do another thing?

---

### Post by oldfred on 2012-09-01
You have to download the nVidia driver and restart without rebooting.

to test, install Nvidia driver while in the liveCD environment. Do not restart entire system but gdm, lightdm, xdm, etc 
press ctrl+alt+f1.
sudo start lightdm
Ubuntu 11.10 and later uses lightdm in place of gdm in earlier versions. So the command would be 'sudo service lightdm restart'

or: gdm, lightdm, xdm, etc 

But if just a liveCD you have to download every time and reinstall every time. I think with persistence you can save download, but still will have to reinstall every time you reboot.

If a larger flash drive you can just do a full install of Ubuntu.
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

