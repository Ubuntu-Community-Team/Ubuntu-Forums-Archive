---
title: "Chromium is 12.0.742.112 (90304), Chrome is already on 13.x ..."
date: 2011-09-04
forum: General Help
---

### Post by sanderj on 2011-09-04
Hi,

My Ubuntu 10.04 and 11.04 are both up-to-date, but are running Chromium "12.0.742.112 (90304)", whereas the plain, mainstream Chrome version is on version "13.0.782.220": [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/) says "the Stable channel has been updated to 13.0.782.220 for Windows, Mac, Linux, and Chrome Frame."

So, is Chromium (or Ubuntu Chromium, or Ubuntu Chrome) lagging behind? If so, why isn't it on version 13.x? And how can I get Chrom* version 13.x via the repositories?

I need an uptodate Chrome version because of all the Diginotar stuff ...

---

### Post by ron999 on 2011-09-04
> **sanderj said:**
> 
 why isn't it on version 13.x? And how can I get Chrom* version 13.x via the repositories?...

Hi
Try using one of the PPAs here:- [https://launchpad.net/chromium-project]("https://launchpad.net/chromium-project")
Stable Channel is now version 13.0.782.218~r98754

---

### Post by sanderj on 2011-09-04
> **ron999 said:**
> Hi
Try using one of the PPAs here:- [https://launchpad.net/chromium-project]("https://launchpad.net/chromium-project")
Stable Channel is now version 13.0.782.218~r98754

I choose Beta, and my Chromium is now on 14.0.835.126 (Developer Build 99097 Linux). So that's good. Thank you.

But why is the official repository so old?



Info for others: this is what I did:

```

 sudo apt-add-repository ppa:chromium-daily/beta
 sudo apt-get update
 sudo apt-get upgrade
 sudo apt-get install chromium-browser

```

---

