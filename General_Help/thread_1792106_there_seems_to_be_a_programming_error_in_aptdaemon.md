---
title: "there seems to be a programming error in aptdaemon"
date: 2011-06-27
forum: General Help
---

### Post by Sgasher on 2011-06-27
When trying to install anything with the Ubuntu Software Centre, I just receive "There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks." 

With details: ```
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

``` 
And then a bug report request with the title "Sorry, the program "aptd" closed unexpectedly" and then, to top that when reporting the error I get ```
The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

apt, apt-utils, libpam-modules, libpam-modules-bin, libpam0g, libplymouth2, perl-base, plymouth, python-apt, python-apt-common, python-gobject
```

I'm totally new to Linux, after only using Windows since Windows 95, through to Windows 7. So if I've missed anything obvious, sorry :/

---

### Post by Rubi1200 on 2011-06-28
Hi and welcome to the forums :-)

Open a terminal and run the following commands:

```
sudo apt-get clean

sudo apt-get update

sudo apt-get upgrade
```

If any of the commands reports errors, please post them here.

Thanks.

---

### Post by Sgasher on 2011-06-28
Thanks, this seems to have fixed it! Can't thank you enough ^^

---

### Post by Rubi1200 on 2011-06-29
Excellent! I am really pleased this worked and fixed the issues :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

