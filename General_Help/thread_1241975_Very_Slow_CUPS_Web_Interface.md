---
title: "Very Slow CUPS Web Interface"
date: 2009-08-16
forum: General Help
---

### Post by i.wanna.corndog on 2009-08-16
I have CUPS installed on my Ubuntu box that sits in my closet, but for some reason the CUPS interface is unbearably slow (i.e. it takes at least a minute to load each configuration page. I am on a rather large network, so I'm not sure if this issue is due to the fact that CUPS is searching the network for shared printers or something like that.

Is there any way I could diagnose this issue or figure out why CUPS is taking so long to come up?

---

### Post by soldersplash on 2009-12-29
I have similar experience with CUPS on Ubuntu server 8.04. Not a large network though, just a few machines in a domestic setting. Anyone got any ideas for us? I have been searching here and Googling but have not found relevant answers yet...

---

### Post by soldersplash on 2010-05-31
Shameless bump! I still haven't found any answers to this...

---

### Post by soldersplash on 2010-12-05
I found the root of _my_ problem! I have a USB printer added to CUPS in addition to a parallel port printer. Whilst I could print to the parallel port OK, not withstanding the massively slow web interface, the USB one wasn't working anyway and I had given up on it. However, the owner:group for the /dev/usb/lp0 where root:root which wasn't right compared to the parralel port printer which had /dev/lp0 root:lp . A-ha! So I 'fixed' the permissions for the /dev/usb/lp0 [ sudo chown root:lp /dev/usb/lp0 ] and now the USB printer works AND the web interface is positively snappy! :guitar: 

Whilst reading around the net I also came across references to DNS resolution problems causing painfully slow CUPS performance, so if you have this problem and it's not a permissions thing, maybe check that too?

---

