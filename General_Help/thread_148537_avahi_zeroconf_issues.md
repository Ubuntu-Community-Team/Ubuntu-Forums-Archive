---
title: "avahi zeroconf issues"
date: 2006-03-22
forum: General Help
---

### Post by zapcojake on 2006-03-22
Hello, I have the daemon running on 3 computers.  2 are wired and one is wifi.
The 2 wired can see all 3 computers but the wireless can see nothing.  Also I seem to be stuck here.  How to I browse folders on different computers?  I have read the howto's which usually are really great but this one has me stumped.  I should also mention I computer is running 64 Ubuntu.  The wireless computer is using an airnet awd154 card with ndiswrapper and I am on a Belkin router (which I do not recomend).   Thanks in advance--Jake

---

### Post by tonic on 2006-06-06
I don't think avahi works with ndiswrapper. I have the same problem at the moment. However, I never had the problem when I was running a linux native driver (that sort of worked) for wireless.

The exact behaviour I currently get is that avahi will broadcast/publish to the interface but will not discover anything through it. There is a mention of issues with ndiswrapper on the avahi troubleshooting page - [http://avahi.org/wiki/Avah4users#Troubleshooting](http://avahi.org/wiki/Avah4users#Troubleshooting).

---

### Post by dyssident on 2006-07-16
FYI, Im running the current Avahi / ndiswrapper and they work like a dream.

---

