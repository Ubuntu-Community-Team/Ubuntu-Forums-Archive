---
title: "Multiple users on One system Project"
date: 2006-03-22
forum: General Help
---

### Post by whazzup on 2006-03-22
If I'm posting in the wrong forums, do tell me!

Ok, My final AIM:
One system feeding 2-3 users with their own Monitor/Keyboard/Mouse/Audio.

Running Ubuntu as the OS.

Main Apps: Opencanvas 1.1b72

Hardware: Yet to be determined, but probably:
Gigabyte GA-8VM800M (onboard graphics)
Celeron 2.13D
512mb DDR-400 
Wacom Graphire3 tablet


My fren is thinking of holding some basic drawing lessons, and needs a classroom of sorts. So he basically requires ard 10 sets of computers and tablets. But the cost of such a setup is considerable. So I had the idea of deploying Linux systems to do away with the Windows licensing. And if we could setup 1 system to accomodate 2 users, we will be able to get by with 5 systems instead of 10.

I'm not a Linux person, but I'm taking the opportunity to learn some new stuff, and basically see how it can help me. And if there're similar cases like this previously, can anyone point me to the threads? 
Searching 'Two users on One computer' didnt really help.... :mrgreen: 




With that, some questions:

1)  Any FAQ on setting up multiple users on 1 comp?

2) The motherboard I had in mind has an onboard VGA and an AGP slot. In view of my usage, would it be better if I let 1 user use the onboard VGA, den another user use the AGP VGA? Or better if I hook up both users to the two ports of the AGP VGA card?

3) I tried the Ubuntu LiveCD, enabled Wine in Synaptics>Cross Platorm (universe), but when I tried opening Opencanvas (the program is just an .exe file) with wine, an error msg tat wun close pops out. Did I install Wine the right way?

4) Opencanvas has a network function that enables people from different computers to draw on the same canvas. Will Ubuntu be able to do that, thru Wine?





These are the questions I have so far. Taking the next few months to get myself up to speed on using Ubuntu/Linux, so if anyone can give me some pointers on where to look for information, that'll be great!

---

### Post by joshuapurcell on 2006-03-22
The only real problem I see at this point is getting multiple keyboards/mice hooked up to the computer. I guess you could use all USB devices though... you would need to somehow associate a specific USB device with a specific screen (and that I'm not familiar with).

I am familiar with VNC though, and you can do all kinds of cool things with virtual X sessions either remotely or locally on a machine. There's a problem here as well, since most of the time if you have an integrated video card and an AGP (or PCI slot) available for an add-on graphics board, the integrated card will automatically get disabled on the BIOS level when a new card is installed (or there will be a BIOS switch that you will need to use to select either one or the other). You can get around this by just buying dual-output video cards and not worrying about having integrated video on the motherboard. Matrox makes some inexpensive dual-output cards, and they may be useful in this setup.

I think the main problem will be connecting two USB keyboards (or two USB mice) to the system. There may be a better way than this and if so someone will post it, but if not then it will be a learning experience (for me at least) whether or not these USB devices can work this way.

---

### Post by z_diver on 2006-03-22
You should probably have a look at Edubuntu, an amazing Environment for teachers.  With that you would be able to have many slim clients run from one "server".  I know that is not exactly what you are asking for but it's the only way I know of to acheive similar results.  

One obstacle with this for your scenario is that Opencanvas is a Windows based.  If the goal of this class is to teach oC then you will want to use a windows terminal server client combo or full featured windows desktops.

Good luck with the project!

---

