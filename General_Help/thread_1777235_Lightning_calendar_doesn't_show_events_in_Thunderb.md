---
title: "Lightning calendar doesn't show events in Thunderbird"
date: 2011-06-07
forum: General Help
---

### Post by csmartdalton on 2011-06-07
I thought I'd ask since others must be having the same problem. I've tried twice on a fresh install of 64-bit ubuntu with Lightning/1.0b2 on Thunderbird/3.1.10. The lightning calendar works fine at first, but within a day it quits working completely. No events show up on the calendar, I get no reminders, if I create a new event, it doesn't show up, etc. The calendar is 100% empty and never gives any reminders. Has anybody been able no resolve this?

---

### Post by pqwoerituytrueiwoq on 2011-06-07
mine is working fine
thanks for saying something i had forgot to link lightening to my google calender on my desktop
tb must be open to give the event alert

---

### Post by cottfcfan on 2011-06-07
Where did you download your version of Lightning from?
Mine works perfectly, but I didn't use the one from "add ons"

---

### Post by csmartdalton on 2011-06-07
> **cottfcfan said:**
> Where did you download your version of Lightning from?
Mine works perfectly, but I didn't use the one from "add ons"

My ubuntu is 64-bit, and when I tried to install the one from add-ons it told me my os/thunderbird were incompatible. I had to download it from the 1.0b2 link here: [https://help.ubuntu.com/community/ThunderbirdLightning](https://help.ubuntu.com/community/ThunderbirdLightning)

---

### Post by cottfcfan on 2011-06-07
try using the one from here and see if it works any better.
[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/contrib/linux-x86_64/)

---

### Post by csmartdalton on 2011-06-07
I just uninstalled Thunderbird, put on a 32-bit deb, and installed the latest-and-greatest 32-bit lightning. Still nothing. Although, the 32-bit thunderbird knew all my old information which may be what's messing it up. How can you completely kill thunderbird and all the info it has  saved?

---

### Post by pqwoerituytrueiwoq on 2011-06-07
rm -r ~/.thunderbird

---

### Post by csmartdalton on 2011-06-07
> **pqwoerituytrueiwoq said:**
> rm -r ~/.thunderbird


That did it. Now my calendar is working again. We'll see if it stays. For reference, here are the steps I took in 64-bit ubuntu:

sudo apt-get purge thunderbird
rm -rf ~/.thunderbird
wget [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb)
sudo dpkg -i --force-all thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb
Tools > Add-ons > Install lightning

---

### Post by cottfcfan on 2011-06-07
Can i just ask. Why did you use Thunderbird from sourceforge, instead of the one from the repos?

---

