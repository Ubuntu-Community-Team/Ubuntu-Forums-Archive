---
title: "LiveCD - ran update manager, got upgraded kernel version.  How can I test it?"
date: 2009-08-30
forum: General Help
---

### Post by jimmy the saint on 2009-08-30
I have a trendnet wireless card that is a complete pain in my rear.  I spent hours (too many of them) trying to get the drivers to work using .debs, compiling them myself and following 3 different guides.  no dice.  I saw a few reviews for the card that said it works out of the box in Jaunty, but only a after an upgraded kernel was pushed down.  I want to test this before I do a fresh installation on my server.  How can I use the kernel upgrade with the LiveCD?  It upgrades, but then I have to restart... which loses the upgrade!

Thanks

---

### Post by P4man on 2009-08-30
perhaps there is another way, but why not create a live USB stick (persistent) and upgrade the kernel there?

---

### Post by jimmy the saint on 2009-08-30
Does that USB creator pump out a persistent LiveUSB?  I thought it was just a live CD on a stick?

Also, thanks for the quickest response I've ever gotten in the General Help section!!

---

### Post by P4man on 2009-08-30
usb creator can make persistent usb sticks, but there is a bug with sticks > 4GB (or persistence files larger than ? 2? GB, not sure). use a small stick and/or persistence file of 1GB or less, and you should be ok.  Further more, the "ubuntu" user is recreated on each boot, so it may seem not persistent, but that wouldnt affect the kernel.

As for the speedy response, thats just luck :)

---

### Post by jimmy the saint on 2009-09-04
I appreciate your help.  Just an update on the situation. I fully intended to use your method to figure out this problem.  When I finally had a chance a few days later, the wireless card simply decided to start working.  I have no idea why, how or what happened.

---

