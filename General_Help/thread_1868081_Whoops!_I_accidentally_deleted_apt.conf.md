---
title: "Whoops! I accidentally deleted apt.conf"
date: 2011-10-23
forum: General Help
---

### Post by KebertX on 2011-10-23
I just deleted all the text in apt.conf. Unintentionally.

It kept telling me it was unable to connect to 127.0.0.1:4444. (That's just since I set up Privoxy for I2P), so I figured something must be up. Sure enough, apt.conf contained only two lines naming 127.0.0.1:4444 as its http proxy. I raeg'd and just deleted both of them then saved and exited. Now I'm getting a few 404 errors as I try to apt-get update. I just sort of recklessly fuc*ked up.

Anyways, for the sake of my future apt-getting, would one of you fine ladies or gentlemen refresh my memory for what I properly need in that file?

---

### Post by cryptotheslow on 2011-10-23
Well I thought I'd try and be helpful.....   but on my 10.04 LTS Server install there is no apt.conf, just the below in /etc/apt/apt.conf.d :confused:


```
crypto@ubuserver:/etc/apt/apt.conf.d$ ls -l
total 44
-rw-r--r-- 1 root root   40 2011-10-08 00:35 00trustcdrom
-rw-r--r-- 1 root root  406 2011-05-30 06:43 01autoremove
-rw-r--r-- 1 root root    9 2011-05-30 06:43 01ubuntu
-rw-r--r-- 1 root root  157 2010-04-09 15:41 05aptitude
-rw-r--r-- 1 root root  129 2010-04-13 21:45 10periodic
-rw-r--r-- 1 root root  108 2010-04-13 21:45 15update-stamp
-rw-r--r-- 1 root root   85 2010-04-13 21:45 20archive
-rw-r--r-- 1 root root   80 2011-01-10 17:54 20auto-upgrades
-rw-r--r-- 1 root root 1052 2011-01-10 17:54 50unattended-upgrades
-rw-r--r-- 1 root root  182 2010-04-09 15:33 70debconf
-rw-r--r-- 1 root root  229 2010-04-13 21:45 99update-notifier
```
So I'm no use at all and will have to watch for an answer too :popcorn:

---

### Post by WorMzy on 2011-10-23
You should have an example file at /usr/share/doc/apt/examples/apt.conf.

---

### Post by KebertX on 2011-10-23
> **WorMzy said:**
> You should have an example file at /usr/share/doc/apt/examples/apt.conf.

Winner! Copypasted it, updating works now. 
Interestingly enough, I still get a 404 on any packages from [http://ppa.launchpad.net](http://ppa.launchpad.net) (Only 5).
A click of that will show that there's nothing wrong with that. But I will survive. tanks ubuntuforums, you gave me my life back!

---

