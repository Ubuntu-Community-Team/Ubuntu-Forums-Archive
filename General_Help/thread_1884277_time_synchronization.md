---
title: "time synchronization"
date: 2011-11-21
forum: General Help
---

### Post by Neeti on 2011-11-21
i am trying to make a private cloud using two systems of the same configuration. 
after setting up the initial setup i am not able to synchronize the time of both the systems..
i have tried installing NTP for this.
apt-get install ntp
but  still the time is not synchronized
can anyone help me out for this????

---

### Post by lisati on 2011-11-21
*Thread moved to **General Help**.*

---

### Post by Zill on 2011-11-21
Neeti:  Are you *sure* ntp is actually installed?  The command you gave should be prefixed by sudo eg.
```
sudo apt-get install ntp
```
Type the following to find out if ntp is working or not:
ntpq -p         (displays server name)
or
ntpq -pn	(displays server IP address)

The IP addresses will be different, because you've been assigned random timeservers. The essential thing is that one of the lines starts with an asterisk (*), this means your computer gets the time from the internet - you'll never have to worry about it again!

---

