---
title: "An Unhandled error occured"
date: 2011-12-11
forum: General Help
---

### Post by Cookieh on 2011-12-11
In Ubuntu Software Center, I have tried to install XVidCap Screen Capture and got this following error :

There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

>Details

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

-----------------------------------------------------------------------------------------------------------------------------------

After I got this error, I have decided to try to install other app. It failed and gave me the same error.
I am using:

Ubuntu 11.10 Oneiric (sorry for maybe bad spelling)
Memory 488.0 MiB
Processor  Intel® Pentium(R) 4 CPU 2.80GHz
Graphics Intel® 865G x86/MMX/SSE2
OS Type 32-bit
Disk 491.7 GB with another 160 Gig internal hd connected

I know that there are loads of posts about this but most arent solved... Hopefully you will help me... Thanx

---

### Post by Cookieh on 2011-12-11
Got an idea of installing Python 2.7 as it will share the libraries, as it talks something about Python 2.7.. Not sure though...

---

### Post by Cookieh on 2011-12-11
More info, tried to install something through Terminal.... got this error...

root@cookieh-SCENIC-E:~# apt-get install gedit-gmate
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@cookieh-SCENIC-E:~#

---

