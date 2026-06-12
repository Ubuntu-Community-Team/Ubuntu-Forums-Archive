---
title: "Can't configurate my Realtek Ethernet..."
date: 2006-03-19
forum: General Help
---

### Post by Klingstedt on 2006-03-19
I just put in a simple realtek Ethernet card in my other computer with Ubuntu..
My router cant find it tho.. and that sucks.. i think its installed on Ubuntu but im unsure...
Anyone who knows how to fix?

---

### Post by Azrael on 2006-03-19
lspci -vv | grep Eth
dmesg | grep eth
cat /var/log/syslog | grep eth
ifconfig
cat /etc/network/interfaces
etc.......


Open a terminal on your Ubuntu computer and try those commands to figure out what's going on. Post back whatever you think might be relevant.

---

