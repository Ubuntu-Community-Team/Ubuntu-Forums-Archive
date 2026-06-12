---
title: "Apollo CLE266 on OpenChrome?"
date: 2012-10-04
forum: General Help
---

### Post by DanStamp on 2012-10-04
Hi all,

I've got an ongoing problem which I'm wondering if you can help me with.  I have acquired an old Point of Sale J2 550 machine.  It's an all-in-one machine with a touchscreen and an LED on the back for use within a shop.  My plan is to use said machine in a shop with some custom software which I've already written most of.

With it being so old, I had trouble getting Ubuntu 12.04 installed (with it being non-PAE), and even when I did manage to get the operating system installed, it was frightfully slow, so I ended up reverting to 10.04.3 which runs well enough for the job I'm wanting it to do.

The only problem I'm left with, is that I can't seem to get the native monitor built into it to run on the built in graphics card.  I know the chipset is a "Via technologies inc VT8623 [Apollo CLE266] integrated castlerock graphics (rev 3)" and I understand that should run on the OpenChrome driver, which after forcing it into creating an xorg.conf file, i verified it was doing.

```
Driver      "openchrome"
VendorName  "VIA Technologies, Inc."
BoardName   "VT8623 [Apollo CLE266] integrated CastleRock graphics"
BusID       "PCI:1:0:0"
```The problem I'm left with is that as soon as graphics are loaded my monitor switches itself off and stays black.  Pressing ctrl alt and f1 to switch to a terminal gives me a massively glitchy screen, mostly red in colour.

Here's a link to my xorg.conf file in the hope that that'll help give some insight:
[https://dl.dropbox.com/u/956557/xorgconf](https://dl.dropbox.com/u/956557/xorgconf)

Any ideas on how I can get it working?

If any more information is required let me know, any suggestions would be very much appreciated though as its been bugging me for weeks now.

Oh, and incase it wasn't obvious, I've actually got a secondary monitor plugged in, which is how i've been able to get this information here.  I also know there isn't a hardware fault, as the hard drive it came with had a very early version of knoppix installed with the following xorg.conf which worked on that: [https://dl.dropbox.com/u/956557/XF86Config-4](https://dl.dropbox.com/u/956557/XF86Config-4)


Thanks, 

Dan.

---

### Post by gordintoronto on 2012-10-04
Via graphics are very old, very cheap, poorly supported in any modern OS.

Several years ago, I bought a vido card on eBay for $10, and it was much, much better than the Via graphics on the computer I was using at that time.

If there's any possibility of using a separate video card, that would be a better option.

How old is the J2? I think I can buy a vastly superior computer for under $200. If you're using this in a business, that should be a noise-level expense.

---

### Post by DanStamp on 2012-10-05
Thanks for the reply.  And Yeah I fully understand that they're really old, and if I can't get it working, replacing it completely is exactly what we'll have to do.  The problem the business is just starting up so funds are tight at this precise moment in time.

One solution I might have found yesterday is reverting all the way back to Ubuntu 8.04.4  It seems like there are at least drivers available for the via device on that machine, and its not as if it needs the latest and greatest software.

Those are here if anyone's interested.  I'll keep you posted as to if this works. [http://www.viaarena.com/ViaDisplayDrivers.aspx?PageID=1&OSID=59&CatID=3640&SubCatID=101&lang=en-GB](http://www.viaarena.com/ViaDisplayDrivers.aspx?PageID=1&OSID=59&CatID=3640&SubCatID=101&lang=en-GB)

---

