---
title: "Weird graphics problem - Ubuntu keeps crashing"
date: 2009-07-21
forum: General Help
---

### Post by dave_i on 2009-07-21
Hi everyone,

I've been having this weird problem with Ubuntu for a week or so now. I can startup the computer fine, but after I log in, I frequently (pretty much every time I use the computer) find that the system crashes. I am able to move the mouse pointer, but unable to click on anything. I get weirdly distorted graphics as well, and I end up having to press alt+sysreq+k to log out of gnome. When I log back in, it works fine for a while, then the same thing happens. 

I've noticed that typing certain words into firefox's awesomebar crashes the system instantly, which is really weird. It's also been acting strange with my USB wireless adapter and wireless mouse dongle - occasionally either of them stops working, but works fine if I move it to a different usb socket.

My gut feeling is that this is a graphics / general motherboard problem. I've noticed that the GPU is running at 60deg+, even when just using firefox, although other people with the same adapter have noticed this and it didn't seem to be a problem for them.

My system is:

600W PSU
Athlon 64 x2 dual-core 2.7GHz,
Asrock K10N78-1394 with onboard nVidia 8200 (I'm using the proprietary driver)
4G DDR2
500Gb SATA HD
Ubuntu 9.04 64bit


Any ideas? I think I may see about getting this M/B replaced, as it's only a few weeks old.

---

### Post by Janeway on 2009-07-21
Hi,

the GPU running at 60+ degrees is normal.

I had a similar graphics problem with my notebook which has an ATI Graphics Adapter using Ubuntu 9.04. I think the problem is caused by the new ubuntu kernel 2.6.28 in combination with the proprietary driver.

You should make sure you have the newest version installed, or some googling should show if there is a NVidia driver for this kernel.

However, it might be better to use the normal driver or an older version of ubuntu. New kernel with new drivers often causes problems.

Best regards
Janeway

---

### Post by dave_i on 2009-07-22
Thanks for the reply - as far as I can tell, it's worked perfectly. I had a few problems installing the new driver - I had to remove the old nvidia kernel modules before reinstalling the new driver, but so far I've had no crashes :).

---

