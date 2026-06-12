---
title: "Black Screen on Start Up and Problem with Reinstalling"
date: 2011-05-15
forum: General Help
---

### Post by SilverDragon on 2011-05-15
To start this is on my mom's laptop which is a Gateway NV78.

It was running fine with Ubuntu 10.10 but I like to do a clean install of the latest version when it comes out and I am home. I torrent the 11.04 desktop 64 bit releaee and strangely the screen is just black but it appears to load. Then I try to the 64 bit alternate install which appears to work fine. Unfortunately, the screen is black when loading past GRUB and plays the Ubuntu sound. To test if it is loading I type in my password and hit enter and the Ubuntu log in sound plays but still nothing on the screen.

I thought no big deal I will just install 10.04.2 and use the alternate download. I download it on the desktop running Windows 7 and use the USB installer the Ubuntu website recommends. It installs fine but the same problem occurs with a black screen.

At this point I think to reinstall again but this appears at the top of the screen.

SYSLINUX 3.86 20-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al

The screen is just stuck there with a blinking cursor and if press any keys it beeps several times.


TL;DR Installed 11.04 then black screen. Installed 10.04.2 then black screen. Install 10.04.02 again and error message.

---

### Post by SilverDragon on 2011-05-17
Well I installed Windows 7 through the same flash drive and it worked and when I tried to reinstall any version of Ubuntu (10.04.2, 10.10, or 11.04) they all just load up to a blank screen now. I guess I'll just leave it on Windows for now and try again when 11.10 or 12.04 comes out.

---

### Post by scottstensland on 2011-05-17
hold down F6 just after the grub screen to
force the ubuntu menu and pick various
combinations of the disable options until
your X will load - my machine had same symptoms
and had to use

pci=noacpi

my 10.04 worked fine only 11.04 needed this boot mod

good luck - Scott Stensland

PS - there are loads of similar 11.04 boot up blank screen discussions here so poke about

---

### Post by SilverDragon on 2011-05-18
Thank you for your suggestion. I remember having to do that a long time ago. Probably around Ubuntu 8.10. I'll try that when the next version comes out if there are still issues. My family wants to me to leave the laptop the way it is for now.

---

