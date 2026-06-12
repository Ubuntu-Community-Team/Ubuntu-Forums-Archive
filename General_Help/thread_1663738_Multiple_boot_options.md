---
title: "Multiple boot options"
date: 2011-01-10
forum: General Help
---

### Post by geo132 on 2011-01-10
Hi, 
recently i started noticing that grub is adding "OS" to the bootload with no obvious reason:
at first i had ubuntu,memtest, windows 7. after a month: ubuntu,ubuntu,memtest,windows7. last week: ubuntu,ubuntu,ubuntu,memtest,windows7.
and i have not changed anything or tried installing ubuntu again.!
anybody got idea how to fix this?
thanks in advance,
Giorgio

---

### Post by Bucky Ball on 2011-01-10
They are kernel updates. When the kernel updates it leaves the previous kernel there in case the new one breaks anything. You can boot in to the old one to try and fix.

The easiest way with grub2 is with this really neat tool I found the other day. You can hide the ones you don't want to see and more:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

To install, run these commands in a terminal, one at a time, hitting return after each:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```


Grub Customizer should now be in Applications >System Tools. If it's not do a
search for it in Ubuntu Software Centre or Synaptic Package manager and install again..

This little package really works a treat. ;)

---

