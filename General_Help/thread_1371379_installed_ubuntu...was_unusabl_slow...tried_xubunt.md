---
title: "installed ubuntu...was unusabl slow...tried xubuntu...still painfully slow"
date: 2010-01-03
forum: General Help
---

### Post by blackmajik2021 on 2010-01-03
I've been in need of an extra computer for a while, and the other day my friend just happened to be getting rid of a dell dimension 8200 p4 1.8 ghz with 256 mb ram. I installed ubuntu on it and it was so slow it was broken, I would have to wait upwards of a minute to load websites and do basic things. I decided to try xubuntu which I've heard is a lot better for old computers like this, and while it definitely runs better (about twice as fast), Its still the slowest thing in the world. The problem is that this computer uses RD ram which is pretty rare and expensive  (200$-300$ for a 1 GB kit). I managed to find a cheap 256 kit on ebay which i will be adding whenever it comes in the mail.

basically I want to know what I can do to speed up xubuntu while still running with the GUI.

---

### Post by Svens on 2010-01-03
Are you shure that the PC is fine physicaly? Is everything fine with the PC's HDD?

---

### Post by Sef on 2010-01-03
> dell dimension 8200 p4 1.8 ghz with 256 mb ram.


256 mb ram is not enough for Ubuntu.   You really should have at least 512 mb.


From the community documents:

> **Recommended minimum requirements**

 Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor 
[*]384 MB of system memory (RAM) 
[*]8 GB of disk space 
[*]Graphics card capable of 1024x768 resolution 
[*]*Sound card* 
[*]*A network or Internet connection* 
[/LIST]
**Note:** All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 

---

### Post by blackmajik2021 on 2010-01-03
> **Sef said:**
> 256 mb ram is not enough for Ubuntu.   You really should have at least 512 mb.


From the community documents:

right, thats why i said i switched to xubuntu which says it needs 192 MB ram. 

and yes, i installed a different hard drive, a 120 gb 7200 rpm I had in another machine. I also installed a GeForce5200FX 128mb...though each time i install the drivers the system never boots and i have to re-format...so the GeForce is basically sitting in there doing nothing right now.

---

### Post by Leppie on 2010-01-03
xubuntu requires a minimum of 192mb.
are you sure there isn't some other issue like graphics drivers?

---

### Post by blackmajik2021 on 2010-01-03
like i said, the computer crashes when i try to install the nvidia restricted drivers...crashes to the point where I couldn't figure out how to even boot and try to fix it and I had to reformat. reformatting takes a long time and I dont want to have to do that again.

---

### Post by Leppie on 2010-01-03
maybe install them while x is not running?

---

### Post by SinxarKnights on 2010-01-03
Xubuntu being for old computers is kinda a myth. This machine i'm using now has Xubuntu installed, 256MB RAM and a P3 900 MHz processor (old laptop).

What I ended up doing was installing LXDE. Its a lightweight window manager. Works very well for very low end hardware, although Firefox is still really slow and trying to watch Flash videos is a nightmare. But it does help to switch to a lightweight manager and just add any applets you need (such as the the network manager).

I heard the same rumor that Xubuntu was lightweight and all that, maybe it is compared to Ubuntu but its still way too much for old hardware. 

You can try LXDE without reinstalling. Just install:

```
sudo aptitude install lxde
```

then just logout and select LXDE from the "Session" menu on the login screen.

There are others aswell, Fluxbox, IceWM etc, but they required too much setup for my taste.

---

### Post by Leppie on 2010-01-03
#! (crunchbang) is more towards low end equipment, still ubuntu based (but current release is based on jaunty).

---

### Post by blackmajik2021 on 2010-01-03
i just installed chrome...oh my god what a difference. I can actually run multiple browsers now with no slowdown, and i can type on my keyboard without lag. 

:D

---

### Post by Leppie on 2010-01-03
> **blackmajik2021 said:**
> i just installed chrome...oh my god what a difference. I can actually run multiple browsers now with no slowdown, and i can type on my keyboard without lag. 

:D

still in xubuntu? or you installed the chrome os?

---

### Post by Shippou on 2010-01-03
If you have time, you can also try the following distros:

1. DSL (Damn Small Linux). Only 50MB and runs IceWM.
2. Puppy Linux. Only 100+MB and runs IceWM (I think).

Have fun with Linux. :)

---

### Post by blackmajik2021 on 2010-01-03
in xubuntu...I also disabled power saver and print queue applet from startup and then re-booted. 

web browsing is now super fast, which is all I really need. flash still bogs it down a bit but im hoping that will get better once I get this extra ram installed.

---

### Post by Leppie on 2010-01-03
> **blackmajik2021 said:**
> in xubuntu...I also disabled power saver and print queue applet from startup and then re-booted. 

web browsing is now super fast, which is all I really need. flash still bogs it down a bit but im hoping that will get better once I get this extra ram installed.

glad your system is giving you good response now :)

flash isn't something that is likely to work on linux as smooth as on windows. adobe doesn't seem to be very interested in the open source community (they'd rather make plenty of money selling 1 app, sounds like another software house...) :(

---

