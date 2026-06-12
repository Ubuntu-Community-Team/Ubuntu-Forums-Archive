---
title: "Performance for Netbook 10.10 on Toshiba nb205"
date: 2011-03-17
forum: General Help
---

### Post by jhargis1012 on 2011-03-17
Hello. I recently bought a Toshiba nb205 netbook (specs are Intel Atom 1.66ghz, integrated Intel Mobile 945GME graphics, 1gb ram). Ubuntu installed pretty cleanly on it. I think everything is working right out of the box, which is nice. At first I was experiencing the intermittent freezing problem described in this thread:

[http://ubuntuforums.org/showthread.php?t=1215665&highlight=performance+nb205&page=26](http://ubuntuforums.org/showthread.php?t=1215665&highlight=performance+nb205&page=26)

But after updating, I'm pretty sure the newer kernel version fixed it.

Anyway, the system still seems to be running pretty slow. Comparatively, Windows 7 Starter runs more smoothly on the other partition (I'm dual booting). I would have expected a performance increase with Ubuntu. Perhaps there is some tweaking that can be done to improve the performance?

---

### Post by 5149.5 on 2011-03-17
How big is your partition? Have you enabled swap space? I'm running the 10.10 netbook remix on an Aspire One with specs like yours and  my performance is better than W7 starter.

---

### Post by jhargis1012 on 2011-03-17
I started with a 100 gig partition for Ubuntu and a 10 gig swap space (I know that's ridiculously large, but I didn't at the time of install). Upon later reading, I saw a lot of people advising turning down the swappiness, so I set it to 10. Not sure if that's shooting myself in the foot.

---

### Post by blueridgedog on 2011-03-17
Is there an option for a restricted driver for the Mobile 945GME graphics?  System > Administration > Hardware Drivers...

---

### Post by Tijok on 2011-03-17
For the OP:

This is going to seem like a pretty silly question off the bat, but did you use the Ubuntu Netbook Remix? There is a fair amount of trimming and optimization that I've found to be very advantageous for Atom-based setups.

Otherwise, I second the check of drivers for graphics, wireless, and others, these are terrible culprits in low performance systems like this.

Best of luck!

---

### Post by jhargis1012 on 2011-03-21
Thanks for the responses. Yes, I did use Netbook Edition, and that was the version that was slow.

When you say check for drivers, do you just mean the proprietary drivers section there in the administration menu? I hit check and nothing came up in there, unfortunately.

As of right now, I've switched over to Lubuntu and it works awesomely. Very simple and smooth.

---

