---
title: "Ubuntu 11.10 booting time is about 40 sec."
date: 2012-01-08
forum: General Help
---

### Post by avdmys on 2012-01-08
I have acer-aspire-5750G with 1GB nvidia,core i5 second generation and 4 GB ram,With dual boot WIN7 and ubuntu 11.10. 

First when i power on the laptop the grub appears and when i choose to boot to ubuntu 11.10, the screen goes blank with a cursor blinking at the top and it stays like that for about 20sec-25sec and then i get the default plymouth with UBUNTU written on it and it takes about 15 sec after this for the ubuntu desktop to appear.

I have seen ubuntu booting in 10-12 sec so i was hoping to speed up by booting as well.:)

---

### Post by Mark Phelps on 2012-01-09
> **avdmys said:**
> I have seen ubuntu booting in 10-12 sec so i was hoping to speed up by booting as well.:)

Was that an Ubuntu 11.x version?

Asking because the LAST Ubuntu version that booted quickly on my PC was 9.10.  Version 10.x took longer, and version 11.x takes even longer.

Good Luck with your quest.

---

### Post by xyzzyman on 2012-01-23
I have an older Aspire 6930G w/Core2Duo 2.53Ghz and 4GB of RAM. Normal 5400RPM Hard drive. I can get it down to a 24 second bootchart, but when I have virtualbox drivers and all my start-up programs and indicator applets I am at 44seconds:

[[IMG]http://i.imgur.com/b8tebl.png[/IMG]](http://imgur.com/b8teb)

As you can see there's a stall with what seems like no activity for the first 10 seconds after grub, but what's actually going on is it's initializing all the hardware, then using a program called ureadahead that loads everything in one fell swoop (It'll auto rebuild its cache if you change kernels, upgrade daemon's, etc...). You can disable ureadahead but for most people and I believe in your situation you will wind up with actually longer boot times. 

If you had an SSD and optimize the boot process manually for just your system you can get down to 10-15 second boot speeds but is it worth a few hundred dollars to you?

---

### Post by avdmys on 2012-01-27
i hav posted my bootchart can someone look at it and see what can be done here please........
Thanks.
[http://imgur.com/zFHml](http://imgur.com/zFHml)

---

### Post by Tosho on 2012-03-07
my ubuntu 11.10 x64 boots for 1min and ~10sec.
how to speed up the boot and stop/remove some processes ?
could my encrypted home partition cause this ?

---

