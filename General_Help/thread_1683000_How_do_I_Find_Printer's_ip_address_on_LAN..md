---
title: "How do I Find Printer's ip address on LAN."
date: 2011-02-06
forum: General Help
---

### Post by Rasputin69 on 2011-02-06
I have a Brother MFC-5490CN AllIn One  on a LAN and I need to know it's IP address.

I am a newbie.

How do I find the address?

---

### Post by RAMDrive on 2011-02-06
if you're on a small private network, like your home.  Then try nmap 192.168.1.0/24  chagn ethe range to match your home range.  give it at leat 30 seconds dependong on the amount of devices.  Then you should receive something like thins:

Interesting ports on 192.168.1.153:
Not shown: 997 closed ports
PORT     STATE SERVICE
80/tcp   open  http
515/tcp  open  printer
9100/tcp open  jetdirect

results from my dell Printer.

---

### Post by marshag63 on 2011-02-06
I use this method.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

hope this helps.

MDG

---

### Post by pqwoerituytrueiwoq on 2011-02-06
i would just check my routers connected devices list it or check the printer if it has display

---

### Post by djeikyb on 2011-02-06
When I want a list of all machines on the network, I use [AngryIP aka ipscan](http://www.angryip.org).

---

