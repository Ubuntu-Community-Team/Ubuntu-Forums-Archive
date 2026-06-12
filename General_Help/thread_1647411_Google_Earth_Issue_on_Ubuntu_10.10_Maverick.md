---
title: "Google Earth Issue on Ubuntu 10.10 Maverick"
date: 2010-12-17
forum: General Help
---

### Post by ckl on 2010-12-17
Hello all,;)
   
  I encounter an issue with Google Earth
   
  After following the installation
  [http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)
  which worked fine, Google Earth starts but I cannot use it because when I zoom in, the quality becomes worse.
   
  It's like the image is vectorized, straight lines and segments overlap the image
  See:
  [https://docs.google.com/leaf?id=0B96VX1rJWeekNWFkZjAxYTYtMGI3OC00ZGI0LTk0Y2QtYTkyNjQ5NjczNzVm&hl=fr&authkey=CILOyPMM](https://docs.google.com/leaf?id=0B96VX1rJWeekNWFkZjAxYTYtMGI3OC00ZGI0LTk0Y2QtYTkyNjQ5NjczNzVm&hl=fr&authkey=CILOyPMM)
   
   
  Have somebody and idea relative this issue 
   
  Thanks in advance
   
  Christian
   
  PS: I don’t know if this can help, but with my Compaq Presario R4000 I have to change my navigator, I moved from Firefox to Opera, because it happens 2 or 3 times, that my Ubuntu completely crash (PC Stopped in 2 seconds, and I have then to restart my PC) It seems that with Opera it's more stable.

---

### Post by petermck on 2011-01-09
I've got the same problem. It is worse with the 'Show terrain' option unchecked in Googleearth options.
I'm using a motherboard with an on board Radeon 2100 chip, Ubuntu Maverick and the ATI open source driver.
It appears this combination may be the problem. Someone else on here told me the fglrx closed source drivers work, but these drivers do not support this chip set (and a bunch of others) on kernels past 2.6.29.
So, at least in my case, it appears to be a problem with the ATI open source drivers.

---

