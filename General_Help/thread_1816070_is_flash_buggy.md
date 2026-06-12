---
title: "is flash buggy?"
date: 2011-08-01
forum: General Help
---

### Post by chedderslam on 2011-08-01
I installed 11.04 desktop on a  vmware player vm to use as a pausable browser based game environment.  Tried Gemcraft Labryinth and it played very buggy.

Is buggy flash player a known issue on Ubuntu, or is it something I can troubleshoot?

Thanks!

---

### Post by ottosykora on 2011-08-01
I would not say that flash is buggy, but there might be some incompatibility at the moment somewhere.

I was running 10.10 with firefox and flash and all was working.

I updated to 11.04 and it was night mare. Browsers did crash all the time and particularly any kind of flash did crash within seconds regardless of browser I did use.

The computer has 64bit proc, so today I installed 64bit ubuntu 11.04 and so far all browsers and all versions of flash do work very stable.
No idea so far what is incompatible in the 11.04 as far as flash is concerned.

---

### Post by CatKiller on 2011-08-01
> **chedderslam said:**
> Is buggy flash player a known issue on Ubuntu

Flash is buggy everywhere.

---

### Post by uRock on 2011-08-01
If you install Flash using the [Firefox Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") addon, then your problems will go away.

---

### Post by ninjaaron on 2011-08-01
> **urock said:**
> if you install flash using the [firefox flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/") addon, then your problems will go away.

+10^9

---

### Post by ottosykora on 2011-08-01
>If you install Flash using the Firefox Flash-Aid addon, then your problems will go away.<


to nice to be true, 

I tried many times, the offered versions, but nothing, on the 11.04 32bit, it was crashing any time and under any situation with any browser.

It seems to be also some kind of compatibilty problem with some hardware or so, as on my pure intel based machine (M520 proc, HD i5 graphic) all works only from true 64bit ubuntu, simply crashing after few secs on 11.04 32bit on this hardware. On other hardware it works fine however.

---

### Post by uRock on 2011-08-01
> **ottosykora said:**
> >If you install Flash using the Firefox Flash-Aid addon, then your problems will go away.<


to nice to be true, 

I tried many times, the offered versions, but nothing, on the 11.04 32bit, it was crashing any time and under any situation with any browser.

It seems to be also some kind of compatibilty problem with some hardware or so, as on my pure intel based machine (M520 proc, HD i5 graphic) all works only from true 64bit ubuntu, simply crashing after few secs on 11.04 32bit on this hardware. On other hardware it works fine however.

Sounds like your problem has nothing to do with Flash. Have you started a thread on your issue(s)?

---

### Post by ottosykora on 2011-08-01
>Sounds like your problem has nothing to do with Flash. Have you started a thread on your issue(s)?<

yes somewhere I did, but it looks like it is not so simple resolvable.
Flash was in any version running max 3secs on 32bit and the hardware in question.
(standard kernels and -pae)

Taking now full 64bit ubuntu and what ever flash offered, it gives stable pictures.

But you are right, this is not a simple flash buggy or so, it is some general compatibility issue as on 10.10 all did work best, on 11.04 then not until I removed all and installed 11.04 64bit fresh.

In many experiments I could verify all by running this and that from life CD, therefore rather insulated system, but all symptoms were exactly same.
Used the flash aid to pick what ever flash versions offered, but no help, did not work at all.

As on an very old computer with olde celeron all works fine, I assume there might be some lack of support for the intel graphic in the 32bit 11.04 or so. Or at least this would sound most probable reason.

---

