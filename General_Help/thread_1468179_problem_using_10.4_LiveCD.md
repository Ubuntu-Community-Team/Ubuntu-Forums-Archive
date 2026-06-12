---
title: "problem using 10.4 LiveCD"
date: 2010-05-01
forum: General Help
---

### Post by Rubi1200 on 2010-05-01
Hi,
I am trying desperately to get the new 10.4 LiveCD to work with no results.
It starts out then gets to the screen with the dots then a black screen then nothing.
I tried booting with the nomodeset parameter to no effect.
Hardware:
product: 82852/855GM Integrated Graphics Device
vendor: Intel Corporation
It is a Fujitsu-Siemens laptop (approx. 7 yrs old) with 1GB of RAM.
I have had no such issues with previous versions of Ubuntu.
If anyone has any ideas as to why this is happening or how I can work around it to actually boot into the new version, I would be very grateful.
Thanks in advance.

---

### Post by mikewhatever on 2010-05-01
This is a known issue according to Lucid's release notes.
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes](http://www.ubuntu.com/getubuntu/releasenotes/1004#Intel%208xx%20X%20freezes/crashes)

---

### Post by Rubi1200 on 2010-05-01
Thanks for responding so quickly. However, as a new user could you please tell me which option to add to the boot menu when I hit F6 before 10.4 starts?
I tried i915.modeset = 0 xforcevesa but it did not work. Any other options available or wait till the devs figure out another workaround?
Thanks.

---

### Post by mikewhatever on 2010-05-01
Actually, I've no idea how to load vesa on startup. In fact, my only experience with Intel's graphics was gma500, not as bad as yours, but also pretty horrible.

---

