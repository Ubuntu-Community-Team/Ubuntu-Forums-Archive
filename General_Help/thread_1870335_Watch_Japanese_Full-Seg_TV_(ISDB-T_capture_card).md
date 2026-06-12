---
title: "Watch Japanese Full-Seg TV? (ISDB-T capture card)"
date: 2011-10-27
forum: General Help
---

### Post by quequotion on 2011-10-27
This is driving me insane.

I purchased an Earthsoft PT2 tuner card because it has a linux driver.
I also purchased an SRC3310-NTTCom (SCM Microsystems smart card reader) to read the required B-CAS encryption keycard, which I pulled out of a cheap USB tuner that does not have a linux driver.

Actually, it's exactly the same hardware as this on this page (Japanese): [http://team2ch.org/blog/?p=1103](http://team2ch.org/blog/?p=1103)

Apparently, this actually worked in Ubuntu 10.10, but I can't get anything done in 11.10.

First of all, the PC/SC driver is intermittently broken, so it's difficult to test the card (there are no unencrypted tv signals in Japan). This is supposed to be "fixed" after creating a pcscd group an adding myself to it but the error comes back frequently.

The installation process as recommended on the Japanese site above is out of date. Those drivers were not written to be compatible with linux 3.0. There are other drivers out there (several variant branches exist) but none have documentation and only a few even have a brief, mostly incomplete tutorial in Japanese.

At the moment i'm using the "earthsoft-pt1" driver which I believe is part of the dvb drivers included in ubuntu's kernel.... Most, but not all, of the guides in Japanese recommend to blacklist this driver without saying why or how to use the card without it.

This... file repository? Has a lot of zip files of code for this, but there is no organization of any kind. Most of the files are linked to from scattered guides for doing this and that with PT1/2 and other ISDB-T cards.:
[http://2sen.dip.jp/dtv/](http://2sen.dip.jp/dtv/)

One of those packages, up0588.zip, is an update for dvb-apps with a scanner that actually worked and got me a list of local channels.

That's the end of my progress.

---

### Post by quequotion on 2011-10-27
[http://aqua-linux.blog.so-net.ne.jp/2010-12-24](http://aqua-linux.blog.so-net.ne.jp/2010-12-24)

This post, from nearly a year ago, seems to have more up-to-date information than I've found so far.

I can now watch a recorded transport stream, but mplayer exits pretty quickly if I try to watch livetv.

---

### Post by quequotion on 2011-11-12
Figured this out.

The drivers for the B-CAS card reader are broken. (PS/SC)

If the card can't be read, the video stream won't decrypt.

If the video stream is encrypted, mplayer will crash.

Another page on the site above recommends some downgrades and pinning the versions in /etc/apt/preferences. The old versions work. Unfortunately the site recommends to pin those files in /etc/apt/preferences.d/pcsc, which does not work. /etc/apt/preferences.d/ is ignored by apt.

---

