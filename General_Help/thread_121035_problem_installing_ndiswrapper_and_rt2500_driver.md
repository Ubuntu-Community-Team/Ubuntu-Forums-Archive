---
title: "problem installing ndiswrapper and rt2500 driver"
date: 2006-01-24
forum: General Help
---

### Post by mankuan on 2006-01-24
hi all. 
as i was installing ndiswrapper with instructions from [here]("http://www.ubuntuforums.org/showthread.php?t=104539&highlight=version+repositories+outdated+update+current+ndiswrapper"), 
 i encountered the error:

[COLOR="Blue"]Can't find Kernel Sources in /lib/modules/2.6.12-9-686/build; give the path to kernel sources with KSRC=<path> to make[/COLOR]
after i ran fakeroot debian/rules binary-modules

anybody know what's wrong?

and how do i use the RT2500 drivers from [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page) ??

they dont seem to have an inf file included.

---

### Post by GeneralZod on 2006-01-24
Do a search for rt2500; I'm pretty sure there's a HOWTO here.  Long story short - the rt2500 chipset has decent open source drivers available, and so there's no need to use ndiswrapper in order to get them to work! :)

---

