---
title: "Internet connection"
date: 2010-03-30
forum: General Help
---

### Post by sillstep on 2010-03-30
Installed Ubuntu from live disc to a new hard drive and was able to connect to internet first try using Firefox. After one day I lost the internet connection and now cannot connect. Help me please. I have a cable broadband modem and a Netgear wireless router. Port 1 on the router is a wired connection to my desktop PC. Port 2 is a wired connection to the computer with Ubuntu installed. Also have a wireless connection from router to a laptop. All computers connect to internet except the PC with Ubuntu installed. I am not a computer wizzard, but I can follow instructions if someone can guide me. Thanks.

---

### Post by carlosgs91 on 2010-03-30
.

---

### Post by sillstep on 2010-03-30
I cannot find any panel with a wireless icon to enable eth.  ???

---

### Post by Iowan on 2010-03-30
Check **ifconfig -a** to see if interface has an IP address (probably won't). If it doesn't check **sudo lshw -C network** to verify whether the interface has an alias eth0) and a driver. (Post results, if possible)

---

### Post by sillstep on 2010-03-30
Iowan, thanks for your reply.  I have results for your request and this probably sounds real dumb, but other than typing the results of the commands, how would I post them so you can see?  I will do that if need be.

---

