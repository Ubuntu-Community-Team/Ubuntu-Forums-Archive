---
title: "Compiz not enabling"
date: 2010-01-30
forum: General Help
---

### Post by woodmaster on 2010-01-30
setting up Compiz and can't seem to enable...I got Compiz Check and it returned an error:
```
Checking for hardware/setup problems...           FAIL

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
```
any ideas on this?
I use xfce mostly lately but it is a regular Ubuntu Gnome install...my wife doesn't seem to like XFCE

---

### Post by rogue_0111 on 2010-01-30
This thread should be of assistance:

[http://ubuntuforums.org/archive/index.php/t-1018240.html](http://ubuntuforums.org/archive/index.php/t-1018240.html)

--

---

### Post by woodmaster on 2010-01-31
I don't seem to have a file called: > /etc/X11/xorg.conf
Is that possible.  Or is it someplace else?

---

### Post by rogue_0111 on 2010-01-31
Ok so 9.10 does not come with an xorg.conf file.

It seems that you have a resolution issue. Try "lxrandr" it has a nice GUI and easy to use.

To install:

apt-get install lxrandr

---

### Post by woodmaster on 2010-01-31
should I let it as auto...How do I know what resolution my screen is supposed to be?  all other options don't look right.

---

### Post by woodmaster on 2010-01-31
bump

---

### Post by rogue_0111 on 2010-01-31
> **woodmaster said:**
> should I let it as auto...How do I know what resolution my screen is supposed to be?  all other options don't look right.

Sure try Auto an see if you can run Compiz. If that doesn't work try another resolution setting. 

This is the fun part:) So close to a fix.

---

### Post by woodmaster on 2010-01-31
none of them will allow enabling compiz and a few made my screen go crazy!!!  Had to reboot and it all seems fine now.  Still no Compiz:-<  Just might have to live without it...

---

### Post by FunkeyMonk on 2010-03-18
I get the same error.

In Ubuntu 9.04, Compiz works flawlessly on the same machine.  (Toshiba Satellite M115)  In Ubuntu 9.10, I can't get Compiz to start at all.

I do not have an external monitor connected, nor have I EVER connected one.

Compiz-Check gives the same "Software Rasterizer in Use" error.

---

