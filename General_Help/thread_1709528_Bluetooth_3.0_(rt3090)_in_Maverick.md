---
title: "Bluetooth 3.0 (rt3090) in Maverick?"
date: 2011-03-18
forum: General Help
---

### Post by Interruptor on 2011-03-18
I am configuring Ubuntu on Impression ImPAD 1410 (Ukraine-based vendor) and it has RT3090 Network card. Which has Bluetooth 3.0 also. And I'm searching a way to make it work.
WiFi was perfectly recognised out-of-the-box, but bluetooth didn't even after installing 2.6.38-7.35~lucid1 kernel from PPA (yes, in maverick).
Also I've downloaded driver tar from official RaLink page, but didn`t find any bluetooth-related stuff, is it worth trying to compile?

Is there anyone who have bluetooth 3.0 working on ubuntu?

---

### Post by bugslayr on 2011-04-09
Hello Interruptor,
what version of the rt2806sta (rt3090 is an alias for it) driver is included in your kernel?
The version currently provided on the Ralink web page is 2.4.0.4 ... I know, the one which comes with Natty beta 1 is 2.4.0.0. So there may be some changes and it might be worth compiling and loading the driver.
Compiling the driver should not be a big issue - I had to do it a few years ago on a netbook ... as far as I remember, a "make" and "make install" did the trick ...
Please let us know, whether the new driver got BT 3.0 working!
Take care

---

### Post by Interruptor on 2011-04-09
I don't own that tablet, so I'll check it on Monday probably, thanks for your reply.

---

