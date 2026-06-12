---
title: "HP LaserJet and netowork scanning"
date: 2011-11-02
forum: General Help
---

### Post by malcmail on 2011-11-02
After 3 days of trying I'm hoping someone can help. I have a small server type machine running lubuntu (I think its 10.04 but can't quite remember). IT has a LaserJet 3050 all in one attached and works perfectly.

Its shared with CUPS across my network and printing is again working fine. What I am trying to get it to do, and cannot for the life of me, is get my Ubuntu (10.04) box to access it over the network to scan. I've tried the instructions here ([https://help.ubuntu.com/community/ScanningHowTo#server](https://help.ubuntu.com/community/ScanningHowTo#server)) but no joy. Anyone got any experience of this and any tips on how to get it working?

Cheers

---

### Post by malcmail on 2011-11-02
*bump*

---

### Post by amjjawad on 2011-11-03
Hi there,

I don't have a direct answer to your question but I suggest to pop up on IRC channel and ask there. The team will help you with your question in no time :)

All the information you need will be here: Lubuntu One Stop Thread - check my signature.

Check "Contact Us".

---

### Post by malcmail on 2011-11-03
I'll give that a go then - cheers.

---

### Post by amjjawad on 2011-11-03
> **malcmail said:**
> I'll give that a go then - cheers.

Good luck and please don't forget to update your thread (this one) in case you got an answer :)

---

### Post by Guilden_NL on 2012-01-20
A quick work around is to scan the images to a SD-MMC card.  I have a 8GB card that I scan to, and then walk to (spin in my chair actually) the system I want the files copied to.

Old fashioned sneakernet.

---

### Post by malcmail on 2012-01-25
> **Guilden_NL said:**
> A quick work around is to scan the images to a SD-MMC card.  I have a 8GB card that I scan to, and then walk to (spin in my chair actually) the system I want the files copied to.

Old fashioned sneakernet.

Haha. Sadly can't pull that one off.

For anyone who chances upon this thread though I realised there's another way to do it of course.

ssh -X <ipaddy-of-PC-with-scanner> xsane.

Not perfect and doesnt always behave like it would if I was using the attached PC but does the job :)

---

### Post by amjjawad on 2012-01-27
Thanks for updating us and hopefully soon you will be able to find a better way :)

---

