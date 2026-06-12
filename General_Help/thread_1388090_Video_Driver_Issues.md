---
title: "Video Driver Issues"
date: 2010-01-22
forum: General Help
---

### Post by ThomasTheTan on 2010-01-22
Hi,

Here's my problem:

I have an ATI 5770 GPU, and, up until a couple of days ago, I have never had any problem with the drivers (I have had to use the proprietary drivers as this card is not yet supported by the open source ones).

A couple of days ago, however, it became difficult to boot ubuntu.  My machine would run through its POST and then the screen would go black and the system would restart.  I managed to get into ubuntu by running it in safe mode (Ctrl Alt F1 wasn't working), uninstalled and reinstalled the same drivers.  Since then, ubuntu has been booting, but there is a large black margin around the edge of my screen (I would say that the picture only occupies 90% of the screen).

I have a widescreen (16:9) monitor, and, when I fiddled with the resolutions, changing to a 4:3 or 16:10 aspect ratio made the picture fill the screen again (in a stretched way, obviously).  However, when I run any 16:9 settings - even lower resolution - the margin is present.

I have the catalyst 9.12 driver.  I tried installing the hotfix, but it didn't accomplish anything (except that it added a watermark to the corner of the screen).

I don't think that this is an issue with the monitor, as there are no buttons on it to actually change the size of the picutre.

I have heard that a couple of other people have this problem, but the general consensus is that this issue comes about as a problem with Xorg 7.5.  I know that I am only running Xserver 1.6.4, but I don't know how to tell what version of Xorg I have.

As a final thought, I'm almost completely sure that this GPU is supported by the open source drivers that come with lucid.  I wouldn't feel completely comfortable running lucid (I'm pretty new to linux), but I would be willing to give it a try if people think that it would be the best solution to this problem (worst that could happen = reinstall... whatever, I don't care about doing that).

Any help would be much appreciated. 

Thanks!

---

### Post by crom.osec on 2010-01-22
have you tried dpkg-reconfigure xserver-xorg ?
See [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) for more details.

---

### Post by ThomasTheTan on 2010-01-22
I tried once; for some reason it doesn't actually do anything on this machine. 

I guess that it doesn't do anything in 9.10:
[http://ubuntuforums.org/archive/index.php/t-1306844.html](http://ubuntuforums.org/archive/index.php/t-1306844.html)

I'm about to edit my xorg.conf file to see if I can change my display size.

---

### Post by spiritech on 2010-01-22
> **crom.osec said:**
> have you tried dpkg-reconfigure xserver-xorg ?
See [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) for more details.

nothing wrong with your gpu or monitor, i had this problem aswell.
go into your ati catalyst control centre with super user privaliges

double click Display Manager, then click the option underneath should be DTV (1) or something. then go to adjusyments. at the bottom of this page says Scaling options, put this all the way up to over scan then make sure "use scaling value override" is active     should be grey not white. then click apply.

step by step below

open terminal 

   type "sudo amdcccle,
   enter your password

click

   display manager
               -  DTV(1)

   adjusments

   overscan

   use scaling value override

   APPLY!!!!!!

---

### Post by Overcast32 on 2010-01-22
I fought and fought and fought with my Radeon x1650 driver to get it to work - but it did eventually. 

Here's a wiki I found for ATI driver - perhaps it will be helpful. 

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

And make sure you keep a backup of that .CONF file - but eventually editing that was what did the trick for me (after 400 other things, lol)

---

### Post by ThomasTheTan on 2010-01-22
So... I don't think that editing the xorg.conf file really did anything to the screen.

All I did was add the line to the monitors section about displaysize:

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    DisplaySize  521 293
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"

The system boots up without a problem, but the margins are still there.  I'm pretty sure that that's the correct way to implement this (I tried once previously and things weren't pretty...), but it seems like there has been no effect.

Another thought - my bios screen has never filled the entirety of the monitor.  Do you think that this could actually be a monitor issue?  This seems odd, since everything was alright beforehand....

---

### Post by ThomasTheTan on 2010-01-22
Yeah, that xorg.conf file is a dangerous thing to mess up.  Thanks for that link, it seems really useful!

Wow, thanks guys!

The scaling thing worked!!

Thanks so much!!

---

### Post by Overcast32 on 2010-01-22
Yeah, it kicks butt when you get something working you've been on a while, enjoy :)

:popcorn:

---

