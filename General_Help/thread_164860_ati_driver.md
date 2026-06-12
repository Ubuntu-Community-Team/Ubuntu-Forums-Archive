---
title: "ati driver"
date: 2006-04-23
forum: General Help
---

### Post by anxean on 2006-04-23
anxean@nixbox:~$ /usr/X11R6/bin/fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

anxean@nixbox:~$ /usr/X11R6/bin/aticonfig
/usr/X11R6/bin/aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
anxean@nixbox:~$ /usr/X11R6/bin/mmapr

I tried installing this thing, and it gave me a control panel icon(doesnt work)


can anyone tell me how to install these drivers?(ati x800pro)

---

### Post by Ensnared on 2006-04-23
Provided your card is supported by the driver, following [these instructions](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide) will probably make it work. Before I tossed out my ATI-card I always used the instructions from that wiki to install the drivers downloaded from ATI, and they always worked on the first try.

---

### Post by adamkane on 2006-04-23
Which card do you have? Give details.

---

### Post by Ensnared on 2006-04-23
[QUOTE=adamkane]Which card do you have? Give details.[/QUOTE]
Since he already stated he's got an ATI X800 Pro I'll assume you mean me. I had an ATI Radeon 9800 Pro before getting an nVidia card, but I still have an ATI Mobility Radeon 9000 on my laptop.

Both the driver and the method of installing it are the same though.

---

### Post by anxean on 2006-04-23
What do i put for my bus identifier?

Ubuntu Configuration







               &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
               &#9474; Please enter the video card's bus identifier.  &#9474;
               &#9474;                                                &#9474;
               &#9474; PCI:1:0:0_____________________________________ &#9474;
               &#9474;                                                &#9474;
               &#9474;                     <Ok>                       &#9474;
               &#9474;                                                &#9474;
               &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


I am using agp, the deafult value is there^

---

### Post by adamkane on 2006-04-23
anxean should also give steps that have been taken up to the error messages.

---

### Post by Ensnared on 2006-04-23
[QUOTE=anxean]What do i put for my bus identifier?[/QUOTE]
Chances are the default is correct, but to make sure you can enter this command at the commandline:
```
lspci -X | grep ati
```
That will show the bus identifier as it should be entered for the X configuration. For example, on my server with an old ATI PCI-card, that command produces this output:
```
PCI:0:12:0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]
PCI:0:14:0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
```
Of course, the interesting line here is the VGA controller one - the other one shows up because of the "ati" in "Corpor**ati**on" for my network adapter. So in my case, the correct bus identifier is "PCI:0:12:0".

---

