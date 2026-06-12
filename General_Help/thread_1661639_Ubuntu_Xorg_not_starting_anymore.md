---
title: "Ubuntu Xorg not starting anymore"
date: 2011-01-07
forum: General Help
---

### Post by arloth on 2011-01-07
I recently upgraded the memory in one of my computers running Ubuntu 10.10 amd64 to 4GB of RAM from 2GB.  It's a Biostar TA690G AM2, with an Athlon X2 BE-2400 in it. It supposedly supports up to 4GB of RAM when done as 4 1GB sticks, at least according to the original manual that came with it.  Upon start up, I no longer get my login screen, it appears to crash when it gets to the part where it starts up Xorg.  

At first I figured the memory might not be happy with the computer so I ran Memtest86, every thing seems fine there.

So I try the recovery boot to the root prompt with networking. Everything seems to work fine there, at least as far as a root prompt with no gui goes..  However, if I try startx here, it crashes again.

Ok, so I then try an Ubuntu 10.10 amd64 boot CD.  I get the Try/Install buttons in the little Xorg intro gui running.  It's getting my hopes up now.  However upon clicking "Try Ubuntu" it thinks for a second or two and then locks up, with the busy mouse cursor icon still spinning.

I don't have windows installed on this computer, so I can't really say that it works fine in windows.

Is there some weird BIOS setting or xorg.conf setting that needs to be enabled so that it doesn't croak?  The Bios recognizes the memory, Memtest86 recognizes the memory, and Linux recognizes the memory (at least until xorg starts).

If I pull one of the sticks out, it will once again run, but then it's in single channel mode, and I'm missing out on 1GB of RAM goodness.

---

### Post by arloth on 2011-01-07
I made an interesting discovery.  Xorg seems to start up fine if you use the vesa driver.   It will not start with the fgrlx (radeon 4550), or the nvidia driver (GTX275).   The instant I try startx with either of these the computer crashes. In one instance I did manage to get a garbled picture and the startup sound to play, at which point it promptly crashed.

So, what's the deal with 4GB RAM and a video card? O.o

---

### Post by Krytarik on 2011-01-07
Obviously at least some mainboards fall behind their specs regarding the maximum installable RAM bars.

A while ago I tried to run 3 bars in 3 slots, maximum at this board, and my system also crashed after some minutes. After removing the bar with the lowest capacity, everything worked fine again.

---

