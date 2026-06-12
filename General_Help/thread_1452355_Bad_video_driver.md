---
title: "Bad video driver"
date: 2010-04-11
forum: General Help
---

### Post by wane on 2010-04-11
Hi, 

I'm a little new to ubuntu ... I installed a video driver and after restarting I got as far as the log in screen where I saw that the driver did not work: screen is mostly black with random bars of color. I was only able to restart in recovery mode mode. I tried the fix graphics option, which did not work and also some commands that I've seen posted in other threads. So far, still cannot delete the problematic driver or boot up normally successfully. 

Any help would be very appreciated.

---

### Post by wane on 2010-04-11
Nevermind,

sudo apt-get remove -xorg-driver-fglrx

seems to do the trick.

---

