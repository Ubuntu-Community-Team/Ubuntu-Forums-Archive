---
title: "Ubuntu installation problem ?"
date: 2011-12-30
forum: General Help
---

### Post by Vudothienan on 2011-12-30
I have a PC HP Pavilion a4327: AMD Athlon II 240 Dual Core, 4GB Ram, onboard GPU is GeForce 6150SE, when I install Ubuntu on this graphic card everything went well and I just bought a new Radeon HD 6570 GPU and when I tried to use Ubuntu on CD, the screen said "Stopping system v runlevel compatibility". If I install on my PC, the screen keep flashing and I cannot logon to my computer, I think Ubuntu does not support my GPU, please help !!! thanks

---

### Post by gordintoronto on 2011-12-30
What version of Ubuntu? Did you install a video driver? If so, remove it before you install a different video card.

You might need to disable the on-board video in the BIOS.

---

### Post by Vudothienan on 2011-12-30
> **gordintoronto said:**
> What version of Ubuntu? Did you install a video driver? If so, remove it before you install a different video card.

You might need to disable the on-board video in the BIOS.
It's 11.4 and I can't get to the desktop. After I install Ubuntu and it told me to restart, I restart my computer and the screen keep flashing rapidly so I cannot do anything.

---

### Post by Alln on 2012-01-05
Same problem here!

I have a GeForce 6150SE nForce 430 and I can't able to install Ubuntu 11.10 with live CD.

I downloaded Alternate, and installed...

To install display driver, I had to do this:
[LIST]
[*]Edit grub menu entry, replacing "quiet splash" to "nomodeset"
[*]Wait about 1 minute to press "Ctrl + Alt + F1" and go to console mode
[*]Run NVIDIA-Linux-x86-290.10.run
[/LIST]

One xorg.conf file is created, but when after reboot, the Ubuntu don't start properly!
~1 minute processing something, and then: Black screen! :(
Ctrl + Alt + F1 ...

Curious that I've renamed the /usr/share/X11/xorg.conf.d to xorg.conf.test, and the graphics work!!! Login screen, waiting y password... Perfect! :-k

But, no mouse, no keyboard, no power button, no kind of input!

WTF is going on?! ](*,)

Anyone, HELP ME!

---

