---
title: "Wine, diablo 2 LOD &amp; intel 830M"
date: 2006-04-18
forum: General Help
---

### Post by krotaz on 2006-04-18
hi there.

this is my first post at the forum. And I'm a newb in some linux aspects.

I want to install diablo 2 on my ubuntu and I've found some problems that I hope you can help me with.

1.- after installing wine (with automatix) I installed diablo 2 but when I try to install the LOD expansion set I tells me that I've to install diablo 2    :???:  what can I do???

2.- diablo 2 lauches a video card test so you can choose direcdraw direct 3d and another opcion but when that test finishes tells me that the test can't find a suitable video card and that I've to installa the newest video driver. The quiestion here is. Is it necesary to install the video driver (I have an intel 82830M chipset on my Omnibook Xe3-gf laptop).

3.- I tryed to install the newest driver supplied by intel, but when I try to install it it send 2 errors 

[B]Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
[/B]

What do I have to do here?? I guess I've to install kernel modules, but, how am I supposed to do that???

thanks for your help

---

### Post by markr on 2006-04-19
I'm having similar problems with the video test, your best bet (which is what I'll be doing in a minute) is to go over to the Game section of this forum and see if other people have had similar problems. 

If I can't find a solution, I'll be posting a message so keep an eye out for it and we may be playing Diablo II on Linux sooner rather than later !!!

Mark.

---

### Post by krotaz on 2006-04-19
after reading a lot I get to this

**sudo gedit /etc/X11/xorg.conf**

and on the device section it displays this

[B]Section "Device"
	Identifier	"Intel Corporation 82830 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"[/B]

The driver that my ubuntu is using is the i810 but in one of the post here on the ubuntu forums someone said that the chip 810 does not support DRI wich I belive is my problem

Now thi thing is. How do I install the intel driver???

thanks for your help

---

