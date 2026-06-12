---
title: "No GUI Real time Kernel"
date: 2010-12-29
forum: General Help
---

### Post by oleink on 2010-12-29
Just installed a real time kernel on my new computer so I can record music.  My problem is that I have no GUI.  I noted that I would not when fglrx drivers could not be installed/applied to the new kernel when installing it.

---

### Post by cchhrriiss121212 on 2010-12-29
Rt kernels are not always patched for proprietary GPU drivers, you can either do this yourself (not easy) or try another kernel:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

---

### Post by oleink on 2010-12-30
> **cchhrriiss121212 said:**
> Rt kernels are not always patched for proprietary GPU drivers, you can either do this yourself (not easy) or try another kernel:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

Thanks this one didn't work either.  I've got an ati 5850 I couldn't find anything on what to do to get real time working and couldn't get the drivers to fix in the ones i've installed

---

### Post by cchhrriiss121212 on 2010-12-30
The open drivers should work (I think), is that an option for you? Last time I checked the ATI ones were quite good.

---

### Post by oleink on 2010-12-30
> **cchhrriiss121212 said:**
> The open drivers should work (I think), is that an option for you? Last time I checked the ATI ones were quite good.

I'm not sure.  I mean I can't login except through a terminal mode.  How would I even try that?

---

### Post by cchhrriiss121212 on 2010-12-30
You could edit xorg.conf with vim and specify to use the vesa driver, that would get a GUI back then you can remove fglrx.

A fresh install would use the open drivers automatically, which is what I would recommend.

---

### Post by oleink on 2010-12-30
> **cchhrriiss121212 said:**
> You could edit xorg.conf with vim and specify to use the vesa driver, that would get a GUI back then you can remove fglrx.

A fresh install would use the open drivers automatically, which is what I would recommend.

Thanks I may do a dual boot.  I use the graphics for games and compiz in my standard install.  (I'm a gamer and programmer)

---

### Post by oleink on 2010-12-31
> **cchhrriiss121212 said:**
> You could edit xorg.conf with vim and specify to use the vesa driver, that would get a GUI back then you can remove fglrx.

A fresh install would use the open drivers automatically, which is what I would recommend.

would it work to just uninstall fglrx drivers and then boot to the realtime and then when I get back on my generic kernel to reinstall the drivers

---

