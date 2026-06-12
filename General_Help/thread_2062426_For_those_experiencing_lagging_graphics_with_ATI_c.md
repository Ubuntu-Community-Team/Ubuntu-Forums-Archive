---
title: "For those experiencing lagging graphics with ATI cards."
date: 2012-09-24
forum: General Help
---

### Post by sienile on 2012-09-24
I recent Ubuntu update has caused a performance issue with my (and most likely many other's) ATI graphics card. This issue is only present with the proprietary drivers downloaded from ATI's site. To solve the problem, you must revert to the repository drivers until either Ubuntu or ATI Catalyst is updated.

Here's how you do it:
```
sudo apt-get install fglrx fglrx-amdcccle

sudo aticonfig --initial
```Then reboot and you're done.

---

### Post by QIII on 2012-09-25
Umm...

That installs and initializes the  *proprietary*  ATI Catalyst driver available in the Ubuntu repo at the time of the version release.  If you are using Precise, that would be the ATI 12.4 Catalyst driver.

The Radeon driver is the open source one.

---

### Post by uRock on 2012-09-25
I've had the best experience by installing the latest driver for my card from ATI.

---

### Post by sienile on 2012-09-27
Didn't know those were proprietary drivers, I'll change the post.

The drivers that I was referring to giving trouble were the ones downloaded from the ATI site. It may only affect some cards, such as my Radeon 2600 Pro. The update on the 23rd caused the lagging.

---

