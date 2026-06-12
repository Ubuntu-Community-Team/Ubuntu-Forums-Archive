---
title: "Ubuntu and Rt2780: The Endless Saga"
date: 2010-04-29
forum: General Help
---

### Post by camberiu on 2010-04-29
Q: Why Ubuntu does not become a mainstream OS? 
A: Because it is simply not ready for mainstream.


OK folks, the RT2780 chipset is one of the most popular wifi chips out there (if not the MOST popular). However, wifi adapters based on the RT2780 chipset have not worked out of the box with Ubuntu since version 9.10. I did the blacklisting fix while on version 9.10 and everything worked fine. Now that I've upgraded to version 10.04, the same issue came bak witha  vengeance, and the blacklisting fix won't work anymore.
I find it incredible that a well documented bug that affects a widely available piece of hardware has existed since version 9.10 and it has only gotten worse with time. This is the kind of problem that ensures that Linux will never replace Windows as a mainstream operating system. Here we are will all the buzz surrounding the release of 10.04 and no progress has been made on this issue. Really sad indeed.

---

### Post by camberiu on 2010-04-29
I meat to say RT2870. Sorry for the typo.

---

### Post by mikeRimex on 2010-05-08
EXACTLY the same problem. 

I figured since my RT2870 WiFi dongle worked in Karmic (after blacklisting rt2800usb) that it should work out of the box in Lucid (or at least with the same tweak). 

I gave up after about 6 hours of trying to get it working. It seems the bug sits a bit deeper.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543836)

Out of frustration I reinstalled Karmic. :-x

---

### Post by myjess on 2010-05-09
Other bug listed by me on the bugs site. Other bug that I reference in my bug is also on the site and seems to do some workaround.

---

