---
title: "Poor games peformance"
date: 2011-02-27
forum: General Help
---

### Post by BADGER.BRAD on 2011-02-27
Hello All,

I have been trying to run a few games for my son to have a mess about with but none of the free games seem to work I'm running Xubuntu on a 2.93gig machine with 2 gig of ram is this not enough for Linux the machine seems to work fine in Windows or Dos.The games run very slow and keep stuttering and crashing even the most simple of them.

Any help much appreciated.

Brad

---

### Post by mali2297 on 2011-02-27
Hello Brad,

To troubleshoot...

Can you give some examples of the simple games that you experience problems with? Are they native Linux games or run through an emulator?

What kind of graphics card is in the computer? Have you installed the proper driver for it?

---

### Post by BADGER.BRAD on 2011-02-27
Many thanks for getting back to me mali2297 ,much appreciated doing lspci from terminal gave me VGA compatible controller silicon integrated systems [sis] 661/741/760 PCI/AGP or 662/7616 pci VGA display adapter if that helps ? I have not installed any drivers other than the standard ones which came with Xubuntu. The games are linux games and came from the Xubuntu repository, games such as criticalmass ,free tennis alien arena and many more. 

Again many thanks for your help

Brad UK

---

### Post by BADGER.BRAD on 2011-02-27
Just checked my drivers from xubuntu and exactly as below happened
If "No proprietary drivers are in use on this system" is displayed after  the hardware scan is complete, your video card does not support the  advanced drivers available in Ubuntu. Check with your video card  manufacturer to see if they offer updated Linux drivers for your  particular graphics card.

Thanks

Brad
[LEFT][COLOR=#000000]

[/COLOR][/LEFT]

---

### Post by yusof125 on 2011-02-27
Let try:
Go to system update manager
and keep the OS up-to-date , keep checking for update.

Go to applications xubuntu software center 
and get software : Additional Drivers

Install and run it, there're maybe the solutions for this messy

---

### Post by mali2297 on 2011-02-27
Hello,

All the games that you mention seem to be 3D and use OpenGL. For these, it is important to have sufficiently advanced graphics drivers.

When searching for SiS drivers for Linux, I found this site:
[http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

I do not have the solution for you, but at least you know better where the problem lies.

---

