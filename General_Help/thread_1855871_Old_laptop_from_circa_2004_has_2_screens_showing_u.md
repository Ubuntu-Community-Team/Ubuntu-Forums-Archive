---
title: "Old laptop from circa 2004 has 2 screens showing up, resolution stuck at 640*480(4:3)"
date: 2011-10-07
forum: General Help
---

### Post by Rytron on 2011-10-07
Hi.

I got an old laptop from a friend. I said I'd take it to tinker with. On bootup I got this [image attached]. It has Ubuntu 11.04 on it. It has 2 screens showing up and the resolution is stuck at 640*480 (4:3).

I booted with a live CD and the loading screen was in full screen but it cannot get to the live desktop screen.

I ran a CD and could play audio CD with no problem. It also played a DVD.

Does anyone have a solution? Thanks.

---

### Post by mörgæs on 2011-10-07
Please give a full hardware description.

---

### Post by Rytron on 2011-10-07
The 2 screens are pushed to the left hand side.

Update: I ran recovery mode and ran in safe mode and then got full screen resolution. Then I rebooted in normal mode and all is solved!

---

### Post by Rytron on 2011-10-09
I spoke too soon. It seems that I must go through recovery mode to boot into a full screen resolution desktop. Not ideal.

---

### Post by WasMeHere on 2011-10-09
Try the long time support version Ubuntu 10.04 'lucid lynx'! This version has had longer time to be adapted to old computer hardware (compared to 11.04 that you are running now).

I think you should try the lightweight version Xubuntu (with xfce desktop) as well as the standard Ubuntu version! Alternatively you can download the corresponding Linux Mint version 9 'Isadora' based on Ubuntu 10.04 with xfce or lxde desktops.

Have fun finding which version will suit your computer :-)
Olle

*Edit: Just playing, the graphics might work better with 8.04 'hardy' or some old version of knoppix.*

---

### Post by Rytron on 2011-10-09
> **Olle Wiklund said:**
> Try the long time support version Ubuntu 10.04 'lucid lynx'! This version has had longer time to be adapted to old computer hardware (compared to 11.04 that you are running now).

I think you should try the lightweight version Xubuntu (with xfce desktop) as well as the standard Ubuntu version! Alternatively you can download the corresponding Linux Mint version 9 'Isadora' based on Ubuntu 10.04 with xfce or lxde desktops.

Have fun finding which version will suit your computer :-)
Olle

*Edit: Just playing, the graphics might work better with 8.04 'hardy' or some old version of knoppix.*

Thanks, I may try those distros you mentioned.

---

### Post by Brad55 on 2011-10-09
What is the video card in the laptop?

Take a look at your xorg.conf file. Compare it to the one in recovery mode.


Well you can try Ubuntu 10.04 but I have had problems getting it to work on my old laptop. I can get Ubuntu 9.04 to work just fine. Any thing above 9.04 will show a black screen on the laptop. The funny thing is that Fedora 14 works great on the laptop. 

The laptop is a Tobhisa Satellite mx35 and has the intel video in it.

---

### Post by Rytron on 2011-10-09
> **Brad55 said:**
> What is the video card in the laptop?

Take a look at your xorg.conf file. Compare it to the one in recovery mode.


Well you can try Ubuntu 10.04 but I have had problems getting it to work on my old laptop. I can get Ubuntu 9.04 to work just fine. Any thing above 9.04 will show a black screen on the laptop. The funny thing is that Fedora 14 works great on the laptop. 

The laptop is a Tobhisa Satellite mx35 and has the intel video in it.

Hey Brad55.

It is an old generic laptop that someone didn't want. I ran a report and it says this:
Display:
Video Adapter: Intel(R) 82845G/GL/GE/PE/GV Graphics Controller (64 MB)
3D Accelerator: Intel Extreme Graphics
Monitor: Digital Flat Panel [1024x768]

I will get back to you re xorg file.

---

### Post by Brad55 on 2011-10-09
> **Rytron said:**
> Hey Brad55.

It is an old generic laptop that someone didn't want. I ran a report and it says this:
Display:
Video Adapter: Intel(R) 82845G/GL/GE/PE/GV Graphics Controller (64 MB)
3D Accelerator: Intel Extreme Graphics
Monitor: Digital Flat Panel [1024x768]

I will get back to you re xorg file.

I think that is about the same one I have. I have the Intel 82852/GME in mine, so try one of the older disto's like Ubuntu 8.04 or 9.04 see if they boot up live, or you could install Fedora 14 or try it live. I wanted Ubuntu 10.04 on mine but it just won't work.

This laptop is one some one gave me because the screen was broken, and I paid $200 for a screen and put it in, and has work ever since about 4 years now. I have it dual booting WinXP and  Fedora 14, I use it for work.

---

### Post by mörgæs on 2011-10-10
Whatever you do, don't install an obsolete release of Ubuntu. It is a major security threat.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)


Ubuntu 10.04.3 is a good choice, but you might need some modifications:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by hansdown on 2011-10-10
Rytron, how are you, buddy?

I notice from your screenshot, that the classic mode is running.

That's good, 'cause, I think, that a fix is possible.

click System> preferences> monitors> detect monitors.

Hopefully, You can correct the settings.

---

### Post by WasMeHere on 2011-10-10
Hello Rytron,

It will be really interesting to read what you find is the best OS for your old laptop.

Have fun
Olle

---

### Post by Rytron on 2011-10-10
> **hansdown said:**
> Rytron, how are you, buddy?

I notice from your screenshot, that the classic mode is running.

That's good, 'cause, I think, that a fix is possible.

click System> preferences> monitors> detect monitors.

Hopefully, You can correct the settings.

Tried that, no joy.

---

### Post by Rytron on 2011-10-11
I tried these Live CD's:
Debian 6.0.1 - all was fine
KNOPPIX 6.2.1 - all was fine
Linux Mint 9 - loaded but would not get to desktop screen
PCLinuxOS 2010.10 LXDE - it had 2 screens
Puppy Linux 5.0 - all was fine

I guess I could try alt CD's for Ubuntu/Xubuntu 10.04.

---

### Post by WasMeHere on 2011-10-11
> **Rytron said:**
> I tried these Live CD's:
Debian 6.0.1 - all was fine
KNOPPIX 6.2.1 - all was fine
Linux Mint 9 - loaded but would not get to desktop screen
PCLinuxOS 2010.10 LXDE - it had 2 screens
Puppy Linux 5.0 - all was fine

I guess I could try alt CD's for Ubuntu/Xubuntu 10.04.

Thank you for sharing :-)
Olle

---

### Post by Rytron on 2011-10-11
> **Olle Wiklund said:**
> Thank you for sharing :-)
Olle

No problem.

Benjamin Franklin: "An investment in knowledge pays the best interest."

;)

---

### Post by Rytron on 2011-10-19
> **Brad55 said:**
> What is the video card in the laptop?

Take a look at your xorg.conf file. Compare it to the one in recovery mode.


Well you can try Ubuntu 10.04 but I have had problems getting it to work on my old laptop. I can get Ubuntu 9.04 to work just fine. Any thing above 9.04 will show a black screen on the laptop. The funny thing is that Fedora 14 works great on the laptop. 

The laptop is a Tobhisa Satellite mx35 and has the intel video in it.

Hello Brad55.

Sorry for the late reply.

I installed Ubuntu 10.04 from the alt CD.

The laptop does not boot into screen every time. Sometimes I can login and hear sound but have no picture.

Update:
There was no xorg.conf file in /etc/X11/ I don't understand that. Surely a GUI would have been impossible without an xorg.conf file?
I went to System >> Preferences >> Monitors and did something like apply monitor. Then an xorg file appeared in /etc/X11/.

Please find the xorg file attached.

I fired up the relic today and  got to the desktop screen. Then after a few minutes the screen started to flicker and I was unable to use it. This may have been an issue with the screensaver - I disabled it and will post back on any updates.

Edit: Sometimes when I reboot, it just hangs with a blank screen. Also there are no proprietary drivers being used (or available).

---

### Post by Rytron on 2011-10-20
I notice that if I login to the laptop and leave it for a minute or so, I get this: [http://www13.speedyshare.com/files/30842961/download/2004%20laptop.gif](http://www13.speedyshare.com/files/30842961/download/2004%20laptop.gif). The only thing is to shut down and reboot. What could cause this?

---

