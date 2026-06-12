---
title: "Intel onboard graphics issue"
date: 2009-07-29
forum: General Help
---

### Post by hairypreacher on 2009-07-29
Hello all, 
I've been using this for forum for a while now and have always found the information I am after by simply using 'search' :D 
However in the process of helping a friend escape the joys of windows :wink: I have come across a problem...

Its an old Dell machine and he needs to keep the installation of windows, the live DVD (from Linux format's get started with UBUNTU 9.04 special edition) boots but only in safe graphics mode,

The computer spec is
Celeron 2 GHz
2Gb ram
Intel 82845G Rev 03 Onboard graphics

Using a live Puppy CD the graphics are fine...
I was thinking of installing ubuntu and then working through the graphics issue as I obviously cant make any changes to the dvd but I cant as the installer screen is expanding of the edge of the display and I am unable to move or shrink the window, my other option is to install a geforce pci card that I know works with ubuntu but I dont really want to have to get into installing drivers in windows if I can help it so using the existing hardware would be FAR simpler.

Many Thanks

---

### Post by MockY on 2009-07-29
Jaunty Jakalope (9.04) is NOT the distro of choice if you sit with an Intel graphics card. All my laptops have Intel graphics and I'm patiently waiting to upgrade. I recommend installing Intrepid Ibex (8.10) or wait until Koala is released.

---

### Post by hairypreacher on 2009-07-29
I'll be off to download 8.10 then :)

Thanks very much

---

### Post by hairypreacher on 2009-08-09
Hello again, 
Back with the same computer as the above post but now with a geforce 5200 PCI card
 
Windoze XP is perfectly happy with the new card after I have changed the bios to 'pci graphics' (the mobo only has pci slots)


Now if I try Ubuntu live 8.04, 8.10 or 9.04 it gets part way through booting and stalls I tried Puppy also and the same problem, if I return bios to onboard graphics all is well.

I have installed the Graphics card because I really want to return the computer to my friend with 9.04 if at all possible as he has a decent guide for it and this will help him swap over to Linux from windoze. 

I cant install Ubuntu on the computer with the onboard graphics then swap over as Ubuntu wont install with the onboard graphics (see first post) :)

Many thanks

---

### Post by VMC on 2009-08-09
> **hairypreacher said:**
> Hello all, 
I've been using this for forum for a while now and have always found the information I am after by simply using 'search' :D 
However in the process of helping a friend escape the joys of windows :wink: I have come across a problem...

Its an old Dell machine and he needs to keep the installation of windows, the live DVD (from Linux format's get started with UBUNTU 9.04 special edition) boots but only in safe graphics mode,

The computer spec is
Celeron 2 GHz
2Gb ram
Intel 82845G Rev 03 Onboard graphics

Using a live Puppy CD the graphics are fine...
I was thinking of installing ubuntu and then working through the graphics issue as I obviously cant make any changes to the dvd but I cant as the installer screen is expanding of the edge of the display and I am unable to move or shrink the window, my other option is to install a geforce pci card that I know works with ubuntu but I dont really want to have to get into installing drivers in windows if I can help it so using the existing hardware would be FAR simpler.

Many Thanks

Intel graphics chips are a known problem. Read some of the following links. It can be fixed though.
[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)
This is the one I have to use. I have integrated i865 chip:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
How to Fix Intel chip:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
Alternate Method:
[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)

---

