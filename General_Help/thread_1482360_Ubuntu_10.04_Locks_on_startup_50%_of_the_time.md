---
title: "Ubuntu 10.04: Locks on startup 50% of the time"
date: 2010-05-13
forum: General Help
---

### Post by bgilbert on 2010-05-13
Hi,

I've experienced this problem with a distribution upgrade and then subsequently with a clean install of Ubuntu 10.04. Basically half the time that I boot up Ubuntu, it completely locks up with the following messages on screen (Sorry, I had to take a picture since it was locked up):

[[COLOR="RoyalBlue"]_Picture of Bad Boot_[/COLOR]]("http://picasaweb.google.com/GilbertW1/DropBox?authkey=Gv1sRgCJrDjrX94oidFA#5470814173301871458")

However, when it does boot correctly, it pauses for just a moment after displaying the above text, and then displays a few additional lines, after which it goes on to boot 'normally':

[[COLOR="RoyalBlue"]_Picture of Good Boot_[/COLOR]]("http://picasaweb.google.com/GilbertW1/DropBox?authkey=Gv1sRgCJrDjrX94oidFA#5470814512382276194")

The next lines show 'plymouth' and 'ureadahead' processes being killed. If these lines show up the boot continues normally, otherwise the boot process hangs at the first picture.

It is pretty frustrating to have to perform a hard restart during nearly every other boot, and the hangs seem almost completely random. Sometimes, it happens a couple times in a row, sometimes I can boot normally several times in a row. It also doesn't seem to be related to a cold start, versus a restart. Any help on this subject would be greatly appreciated.

Thanks in advance!
Bryan

---

### Post by bgilbert on 2010-05-14
Bump?

---

### Post by jeepinpete on 2010-06-01
I have the exact same problem.  One in ten boots will actually succeed.  I've been booting using the recovery option, then resume normal boot, then services start gdm.  I've yet to have the recovery option hang at the point.

---

### Post by T&amp;H on 2010-07-06
I have a similar problem with my machine except it looks like everything is going fine but the monitor suddenly goes to sleep and your hear the boot music. If you hit enter and your password it continues on in sound only but still no screen. If you reset two or three times the system come up without a hitch.
I am running:
AMD Athlon II X4 630 2.8Ghz quad-core
Gigabyte GA-MA785GM-US2H (mother board)
4 gigs of DDR2 800 (ram)
and the embeded video card of the mother board.

---

