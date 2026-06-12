---
title: "Laptop touchpad doesnt switch screens dual monitor"
date: 2010-05-28
forum: General Help
---

### Post by caradeporra on 2010-05-28
Setup:
Ubuntu 10.04 recently upgraded from 9.10
Dell Precision m6300
4G RAM
Core 2 Duo
Dual Monitor with laptop=screen0 monitor=screen1
external mouse and keyboard

Issue:
In both 9.10 and 10.04 (I am just now trying to solve the issue) the setup works great, but not flawless.  External mouse and keyboard work with no issue.

The touchpad mouse on the laptop, however, will not switch from screen1 to screen0.  It works fine on either screen and will go from screen0 to screen1, just will not return.  One has to hook up an external mouse to get the cursor back onto the laptop screen0.

Ideas?

---

### Post by dougalkerr on 2010-05-28
You might have to go looking for an up-to-date driver for the touchpad or perhaps try looking to see if the Alps driver program has been installed in Synaptic. At least I think this is where to look.
Others with more technical knowledge will no doubt correct me.
I installed the program 'hardinfo' to tell me exactly what all my hardware was. It may help identify things for you.

---

### Post by caradeporra on 2010-05-31
I could not find anything useful in Synaptics or driver updates.  Any other ideas?

---

### Post by k0d3g3ar on 2011-01-28
Sorry for digging up an old thread, but I'm about to upgrade Ubuntu 9.10 to 10.10 on my Dell M6300 after I upgraded the RAM from 4GB to 8GB.  I'm wanting to go with the 64 bit edition to get max ram support, but wanted to know if you encountered any driver issues with this machine and the 64 bit Ubuntu edition.   I run the Intel Wifi card in it, and drive 2 x 24" monitors off the back (using the proprietary NVidia drivers) - one in the DV port and one in the VGA port.  Works great with 9.10 32 bit and a hacked xorg.conf.  But I really want to take advantage of the extra memory, particularly for VirtualBox instances.

I realize you posted your intention to upgrade back in early 2010, so I was hoping you might be able to let us know how this all went in the end for you.

Thanks
k

---

### Post by caradeporra on 2011-01-31
After upgrading to 64bit 10.10 this issue has been resolved.  I am guessing an updated driver going into 10.10.

All I did was backup my Home directory and once I installed 10.10 64 bit I extracted it and replaced the newly created Home directory with mine.  Works like a charm.

---

### Post by drewsus on 2011-01-31
> **k0d3g3ar said:**
> Sorry for digging up an old thread, but I'm about to upgrade Ubuntu 9.10 to 10.10 on my Dell M6300 after I upgraded the RAM from 4GB to 8GB.  I'm wanting to go with the 64 bit edition to get max ram support, but wanted to know if you encountered any driver issues with this machine and the 64 bit Ubuntu edition.   I run the Intel Wifi card in it, and drive 2 x 24" monitors off the back (using the proprietary NVidia drivers) - one in the DV port and one in the VGA port.  Works great with 9.10 32 bit and a hacked xorg.conf.  But I really want to take advantage of the extra memory, particularly for VirtualBox instances.

I realize you posted your intention to upgrade back in early 2010, so I was hoping you might be able to let us know how this all went in the end for you.

Thanks
k

FYI - Ubuntu 32-bit will recognise and use 3GB+ RAM (and is enabled by default - so this next link is just for your reading pleasure):
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

