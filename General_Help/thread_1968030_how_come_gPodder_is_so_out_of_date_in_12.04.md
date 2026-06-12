---
title: "how come gPodder is so out of date in 12.04?"
date: 2012-04-28
forum: General Help
---

### Post by nrundy on 2012-04-28
I thought new OS releases were supposed to update applications to the latest release or at least close to the newest release. gPodder is way out of date. Its at 2.20 in 12.04 and the latest is 3.10.

Anybody know why?

---

### Post by PeterP24 on 2012-04-28
Um, I guess it depends if someone is maintaining the package or not for .deb version ... .

---

### Post by Cheesemill on 2012-04-28
gPodder 2.20 was released on 18th Feb 2012.
gPodder 3.10 was released on 27th March 2012

The [FeatureFreeze]("https://wiki.ubuntu.com/FeatureFreeze") date for Precise was before gPodder 3.10 was released, so only version 2.20 will be available. Apart for bug fixes (if any) this is the most up to date version that will be in the Precise repositories.

---

### Post by nrundy on 2012-04-28
thanx for answering guys.

---

### Post by sgage on 2012-04-29
I had a look at the gpodder website (gpodder.org), and found this tid-bit:

> Version 2.20.1 (released 2012-02-18, source tarball) is the latest version in the 2.x series. gPodder 2 contains MP3 player sync and support for Maemo 4 and 5. It will not receive new features, only occasional bugfixes (if any). It is recommended that you use gPodder 3 except if you still need Maemo 4 or Maemo 5 support.

The gPodder 3 releases do not contain MP3 player sync yet. When we add MP3 player sync support to 3.x, we'll update the Ubuntu PPA. Learn more about device sync in 3.x. 

Their ppa (ppa:thp/gpodder) currently has the same version as the official Ubuntu repos.

---

### Post by fernandohleme on 2012-09-14
Unfortunately the package has not been updated yet and gpodder just lost its youtube download feature. I don't know if the folks at google did something diferent but I couldn't download my stuff from there today.

Also the PPA provided by launchpad (weirdly called gwibber) is being ignored by apt-get and I found no .deb available around.

So, I got stuck in the cold.

---

