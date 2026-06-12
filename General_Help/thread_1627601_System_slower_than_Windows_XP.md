---
title: "System slower than Windows XP?"
date: 2010-11-21
forum: General Help
---

### Post by saverio.miroddi on 2010-11-21
I've installed Ubuntu Maverick on a testing machine, a Samsung N510 (Atom N280/2 GB RAM), and I've been quite surprised that I haven't been able, due to slowness, to reproduce MPEG2/DIVX videos (using VLC).
When I subsequently installed Windows XP, the videos were playing fluidly.

Now, I also noticed, although this may potentially be biased, that the overall responsiveness of the system is a bit slower than when I use Windows XP (drawing speed of objects).
I remember having the same feeling I switched (years ago) entirely from Windows to Ubuntu.

Why is video decoding so much slower on Ubuntu?

Providing that the second point (desktop system speed) is not biased, is gnome inherently slower than Windows XP's GUI? Why, if so?

---

### Post by dcstar on 2010-11-21
> **saverio.miroddi said:**
> I've installed Ubuntu Maverick on a testing machine, a Samsung N510 (Atom N280/2 GB RAM), and I've been quite surprised that I haven't been able, due to slowness, to reproduce MPEG2/DIVX videos (using VLC).
When I subsequently installed Windows XP, the videos were playing fluidly.
.......

Did you install the Netbook edition?

---

### Post by clhsharky on 2010-11-22
saverio.miroddi

Ubuntu is a modern OS with a compositor same with Vista and Win 7, XP does not.
Turning off Compiz will give boost with some apps.
What video chip do you have?


Sharky

---

### Post by asmoore82 on 2010-11-22
check the output of `lspci` to see if you have the dreaded "Poulsbo" graphics chipset.

If so, read this: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

---

### Post by drewsus on 2010-11-22
> **clhsharky said:**
> saverio.miroddi

Ubuntu is a modern OS with a compositor same with Vista and Win 7, XP does not.
Turning off Compiz will give boost with some apps.
What video chip do you have?


Sharky

My maverick install runs just as smooth if not smoother than XP with my custom compiz profile. 
My stats are not as good as his netbooks (acer aspire one with 1gb ram)

---

### Post by saverio.miroddi on 2010-11-22
> **dcstar said:**
> Did you install the Netbook edition?

The version was actually a Xubuntu - I'm quite sure I disabled compiz. I'm going to reinstall a plain Ubuntu to see if it makes any difference.

---

### Post by dcstar on 2010-11-23
> **saverio.miroddi said:**
> The version was actually a Xubuntu - I'm quite sure I disabled compiz. I'm going to reinstall a plain Ubuntu to see if it makes any difference.

There is a reason Ubuntu specifically create a version for netbook hardware.

---

### Post by asmoore82 on 2010-11-24
> **saverio.miroddi said:**
> Providing that the second point (desktop system speed) is not biased, is gnome inherently slower than Windows XP's GUI? Why, if so?

One issue is that Linux attempts to enforce a separation of kernel space and user space. This concept is explained here: [http://en.wikipedia.org/wiki/Ring_%28computer_security%29](http://en.wikipedia.org/wiki/Ring_%28computer_security%29) . But this security comes at a price. A dead-simple, sure-fire way to increase the "snappiness" of a GUI is to simply run all of the code at the lower "OS" level. In a nutshell, this is what windows does. But, as we all have no doubt experienced first-hand, this means that any simple misbehaving GUI app in user space can more easily bring the whole system down!

Another point of interest, is that the whole "X" Unix GUI architecture is just plain old. But this is one of those "feature not a bug" scenarios. Software design that old that is still in widespread use must have been doing something very right at some point. X windowing systems adhere to a client/server model that constitutes another layer of separation. Modern implementations undercut this with direct rendering as much as possible, but the underlying client/server architecture still remains for compatibility and its usefulnesses, such as network transparency.

These 2 points combined mean that even when optimally configured, the Linux GUI can *feel* slower or less responsive; while overall number-crunching performance remains unaffected. When not optimally configured, on the other hand, Linux seems to have "can do" attitude. Meaning that it can and will resort to doing GUI operations in very inefficient ways, if that's the only way to make it work. In other words, falling back to a generic VESA video driver; or falling back to rendering video pixel-by-pixel on a bitmap display.

A quick google of your Samsung model brings results mentioning the nVidia Ion chipset. If this is truly the case, you will unfortunately need the not fully open-source nVidia driver modules to get the most out of your hardware. My wife's laptop is an Intel Atom/nVidia Ion combination. I was pleasantly surprised at its performance, keeping in mind of course that nothing will fully overcome the limitations of an ultra low power CPU. At the time we got it however, it was almost completely unusable with the open "nouveau" drivers - I need to revisit this again soon.

---

### Post by Hostie on 2010-11-24
thanks for the post asmoore.  been wondering about this with my own tinkering.

---

### Post by saverio.miroddi on 2010-11-27
> **dcstar said:**
> There is a reason Ubuntu specifically create a version for netbook hardware.

It unfortunately didn't make any difference compared to Xubuntu.
I have a feeling that DVDs playback stutters a bit less (although the playback is not smooth anyway) - but that may well be just perception.
I found at least one DVD that stutters visibly though - and that's objective.

I've setup the closed source nvidia drivers as suggested.
The player is VLC.

So definitively I'm not able to play smoothly DVD on the system under Ubuntu, while I can perfectly do it on Windows XP.

Just for the records, the system is an Nvidia Ion:
- Intel Atom N280 / 1.66 GHz
-   NVIDIA GeForce 9400M

@asmoore: thanks for the detailed post - it's been very informative.

---

