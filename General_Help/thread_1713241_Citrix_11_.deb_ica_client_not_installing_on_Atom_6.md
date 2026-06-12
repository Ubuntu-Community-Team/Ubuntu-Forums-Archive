---
title: "Citrix 11 .deb ica client not installing on Atom 64 Ubuntu"
date: 2011-03-23
forum: General Help
---

### Post by Reeman on 2011-03-23
I get a wrong architecture error when I try to install the .deb

Frustrating as it seems the old incompatibility issues have reared their ugly head. A fully 32 bit enabled install of Ubuntu 10.10 86-64 on a D525 Atom based system does not seem to work at all. It will not install with gdebi or the new Ubuntu software centre.


Does anybody know why this might be happening? I have the 32 bit required OpenMotif libs installed...and all the other stuff that is i386 arch works perfect. I really want to run the 64 bit os but perhaps I can dual boot it with Fedora 32. There is nothing in the asus bios of the board that says emulate i386 like with AMD 64 chips...I thought that the D525 atom was fine as it will run 32 bit XP or any 32 bit linux.

So what might be the trouble with running 32 bit software on Ubuntu 10.10 64 on this machine? Why does the Ubuntu hacked gdebi software install system insist that i386 software is the wrong arch for this intel atom?

This is really maddening as my wife's work demands this citrix client, and the last thing that I want to do is run out and buy an oem of Windows 7...been there done that with 98, XP, and Vista arghhh!](*,)

I am looking to ditch her noisy POS vacuum cleaner vista machine..but I cannot do it until I have the linux citrix client installed and working.

Any help would be greatly appreciated.

---

### Post by grambo123 on 2011-05-15
Hello,
 
I bought one of those boards ASUS 510 Atom to set up a charities server.  The problem is not the board or Ubuntu but the graphics card.  Much like X in red hat you have to set iit up.  Go into the BIOS press DEL before the start up and change the graphics card to AGP/INT.  Then try again it will work.
 
How do you get a citirx client for linux I always thought it worked on Terminal Services (Windows) only.  Any examples ?

---

