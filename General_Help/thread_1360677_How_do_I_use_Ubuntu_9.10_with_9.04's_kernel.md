---
title: "How do I use Ubuntu 9.10 with 9.04's kernel"
date: 2009-12-21
forum: General Help
---

### Post by Nightstrike2009 on 2009-12-21
I've had enough waiting fot the Huwai 3g modem fix for ubuntu 9.10 which never seems to happen, the connection to the internet is no longer possible on 9.10 with this type of 3g USB modem, though it was in 9.04.

This situation is in my opinion a farce on canonicals point and very damaging to the laptop / notebook market in which it does strongest, it has already cost ubuntu converts as I promoted it to friends only to have this stupid and critical flaw preventing them from using the net (Used my Orange, O2, T-Mobile & vodafone). Ubuntu 9.10 should still be in beta and not final release. 

I have heard the solutions are use 9.04 instead (easiest) or what I have heard works too *to tear the kernel out of Ubuntu 9.10 and replace it with the one from 9.04* does anyone know how i would do this?

---

### Post by Linux_junkie on 2009-12-21
Hello, 

Just for the record I'm using a mobile broadband device from T-mobile on Ubuntu 9.10 (karmic) and it works very well.  Once I discovered that to get it to work I had to eject the device as a cd-rom on the desktop then network manager picks it up as a modem.

By the way my mobile broadband device is a ZTE modem.

Linux_junkie

---

### Post by Nightstrike2009 on 2009-12-21
> By Linux_junkie: By the way my mobile broadband device is a **ZTE modem**.

> By Nightstrike 2009: I've had enough waiting fot the **Huwai 3g modem** fix for ubuntu 9.10 which never seems to happen

That would be why it works its not an HUWAI modem many linux users have problems connecting to the internet with 9.10 not just myself. 

I do get your point but the point also must be made that all major 3G USB modems should work with Ubuntu (especially as they did on 9.04 and bug was posted to devs before it was released and not fixed) as thats the easiest way to get your laptop/notebook on-line on the move.

Anyhow back to subject > ...to tear the kernel out of Ubuntu 9.10 and replace it with the one from 9.04 does anyone know how i would do this?

---

### Post by snowpine on 2009-12-21
Every Ubuntu kernel is available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by 3rdalbum on 2009-12-21
> **Nightstrike2009 said:**
> That would be why it works its not an HUWAI modem many linux users have problems connecting to the internet with 9.10 not just myself. 

Ejecting the fake CD-ROM seems to work fine for me. I have an E160G which is the same brand as yours.

---

### Post by sandy8925 on 2009-12-21
Using a kernel from an older release might be a bad idea. Better still see which kernel version supports your modem and compile that version, or see if you can get linux drivers for your modem from somewhere.

---

