---
title: "Persistent LiveCD?"
date: 2011-01-07
forum: General Help
---

### Post by OmegaVesko on 2011-01-07
I've been looking into lightweight Ubuntu distros for my old desktop PC (15" CRT, 900MHz singlecore, 256MB RAM), and so far Lubuntu definitely seems the most promising.

Until now I've been using Puppy Linux as a LiveCD, because it has the ability to run off a read-only disc, but still save any changes and files into a pupsave file on any of the PC's hard drives.

From my past experience with installing Ubuntu on USB sticks, I know this is also possible on Ubuntu, with a casper-rw file. However, the PC in question can't boot off a USB stick (It shows the option in BIOS, but it doesn't work).

I don't have the ability to install to HD, since I don't have the permission to create a new partition. So, my question is: **Is there any way to make a Lubuntu LiveCD persistent?** From what I've seen, the easiest option would be creating a casper-rw on a location other than root, but I haven't the slightest on how to do that.

---

### Post by OmegaVesko on 2011-01-07
Update: I think the "Using a Loopback File" section of [this tutorial]("https://help.ubuntu.com/community/LiveCD/Persistence") should work. What do you think?

---

### Post by cavalier911 on 2011-01-07
Try PloP boot manager burned to a cd, with it's USB driver you may be able to boot your Ubuntu persistant USB key install.
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by C.S.Cameron on 2011-01-07
> **OmegaVesko said:**
> Update: I think the "Using a Loopback File" section of [this tutorial]("https://help.ubuntu.com/community/LiveCD/Persistence") should work. What do you think?

Both the casper-rw on USB and the loopback should work.
With 10.10 I think you have to hit either shift or tab when booting to get to the page where you hit F6 and type " persistent", (note the space before persistent).

Edit:
The plop option is also a good one. Running off USB is much faster than off CD.

---

