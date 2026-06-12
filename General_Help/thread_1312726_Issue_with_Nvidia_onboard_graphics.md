---
title: "Issue with Nvidia onboard graphics"
date: 2009-11-03
forum: General Help
---

### Post by nexoncore on 2009-11-03
I actually left the last version of ubuntu because of this issue, and was hoping this version would resolve it, but it hasnt.

**Problem**
Maximum Resolution is 800x600 on a brand new gaming computer when using ubuntu. ( Windows gives a max Working resolution of 1600 x 1024 ).

[B]Hardware
[/B]Nvidia GeForce 7100 onboard graphics card ( Built into GigaByte Mother Board )

[B]Tried following to resolve issue
- [/B]Restricted Driver Option
- Several Nvidia Drivers from nvidia.com which claim to fully support the card

Can someone please help me with this, I have literally tried everything I could but I am not getting anywhere, I even have a huge google history regarding this issue. I am hoping to go back to ubuntu, but the resolution is so low that I cant even see the Apply button at the bottom of most windows.

---

### Post by DGortze380 on 2009-11-03
> **nexoncore said:**
> I actually left the last version of ubuntu because of this issue, and was hoping this version would resolve it, but it hasnt.

**Problem**
Maximum Resolution is 800x600 on a brand new gaming computer when using ubuntu. ( Windows gives a max Working resolution of 1600 x 1024 ).

[B]Hardware
[/B]Nvidia GeForce 7100 onboard graphics card ( Built into GigaByte Mother Board )

[B]Tried following to resolve issue
- [/B]Restricted Driver Option
- Several Nvidia Drivers from nvidia.com which claim to fully support the card

Can someone please help me with this, I have literally tried everything I could but I am not getting anywhere, I even have a huge google history regarding this issue. I am hoping to go back to ubuntu, but the resolution is so low that I cant even see the Apply button at the bottom of most windows.

Did you actually get a supported driver installed?
Change the resolution with the nVidia Managment App under System -> Prefences -> nVidia

---

### Post by nexoncore on 2009-11-03
I tried that, but the max resulution in there is 800 x 600.

I dont know if the drivers are to blaim, or if linux in general doesnt want it to output a decent resolution.

---

### Post by Vaeil on 2009-11-03
Just fixed something similar on my own computer.

This is going to require a bit of command line work, don't worry, it's rather simple. Can't guarantee it works;

Open up a terminal. You need superuser rights for both these actions (put 'sudo' in front of the command)

> nvidia-xconfig (Should give you a clean configuration file to work with)

> gedit /etc/X11/xorg.conf (This should open up a text editor)

Between 'Section "Screen"' and 'EndSection', add:

SubSection "Display"
Viewport 0 0
Depth 24
Modes "1024x768x60Hz"
EndSubSection

Replacing Depth with the value of DefaultDepth in that file, and replacing the values behind "Modes" with your own resolution.

Save and exit, then restart.

---

### Post by nexoncore on 2009-11-03
Which driver are you using though, one of the restricted?

I am going to make a fresh installation now and try what you put.

---

### Post by nexoncore on 2009-11-04
Its strange, but when I installed it to the hard drive and used restricted driver, it worked perfect first time.

Thanks for you help

---

### Post by nexoncore on 2009-11-05
I WANT TO SCREAM!!!!

I had to reinstall ubuntu, because I had to reinstall vista due to errors on there. WHen I did, I followed the guide for restoring Grub on the ubuntu website. Which did not work at all.

So I resorted to installing ubuntu fresh again, and this time nvidia is not working, I looked in the Hardware Drivers option and it says no propriety drivers are in use, and it no longer lists the nvidia drivers, theres no drivers there.

Someone please help before I smash this computer up, its got me so furious!

---

