---
title: "Karmic Koala 9.10 + Radeon Xpress 200M"
date: 2009-10-30
forum: General Help
---

### Post by Veritas06 on 2009-10-30
First, i'm sorry for flooding the forums with another Karmic problem, but I cannot use my computer, I am posting this from my phone.  After what I believed to be a successful upgrade from 9.04 on a 64bit machine.  After a reboot, I was given a commamd prompt, but no GUI at all.  Tried rebooting & same thing. I installed ubuntu-desktop, rebooted & still just a command prompt.  I tried "startx" & that's when I saw a message about bad radeon drivers.  The next time i'm at the computer i'll write it down & post it.  

Have any other Radeon users had issues?

~Thanks for your help.

---

### Post by ublintu on 2009-10-31
I had the same problem, when I just upgraded. I solved this with a clean inslatt from DVD. Now I try to install ati 200m....

---

### Post by SkillenUK on 2009-11-03
When I select to boot Ubuntu from the GRUB screen I just get a white flashing cursor, not even the command prompt (after a clean install). I have not managed to resolve this yet but I think they really need to think about legacy graphics card support. Especially for popular brands like ATI. I was totally converted to Ubuntu as an operating system, now I'm thinking about going back to Windows because if I'm having trouble in 9.10 then what will happen in the next version and so on.

I can just about get Ubuntu working if I upgrade from 9.04 but it's a mess to be honest, the upgrade doesn't even finish properly (because of the graphics issues). I would love to find out how I can fix this because I really don't want to go back to Windows!

---

### Post by gwpritch on 2009-11-03
To be honest, this is the first time I have ever gotten this XPress 200M card to work without any fiddling.
I originally did a clean install of 9.10rc and then upgraded. The gui even came up with 3D acceleration enabled which is a first. Go figure.

---

### Post by Veritas06 on 2009-11-03
Unfortunately I never got mine working.  I used my 9.04 Live CD to copy all my data off the internal drive, then did a fresh install from a 9.10 dic I made.  No problems since.

~Sorry I can't help out others that are having the same problem.

---

### Post by ublintu on 2009-11-04
Hi gwpritch,

"The gui even came up with 3D acceleration enabled which is a first." How is this possible? how did you do that?
I installed open source driver, compiz is working, but in my hardware drivers list I can`t see it. In 9.04 it was empty, but now, in karmic I can see just Broadcom wireless. Better than before....

---

### Post by gwpritch on 2009-11-05
If compiz is working then 3D acceleration is ie. your driver is working. It doesn't show up in my restricted driver's menu either.

---

### Post by gwpritch on 2009-11-06
Crap! I should have left well enough alone. I wasn't happy with the speed my system was running at so I decided to do a minimum command line install then build from there.  Guess what...now I can't get the bleeping card to work. Tried Envy tried newest proprietary driver from amd tried repo drivers...nothing!
It does however work with the live CD.

---

### Post by ublintu on 2009-11-06
Thank you 4 the answer. I thought I did something wrongly, but no. This is the maximum, what we can have with an "old" ati card (at the moment).

---

### Post by punkcho on 2009-11-11
what if I can't even set the visual effects to normal?
i guess that ATI is not providing drivers for linux anymore ha?

---

### Post by ublintu on 2009-11-11
Ati dropped the support for the older cards like our, but...
Open source driver is working 4 me in karmic. _[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)_[]("https://help.ubuntu.com/community/RadeonDriver")  (I did just until "configure X.org". I didn`t configure X.org and I did not do below it, because I did not really understand how to do it, but the effects, copiz is working. Is it necessary?)

---

### Post by The Beej on 2009-12-21
Hi guys!

I need some help with the 200M drivers.  I've tried a bunch of solutions but I end up with horrible ghosting and messed up displays.  (see picture [http://docs.google.com/View?id=dds2z3zs_53jmmvb9hc](http://docs.google.com/View?id=dds2z3zs_53jmmvb9hc))

Is there any surefire way to install drivers on Karmic that rids me of the ghosting?  I've tried different refresh rates, different resolutions, keeping a solid color background, nearly everything to do with the graphics on here to no avail.

I seek the assistance of the Knights of Ubuntu!

Thank you!!!!!!!!

---

### Post by jlweyland123 on 2010-02-12
Yea, guys I am new to Ubuntu my self; however, I had 8.04 on my DV8000 HP laptop and every thing worked. I went to the 9.10 and I have had trouble with both my wireless driver, that one I fixed, and my ATI Radeon Xpress 200m graphics card. The graphics card is still not working, and from what I can tell no one has found a real fix to that one. The strange thing is that the card was working like a charm when I first installed the 9.10 OS then I did the auto updates and it went down. I have tried a lot of things and none of them have worked. 

So I'm going to try going back to Ubuntu 8.10 and see if I have better luck with it. Has any one tried that? God I hope I don't have any trouble with that one, and if I'm about to walk in to a pile of dodo please tell me. However, it sucks man this 9.10 really looks awesome, and I would have loved to fix it and get it going. I just don't know if it can be done. 

Any advice would be very very cool guys.

---

### Post by gwoodruff on 2010-02-18
This is what worked when the updates to Karmic broke my ATI Radeon Express 200m graphics

```
  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

reboot or restart x and you should be good2go.

---

### Post by jmhkk on 2010-02-18
I'm very new at this, but I've also noticed Karmic is doing some wonky things with the Radeon Xpress 200M (running on an AMD Turion64, 1.8MHz Compaq Presario V2000 laptop). Mine looked like it was working fine, but closer analysis showed it wasn't running full speed, and not all the options could be activated. For example: I can't get my S-video port to activate. I decided to install atitvout, that didn't work. Then I tried EnvyNR and that made the whole thing crash ( the screen was suddenly at 4:3 instead of 16:10 as it should be. I decided to scrap it and install Hardy Heron, but now my monitor isn't recognized and it runs on the default with no acceleration. Plus, my Broadcom wireless modem is lost.

I'll be trying 9.04 this weekend, any advice?

Thanks

---

### Post by switch10 on 2010-02-18
I have the 200m in my Gateway laptop.  It works perfectly, without any configuring at all under 9.10.  Download the drivers. and everything works.  It's way easier than previous versions...

No updates have messed up mine at all...

---

### Post by Smokex on 2010-04-07
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ly9000 on 2010-08-20
> **gwoodruff said:**
> This is what worked when the updates to Karmic broke my ATI Radeon Express 200m graphics

```
  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

reboot or restart x and you should be good2go.

It works !!!
Thanks you so much !!!

---

