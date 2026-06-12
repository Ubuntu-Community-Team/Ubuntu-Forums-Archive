---
title: "Trouble installing on a Compaq Presario 916US"
date: 2012-01-18
forum: General Help
---

### Post by leenewman8899 on 2012-01-18
I have a Compaq Presario 916US with 1GB Ram.  It has a CD/DVD read/write drive and a 30 GB HD.  I know the CD/DVD works as I have used it for other software and as a player, but when I load XUBUNTU and reboot, nothing happens.  The BIOS are set to boot from the CD>DVDdrive, yet I get nothing.  I had XP installed on it and tried to live CD it, I tried to WUBI it, to no avail.  The USB is a 1.0 and there is no way to boot from it.  I've played with Ubuntu products for 2 years and have never had any trouble until now.  I'm stumped!  Any suggestions?

---

### Post by dino99 on 2012-01-18
dont know how you get that cd, but always burn it at the slowest speed

[http://tuxarena.blogspot.com/2009/03/4-ways-to-create-cddvd-iso-images-in.html](http://tuxarena.blogspot.com/2009/03/4-ways-to-create-cddvd-iso-images-in.html)

and sometimes with some hardware, special setting(s) is needed to boot:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mastablasta on 2012-01-18
> **leenewman8899 said:**
> The USB is a 1.0 and there is no way to boot from it. 
 
 
i think mine is older/weaker (731EA or something like that). if nothing shows up (not even GRUB) it could be a GPU issue. If grub shows up try to use the boot options.
 
anyway to boot from USB you can use PLOP boot manager. i had a floppy lying arround and installed it to that, but you could just as well use CD or hard disk for it. then i boot from floppy and select USB...
[http://www.plop.at/en/bootmanager.htm](http://www.plop.at/en/bootmanager.htm)
 
How much RAM you have? I have 256 with graphics card taking 32 MB. So i landed with Chrunchbang XFCE (based on debian stable). works ok.

---

