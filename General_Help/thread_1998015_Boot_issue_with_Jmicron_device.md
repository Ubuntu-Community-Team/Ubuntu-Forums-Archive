---
title: "Boot issue with Jmicron device"
date: 2012-06-06
forum: General Help
---

### Post by Exomancer on 2012-06-06
I have a AMS Venus T5J DS-2350J external eSATA hard drive enclosure which uses a JMicron 393 port multiplier.  I had Ubuntu 11.10 64 bit on the system from a clean install and I never had an issue with the unit.  I did a clean install of Ubuntu 12.04 64 bit and now I have problems when I boot my system.

Whenever I boot the system, it does a search for any attached drives.  With 11.10 it would find one drive and then load the system and any associated drivers.  I never had a problem with it just searching and searching like it does now.  This slows down booting time tremendously.  While it is doing this the drives in the box are making a clicking noise. Currently it no longer finds that one drive till the OS is loaded.  Again once booted, it works just fine and the clicking stops. 

I checked with the unit manufacturer AMS and they said that it's probably not the unit and that JMicron has not released any new drivers.  They said that this was a Ubuntu issue.

Can you give me any guidance as to what is happening?  Why did it work flawlessly under 11.10 and now not under 12.04?

---

### Post by Exomancer on 2012-10-13
On consultation with AMS, this turned out to be a bad power supply, which when replaced, fixed the issue.

---

