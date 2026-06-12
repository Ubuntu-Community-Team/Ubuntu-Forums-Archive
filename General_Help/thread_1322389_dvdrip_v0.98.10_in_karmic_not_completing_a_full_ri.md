---
title: "dvd::rip v0.98.10 in karmic not completing a full rip"
date: 2009-11-10
forum: General Help
---

### Post by KiLaHuRtZ on 2009-11-10
Can anyone else confirm this?  For reasons unknown, I cannot get dvd::rip v0.98.10 in karmic to complete a full 100% disc rip.  It always dumps out around 70-80% and locks up.  Even running the command from CLI yields the same result, only a 70-80% completed rip.  On the inverse, dvd::rip v0.98.9, in Jaunty, worked fine for me most of the time.  I have filed a bug on this in hopes that I can get a regression back to v0.98.9.  However, I still need a few others to confirm this issue/bug.

[https://bugs.launchpad.net/ubuntu/+source/video-dvdrip/+bug/478710]("https://bugs.launchpad.net/ubuntu/+source/video-dvdrip/+bug/478710")

---

### Post by fluffman86 on 2009-11-10
A few things to check:

1.  Can you read/watch the DVD?  Have you installed the dvd css descrambler, either from medibuntu or 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
more: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

2.  Have you tried any other programs to see if it's just the DVD or your drive or something?  I use [http://handbrake.fr](http://handbrake.fr) to make backups of my legally owned, non-copy protected dvds. ;)  (hello, MPAA and DMCA!)

3.  Does this happen on multiple DVDs?

---

### Post by KiLaHuRtZ on 2009-11-10
1) Yes, DVD's are playable.
2) No, have yet to try anything else.
3) A DVD title that worked with Jaunty does not work with Karmic.

Update: I now believe it is an issue with transcode and not dvd::rip.  I just made an attempt with dvd::rip v0.98.9 and it still failed.  So I re-installed dvd::rip v0.98.10 and am now attempting with transcode v1.0.7 (Jaunty's version).  I will update the bug to reflect my findings.

---

### Post by stinger30au on 2009-11-10
doesnt surprise me dvdrip is failing


k9copy has some very weired ripping issues as well that i have never had before

seriously considering going back to 9.04

---

### Post by KiLaHuRtZ on 2009-11-10
Looks like it is not dvd::rip or transcode but some other library causing this which may also explain the problems you are having with k9copy as well.

---

### Post by KiLaHuRtZ on 2009-12-30
[https://bugs.launchpad.net/dvdrip/+bug/478710](https://bugs.launchpad.net/dvdrip/+bug/478710)

Fix should be mirrored in the repositories in 24-48 hours, but here are the packages anyway...

execflow v0.64-0ubuntu1:

[http://www.digitalenigma.net/~luke/ubuntu/lucid/libevent-execflow-perl_0.64-0ubuntu1_all.deb]("http://www.digitalenigma.net/~luke/ubuntu/lucid/libevent-execflow-perl_0.64-0ubuntu1_all.deb")

dvd::rip v0.98.10-0.2ubuntu5:

[http://www.digitalenigma.net/~luke/ubuntu/lucid/dvdrip_0.98.10-0.2ubuntu5_all.deb]("http://www.digitalenigma.net/~luke/ubuntu/lucid/dvdrip_0.98.10-0.2ubuntu5_all.deb")

---

