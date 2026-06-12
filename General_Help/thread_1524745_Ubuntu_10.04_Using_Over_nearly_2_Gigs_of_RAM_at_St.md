---
title: "Ubuntu 10.04 Using Over nearly 2 Gigs of RAM at Start-up"
date: 2010-07-05
forum: General Help
---

### Post by pinguy on 2010-07-05
```
pinguy@pinguy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965       2016       1948          0         57        377
-/+ buffers/cache:       1581       2383
Swap:         9105          0       9105
pinguy@pinguy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965       2263       1701          0         61        394
-/+ buffers/cache:       1808       2156
Swap:         9105          0       9105
pinguy@pinguy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965       2592       1372          0         68        398
-/+ buffers/cache:       2125       1839
Swap:         9105          0       9105
pinguy@pinguy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965       2609       1355          0         69        402
-/+ buffers/cache:       2137       1827
Swap:         9105          0       9105

```

I am about at the end of my patience with this. I have ran BUM and removed everything apart from the bare essentials stop most programs from starting with Startup Applications and just did a pretty violent clean up of programs I don't use.

I removed preload as I had that installed to see if that was the problem, but that made no difference at all.

I already know about the xorg problem but this should not affect me as I am running the property ATI driver.

[[IMG]http://img535.imageshack.us/img535/3750/desk1004.th.jpg[/IMG]](http://img535.imageshack.us/img535/3750/desk1004.jpg)

This wouldn't be too much of a problem if it just sat at about 2 gigs when idle, but it doesn't. After about 3-4 hours of it being on it's using all my memory and the PC is unusable.

---

### Post by davidmohammed on 2010-07-05
might be an issue with ureadahead - seem to remember during beta testing that you have to remove the pack files sometimes and do a couple of reboots to get the pack file to rebuild

sudo rm /var/lib/ureadahead/pack

---

### Post by pinguy on 2010-07-05
> **davidmohammed said:**
> might be an issue with ureadahead - seem to remember during beta testing that you have to remove the pack files sometimes and do a couple of reboots to get the pack file to rebuild

sudo rm /var/lib/ureadahead/pack

This might have sorted it. After two reboots memory use seems to have halved. I am going to leave it on overnight just to see if it maxis out my memory again, but if it doesn't I will mark this thread as solved, and thanks for the help. I would of never thought of trying that.

---

### Post by askreet on 2010-07-05
Sorry for thread jacking: what is that awesome info panel you have on the right side of your screen?

---

### Post by pinguy on 2010-07-06
> **askreet said:**
> Sorry for thread jacking: what is that awesome info panel you have on the right side of your screen?

[http://ubuntuforums.org/showpost.php?p=9501964&postcount=12986](http://ubuntuforums.org/showpost.php?p=9501964&postcount=12986)

---

### Post by pinguy on 2010-07-08
Doing sudo rm /var/lib/ureadahead/pack seemed to help but the memory leak was still there. I was able to hunt down what was causing the leak. It ended up being the property ATI driver. I just un-installed the fglrx driver and went back to the xserver-xorg-video-radeon driver but the problem is still there.

I know it was the property ATI driver because I did a fresh install of Ubuntu and left installing the property ATI driver till last because I was making a distro using Remastersys Backup tool and didn't want the ATI driver installed on the distro.

Before installing the ATI drive ram use was at about 650/700MB. Now it's back to about 1.5/2GB. Like I said un-installing the driver did nothing.

I could easily install the copy I made before install the ATI driver but it would be nice to be able to fix it.

**EDIT#**

It's now fixed, what I had to do was remove the fglrx driver then run *sudo rm /var/lib/ureadahead/pack* and do two reboots.

---

