---
title: "Really Slow Ubuntu-Help please"
date: 2010-09-28
forum: General Help
---

### Post by AustenB on 2010-09-28
So my Ubuntu is really, really slow...I think it's because it's not recognizing how much memory I have (2 Gig Pentium Dual Core).  I could possibly not have the right driver.  I'm using 9.10 Ubuntu on an Acer Aspire 4730Z.

If someone could direct me, I'd really appreciate it.  Also if you could tell me how to post any specs you might need to help, please do.

I would have searched the forums for people with a similar problem, but my Ubuntu is too slow (hah).

---

### Post by mikewhatever on 2010-09-28
Applications->Accessories->Terminal.
Please post the outputs of the following commands:

free -m

df -h

top

---

### Post by AustenB on 2010-09-28
Sorry, I posted before I updated load.  My computer seems a bit faster after updating (still not as fast as it should be though), and I decided I'll upgrade to 10.04 (hope it's a good idea...).

I'll post the results of those commands after I've upgraded if I still have this problem (assuming I don't accumulate worse problems hah).

---

### Post by HermanAB on 2010-09-29
Hmm, applying updates to a broken system is almost guaranteed to cause an even bigger mess...

If a Linux system is not working properly, it is usually caused by some mindless zombie process doing something descpicable in a dark corner of the kernel.  The way to find these miscreants, is with 'top' and then put them out of their misery with 'kill'.

If nothing seems out of order but it still runs slow, the problem could be due to a network configuration issue, which you can investigate with 'ping', 'dig', 'ifconfig' and 'route'.

---

