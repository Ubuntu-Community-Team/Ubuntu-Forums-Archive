---
title: "Ubuntu boots into CLI"
date: 2010-08-15
forum: General Help
---

### Post by ThomasTheTan on 2010-08-15
Hi-

I'm running 9.10 64 bit.  Yesterday, I installed some updates (through update manager) and, upon reboot, I go into the CLI and am unable to get to the GUI.

Things that I've tried:

1) Reverted back to the most basic xorg.conf file.  

Quite often (I'd say 50% of the time) when I install updates that ask me to restart my computer, I just get a black screen upon reboot.  Normally, I can go in with the live cd, revert to the oldest xorg.conf file, reboot, install drivers, reboot again, and I'm good. 

Not so much this time.  Reverting back to the oldest file didn't change anything - I still boot into the command line.

2) ```
startx
```This causes my computer to flash black (like x is starting) but then the command line reappears with a bunch of messages of the form
```
(WW) fglrx: No matching Device section for instance (BusID PCI:0@x:x:x) found
```where the "x" stand for random numbers.  These messages are followed by the following:
```
(EE) config/hal: couldn't initialise context: unknown error (null)

waiting for X server to shut down  ddxSigGiveUp: Closing log
```I get these messages regardless of the version of xorg.conf I am using. 

I've also tried ```
/etc/init.d/gdm restart
``` and ```
restart gdm
```but neither do anything (the first tells me to try the second, and the second gives me a bunch of random errors that I don't feel like reproducing, but will try if people think that this would be of help).

3) ```
dpkg-reconfigure xserver-xorg
```This does absolutely nothing.  I get no output at all.  It doesn't ask me any questions or produce any error messages.  I just get the prompt again on the next line.


Any suggestions?

---

### Post by ThomasTheTan on 2010-08-16
I decided to just install 10.04.  This was never solved, but I can get into my gui now.

---

