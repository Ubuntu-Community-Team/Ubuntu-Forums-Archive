---
title: "Software center problem Please help"
date: 2011-10-05
forum: General Help
---

### Post by Benjotter on 2011-10-05
Hi there I'm still quite new to Ubuntu and still learning. Basically I have built a new PC for my bday yesterday install went smooth all drivers etc work out of the box :) but today i have tried downloading and realised my software center is not working

There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Sorry I'm still new to this and it means nothing to me 

Thanks Ben :P

---

### Post by Rubi1200 on 2011-10-05
Hi,
this is a known bug:
[https://bugs.launchpad.net/aptdaemon/+bug/665218](https://bugs.launchpad.net/aptdaemon/+bug/665218)

Try this first:

```
sudo dpkg --configure -a

sudo apt-get update
```

If that doesn't work, purge the package causing problems and then try installing it again:

```
sudo apt-get purge ttf-mscorefonts-installer

```
and then install it again:

```
sudo apt-get install ttf-mscorefonts-installer

```

---

### Post by Benjotter on 2011-10-05
Didn't make a difference but i just bought a new monitor so i reformatted pc and everything is perfect now :)

Thanks 

Ben

---

### Post by Rubi1200 on 2011-10-06
Glad you managed to get things sorted out.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

