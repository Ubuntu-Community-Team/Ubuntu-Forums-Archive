---
title: "Can't install librtmp-dev because wrong version of librtmp0 is/is not installed"
date: 2012-08-23
forum: General Help
---

### Post by KeithLM on 2012-08-23
I'm running 12.04 on a system that was upgraded from 11.10.  I would like to install librtmp-dev so I can build xbmc locally, however I cannot because of the following message:
```
 librtmp-dev : Depends: librtmp0 (= 2.4~20110711.gitc28f1bab-1) but 2.4~20110711.gitc28f1bab-1ubuntu0~ppa2~natty2 is to be installed
```

The version only varies by the ppa it comes from, or something like that.  I don't really know for sure.  

I've tried to remove other stuff that depended on librtmp0 thinking something was screwing it up and perhaps I could remove it and re-install it, but at this point I have 104 packages installed that depend on it, so I can't really remove it without potentially screwing up my whole system.

So is there some way to convince Ubuntu to install librtmp-dev since clearly a correct version of librtmp0 is on this system?

---

### Post by Marqin on 2012-08-23
Try:
```
dpkg --force-depends --install file_with_librtmp0.deb
```

---

### Post by KeithLM on 2012-08-23
When I first encountered this a few months ago I searched and searched and never found a solution.  Shortly after posting this I continued searching for how to force something and found a decent answer:
apt-get install librtmp0=2.4~20110711.gitc28f1bab-1

That appears to have worked just fine.  Now the question is did I completely screw up my system prior to this when I was trying to remove other things dependent on librtmp that I thought I didn't need.

---

### Post by poho on 2013-06-08
+1

> apt-get install librtmp0=2.4~20110711.gitc28f1bab-1

worked for me

---

