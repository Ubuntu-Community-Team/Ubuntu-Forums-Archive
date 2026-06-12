---
title: "Help with Wireless not working on Ubuntu?"
date: 2011-08-03
forum: General Help
---

### Post by MiKogz on 2011-08-03
I recently installed windows and ubuntu dual boot, and ubuntu will not pick up my connection.  I have tried both a wired and wireless connection and neither work.  It doesn't even register that there is a network connected it just says firmware missing.

---

### Post by wildmanne39 on 2011-08-03
Hi, run these commands please:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

