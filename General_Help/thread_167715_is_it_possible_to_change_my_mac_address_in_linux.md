---
title: "is it possible to change my mac address in linux?"
date: 2006-04-29
forum: General Help
---

### Post by cosmoshell on 2006-04-29
is it possible to change my mac address in linux? if so how do you do it? also is it possible to run my entire computer thru some kind of a %100 annoymas proxy?

---

### Post by Gannin on 2006-04-29
MAC address is based on hardware, not software, so no, I don't think there's a way you can change it.

There are some anonymous proxy services out there, but most of them you have to pay for.

---

### Post by harisund on 2006-04-29
It's not possible to change your MAC address, but it is possible to change the MAC address that your computer displays. That is called Mac Spoofing, and there are some software that allows you to do that, or as sudo you can edit the file /etc/dhcp3/dhclient.conf where you will find commented stuff..

---

### Post by anthro398 on 2006-04-29
It's quite easy to switch your mac address.  You can see the bash script I wrote for that [here]("http://ubuntuforums.org/showthread.php?t=77932").  Someone in that thread also mentions a gui interface for doing this but I've never used it.

---

### Post by anthro398 on 2006-05-09
Furthermore, there are plenty of good free anonymous proxies out there.  One is [tor]("http://en.wikipedia.org/wiki/Tor_(anonymity_network)"), for which there is a deb you can install with apt-get.

---

