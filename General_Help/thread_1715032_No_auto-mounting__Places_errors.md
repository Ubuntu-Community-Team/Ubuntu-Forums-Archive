---
title: "No auto-mounting / Places errors"
date: 2011-03-26
forum: General Help
---

### Post by GenericBox on 2011-03-26
After latest Ubuntu update, my drives are not automatically mounting  (CD, HDD, USB) - there is no Trash button, and even if there was, when I  click "Computer", "Network" or "Trash" from the Places menu, I get this  error:

[Could not display "computer:".] Nautilus cannot handle "computer" locations.

It is driving me insane. Noone on IRC responds and Google is no help at all.

I am a newb. 

Running 10.10 and issue is on both .28 and .27 kernels (haven't tried earlier kernels).

It was working fine yesterday, so I don't think kernel issues are at fault.

---

### Post by GenericBox on 2011-03-26
SOLVED.

It appears to be an issue with glib and libgio in /usr/local/

Following advice from: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889)

I removed the gio and libg folders from /usr/local/ and all files of the same name. (I backed them up however in case).

Rebooted, and USB's automounted again, and I can access Places.

[quote=David K Rose]
I had this problem in Ubuntu 10.10 .  The problem seems to arise after  you install glib.  It's inconvenient, because not only do I not get a  nautilus session from Places>Computer, but various drives -  especially usb sticks - fail to auto-mount.  I don't of course know the  real cause, but here's a work-around that gets rid of the problem.  The  culprits are /usr/local/lib/libgio-2.0.so.0 & libgio-2.0.so.0.2899.0 .  The 1st of these is a symbolic link to the 2nd. Create a folder /usr/local/lib/preventNautilusCrash  and put these two files there along with a README explaining why.  Who  knows: maybe they are needed, so don't destroy them.  Anyway, this fixed  the nautilus problem for me.
[/quote]

---

