---
title: "Display resolution"
date: 2010-05-23
forum: General Help
---

### Post by jadefox on 2010-05-23
Hey all,

Just installed ubuntu 10.x 64bit on my PC, My setup is very unusual, i have my rig's gfx card (radeon 4870 1gb) DVI port with a DVI - HDMI adaptor which also carries sound going to my 27" Widescreen TV resolution 1366x768.

Ive tried setting it via monitors in the menu but it only gives me preset resolutions, i cant figure out how to add my own custom one, after a google search i found this page [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) But i get errors or unknowns after almost every line, could someone please tell me how to set my monitor resolution to 1366x768 @ 25, 30, 50 hz

I couldn't find an ATI program, im pretty sure the drivers are there, after looking for hardware drivers it couldn't find any so i guess its working, 'Extra' effect work like wobbly windows but i need that resolution desperately.

Thanks in advanced

---

### Post by SlidingHorn on 2010-05-23
please post your xorg.conf file if it exists...

---

### Post by jadefox on 2010-05-23
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Hmm, this time after connecting to the internet, its seems to have found drivers for my card aswell, just installed, will see what happens.

---

### Post by jadefox on 2010-05-23
Hmm, okay, after installing the hardware update, i now have lots of new resolution options, 1280x720 and 1280x768 are close but no 1366x768/720 any chance i can set this custom one in Catalyst control centre or any other way?

Thanks

---

