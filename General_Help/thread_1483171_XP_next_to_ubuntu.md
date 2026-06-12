---
title: "XP next to ubuntu"
date: 2010-05-14
forum: General Help
---

### Post by BadboyXD on 2010-05-14
[COLOR="Blue"]I have ubuntu installed on my laptop, v9.10. I will update that, but what I wanted to know is how to install windows xp now, like next to ubuntu. So at the start, when I boot up my comp, it asks me which one I want to boot into. Not a dual boot, I want to be booted into 1 OS at a time. Cause my laptop is really old and doesn't have enough ram for a dualboot. I know there's a way to do this when you had windows as our first OS you can choose to install ubuntu along side so it asks at boot which os you want to boot into, but I had ubuntu as first OS so Im not sure on how to install windows next to it now. Anyone know what to do here?[/COLOR]

---

### Post by dino99 on 2010-05-14
if you want to install windoz, you have to know that it work IF its bootloader can be installed on the first 1024 bytes only.

but instead installing it, why not give a try to wine : [http://www.winehq.org/](http://www.winehq.org/)

most of the windoz apps work smootly with wine installed

---

### Post by obscurant1st on 2010-05-14
I think what you need is a dual boot. in Dualboot you can only boot into one OS at a time. It will ask you which os to boot into.
Now how to do it, 
Just create an ntfs partition with not less than 10GB. And Install winXp normally.
After that boot using live CD of ubuntu 9.10 and do the things said in this link:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

For more info on this search for Dualboot winxp and ubuntu

---

### Post by j0eb0b on 2010-05-14
I think if you  already have Ubuntu installed on your laptop and you do a clean install of XP into an NTFS partition, Windows will modify the MBR to make itself the default OS.  You should still get the option to boot into Linux but if you don't select it up will come XP.  You may want to burn a copy of Super Grub to a CD in case things get messed up or you want to make changes to the MBR.

---

### Post by Objekt on 2010-05-14
> **BadboyXD said:**
> [COLOR="Blue"]I have ubuntu installed on my laptop, v9.10. I will update that, but what I wanted to know is how to install windows xp now, like next to ubuntu. So at the start, when I boot up my comp, it asks me which one I want to boot into. Not a dual boot, I want to be booted into 1 OS at a time. Cause **my laptop is really old and doesn't have enough ram for a dualboot.** I know there's a way to do this when you had windows as our first OS you can choose to install ubuntu along side so it asks at boot which os you want to boot into, but I had ubuntu as first OS so Im not sure on how to install windows next to it now. Anyone know what to do here?[/COLOR]

RAM has nothing to do with dual-booting.  The size of your hard drive does matter, but is probably sufficient.  Unless the hard drive is really small, like under 20 GB, you should be able to fit both Ubuntu 9.10 and Windows XP on it.

Officially ([https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")) you only need 5 GB disk space to install Ubuntu.  I would suggest twice that, just to make sure you have plenty of room for data files, etc.

To get dual-boot set up, you could do one of two things:

Easy but time-consuming: 
1) Install Windows XP, using the entire hard drive.  This will wipe out your existing Ubuntu install, so back up any important files first.
2) Install Ubuntu 9.10.  It should automatically offer to install itself alongside Windows.  It will resize your Windows install, put itself on the remaining space, and you will get a choice of which OS to start at the next reboot.

More difficult but faster:
1) Boot the Ubuntu Live CD.  
2) Use Gparted to free up about 10 GB on your hard drive.
3) Install Windows XP on that 10 GB you just freed up.
4) Boot the Ubuntu Live CD again.  Reinstall GRUB2 on your hard drive using the command line (details in the link in post #3, above).
5) Now you get a choice of which OS to boot when you start the computer.

Feel free to ask for more details, or use Google.  There are a lot of pages showing how to reinstall GRUB2, for example.  If you're somewhat comfortable with the command line, it's not too difficult.

---

### Post by pqwoerituytrueiwoq on 2010-05-14
@Objekt
even 20 gigs should be fine for xp and ubuntu
for a fixed storage in virtual box it says 8 for ubuntu and 10 for xp recommended settings 
as long as you dont need sever multi gig applications and have a lot of video files and mp3 files

---

### Post by cascade9 on 2010-05-14
> **Objekt said:**
> Easy but time-consuming: 
1) Install Windows XP, using the entire hard drive.  This will wipe out your existing Ubuntu install, so back up any important files first.
2) Install Ubuntu 9.10.  It should automatically offer to install itself alongside Windows.  It will resize your Windows install, put itself on the remaining space, and you will get a choice of which OS to start at the next reboot.


Its almost as easy, and faster, to use the winXP parition tool to make a 10GB partition (hit 'c' for 'create partition' when you would normally just use the whole drive. 

That way, you have have to waste all that time while XP formats the whole drive.

---

### Post by BadboyXD on 2010-05-18
[COLOR="Blue"]I think Im going to give wine a try like dino99 sugested. Thanks for all the advice guys. Sorry it took me so long to get back, don't have net sometimes, bad provider.[/COLOR]

---

