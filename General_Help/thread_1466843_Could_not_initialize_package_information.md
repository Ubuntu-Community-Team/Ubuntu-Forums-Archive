---
title: "Could not initialize package information"
date: 2010-04-30
forum: General Help
---

### Post by jamsh on 2010-04-30
I get the following message when I try to update:

[B]Could not initialize package information
An unresolvable problem occurred while initializing the package information.
(Error: Opening the cache('E:type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-lucid.list,E:The list of sources could not be read.)'
This usually means that your installed packages have unmet dependencies.[/B]



Any help would be appreciated.

---

### Post by plucky on 2010-04-30
> **jamsh said:**
> I get the following message when I try to update:

[B]Could not initialize package information
An unresolvable problem occurred while initializing the package information.
(Error: Opening the cache('E:type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-lucid.list,E:The list of sources could not be read.)'
This usually means that your installed packages have unmet dependencies.[/B]



Any help would be appreciated.

Open a terminal and post output of ```
ls -l /etc/apt/sources.list.d/
```

This file (ubuntu-x-swat-x-updates-lucid.list) has a problem,but I have never seen a file like that before.

What exactly were you doing?
What were you upgrading?
Were you doing a distribution upgrade?

---

### Post by jamsh on 2010-04-30
HERE:

jim@X300:~$ ls -l /etc/apt/sources.list.d/
total 76
-rw-r--r-- 1 root root   0 2010-04-30 17:52 chromium-daily-beta-karmic.list
-rw-r--r-- 1 root root  68 2010-03-27 21:09 chromium-daily-beta-karmic.list.distUpgrade
-rw-r--r-- 1 root root 100 2010-04-30 17:52 chromium-daily-beta-karmic.list.save
-rw-r--r-- 1 root root   0 2010-04-30 17:52 chromium-daily-beta-lucid.list
-rw-r--r-- 1 root root  69 2010-04-30 17:52 chromium-daily-beta-lucid.list.save
-rw-r--r-- 1 root root   0 2010-04-30 17:53 chromium-daily-ppa-karmic.list
-rw-r--r-- 1 root root  67 2010-03-27 21:09 chromium-daily-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  99 2010-04-30 17:53 chromium-daily-ppa-karmic.list.save
-rw-r--r-- 1 root root   0 2010-04-30 17:52 google-chrome.list
-rw-r--r-- 1 root root  48 2010-03-27 21:09 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  50 2010-04-30 17:52 google-chrome.list.save
-rw-r--r-- 1 root root  66 2010-04-30 17:58 medibuntu.list
-rw-r--r-- 1 root root 271 2010-03-27 21:09 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root  66 2010-04-30 17:58 medibuntu.list.save
-rw-r--r-- 1 root root   0 2010-04-30 17:53 neversfelde-ppa-karmic.list
-rw-r--r-- 1 root root  64 2010-03-27 21:09 neversfelde-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  96 2010-04-30 17:53 neversfelde-ppa-karmic.list.save
-rw-r--r-- 1 root root 351 2010-03-27 21:09 opera.list.distUpgrade
-rw-r--r-- 1 root root 413 2010-04-01 13:47 opera.list.save
-rw-r--r-- 1 root root   0 2010-04-30 17:53 ubuntu-mozilla-daily-ppa-karmic.list
-rw-r--r-- 1 root root  73 2010-03-27 21:09 ubuntu-mozilla-daily-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root 105 2010-04-30 17:53 ubuntu-mozilla-daily-ppa-karmic.list.save
-rw-r--r-- 1 root root   2 2010-04-30 17:58 ubuntu-x-swat-x-updates-lucid.list
-rw-r--r-- 1 root root   2 2010-04-30 17:58 ubuntu-x-swat-x-updates-lucid.list.save
-rw-r--r-- 1 root root   0 2010-04-30 17:53 xorg-edgers-drivers-only-lucid.list
-rw-r--r-- 1 root root  74 2010-04-30 17:53 xorg-edgers-drivers-only-lucid.list.save
jim@X300:~$

---

### Post by plucky on 2010-04-30
Post output of ```
cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-lucid.list
```

---

### Post by jamsh on 2010-04-30
Just this :


jim@X300:~$ cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-lucid.list
n
jim@X300:~$

---

### Post by plucky on 2010-04-30
Basically it is not actually a repository,so you can delete it.
```
cd /etc/apt/sources.list.d/
ls -l
sudo rm ubuntu-x-swat-x-updates-lucid.list.*
```

The ls -l command makes sure that you are in the correct directory,before you use the rm command in super user mode.

Good Luck

---

### Post by jamsh on 2010-04-30
Wonderful!!! Thanks very much Plucky. 
I did as you said, rebooted, and had my first update via the update manager for 6 days.

Thanks again.

---

