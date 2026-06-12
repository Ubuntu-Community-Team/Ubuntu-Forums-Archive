---
title: "Thunderbird stable ppa still needed?"
date: 2012-07-23
forum: General Help
---

### Post by ajgreeny on 2012-07-23
For a long time I have been using the thunderbird stable ppa to ensure I had the most recent stable version.  When playing around with some of my enabled ppa repos today I noticed that the thunderbird stable ppa for Lucid no longer contains thunderbird; it is now in the standard repos.

Can someone confirm that this is the case, and that TB is now fully updated using the lucid main repos, just like firefox stable ppa became unnecessary some time ago.

---

### Post by cYbercOsmOnauT on 2012-07-23
Nowadays Mozilla provides compiled versions of Firefox and Thunderbird. You just needs to download, unpack and use it. To make it more comfortable you can also create a small .desktop file for it.

---

### Post by papibe on 2012-07-23
Hi ajgreeny.

There's no need any more. Both FF and TB are being updating often.

Currenly I'm on Lucid, and running TB v14 from the repositories:
```
apt-cache policy thunderbird
thunderbird:
  Installed: 14.0+build1-0ubuntu0.10.04.1
  Candidate: 14.0+build1-0ubuntu0.10.04.1
  Version table:
 *** 14.0+build1-0ubuntu0.10.04.1 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     3.0.4+nobinonly-0ubuntu4 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages

```
Regards.

BTW: v15 is on beta 1 (read [here]("http://www.omgubuntu.co.uk/2012/07/thunderbird-15-beta-1-lands-with-new-look-ubuntu-one-support")).

---

### Post by Habitual on 2012-07-24
FWIW: [So, that's It For Thunderbird?]("http://techcrunch.com/2012/07/06/so-thats-it-for-thunderbird/")

---

### Post by ajgreeny on 2012-07-24
Thanks for the repo information papibe, it is exactly what I assumed, but just wanted more confirmation.

There has been a huge amount of FUD after mozilla's announcement of its withdrawal from further development of TB, but that does not mean that TB is going to disappear in the immediate future.

That surely is one of the great advantages of open source software; anyone can, and probably will, pick it up and run with it, and it does not have to be mozilla.

---

