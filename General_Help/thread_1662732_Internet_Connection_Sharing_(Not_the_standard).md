---
title: "Internet Connection Sharing (Not the standard)"
date: 2011-01-08
forum: General Help
---

### Post by AlecTeal on 2011-01-08
So - i got it to work - ish.

first of all the hardware that's involved:
xbox360
Laptop
Computer
Server-box (A computer :P)
5 port £10 switch
Mobile Phone
2 wireless cards

The goal is: 
[FONT=Courier New]using a monospace font
[/FONT]```
[FONT=Courier New]
+-----------+--------+-----------+----------------+---+---------------+
| < ppp0 >  | Server | < eth0 >  | Network Switch | 0 |---------------|
| (phone)   |        +-----------+----------------+ 1 | Xbox 360      |
[/FONT][FONT=Courier New]|           |        |                            | 2 |               |
[/FONT][FONT=Courier New]|   OR:     |        |                            | 3 |               |
[/FONT][FONT=Courier New]|           |        |                            | 4 |               |
| < wlan1 > |        +-----------+----------------+---+---------------+
|           |        | < wlan0 > | {Ad-hoc cloud} | 0 | Laptop        |
|           |        +-----------+----------------+ 1 | [Wi-fi device]|
|           |        |                            |...|  ....         |
|           |        |                            | n | n[th] device  |
+-----------+--------+----------------------------+---+---------------+
[/FONT]
```[FONT=Courier New]
[/FONT][FONT=Courier New]
[/FONT]I hope this diagram shows my intentions, how i may have an internet connection via phone or wlan1 share it with eth0 and wlan0

anyway as i said, i have done  _some_ of this, this is where i get stuck
i did this (while as SU)
```

ifconfig eth0 192.168.254.1
iptables -A FORWARD -o ppp0 -i eth0 -s 192.168.254.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```Source: tweak of: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

i then configured dnsmasq using the settings on that page

I then plugged my laptop into the switch and tried to connect- IT WORKED
i then plugged my computer into the switch - IT DIDN'T
xbox 360 didn't work.

but the laptop still did

i used firestarter along side this setup to see connections, nothing was blocked (bar dns which i unblocked) and my laptop still worked after

the xbox wasn't able to get an IP adress, the laptop did (192.168.254.246)
nor was the computer

I can give more data on request, but....
after i restarted nothing worked, i did the settings again, nothing worked, eth0 was never ready, and you can't connect it to the switch. i'm new to networking; i'd call myself an adept novice regarding linux itself, and all computers can be assumed to be using ubuntu 10.10

my question is really. is there a decent how-to guide. what do you suggest, is it even posible?
[FONT=Courier New]
[/FONT]
[FONT=Courier New]
[/FONT][FONT=Courier New]
[/FONT]

---

### Post by AlecTeal on 2011-01-08
i did read some where that switches only let a gatework on certain ports. athough this makes no sense as its just a bridge, forwarding things i did try multiple ports.
if it helps:

**  TP-Link [B]TL-SF1005D** 5-Port Unmanaged 10 / 100M Desktop Switch      [/B]

    **Overview**  - [Online stores]("http://www.google.com/products/catalog?client=ubuntu&q=tl-sf1005d&oe=utf-8&cid=13171447467756345434&os=sellers")  - [Reviews]("http://www.google.com/products/catalog?client=ubuntu&q=tl-sf1005d&oe=utf-8&cid=13171447467756345434&os=reviews")  - [Details]("http://www.google.com/products/catalog?client=ubuntu&q=tl-sf1005d&oe=utf-8&cid=13171447467756345434&os=contents")  - [Related items]("http://www.google.com/products/catalog?client=ubuntu&q=tl-sf1005d&oe=utf-8&cid=13171447467756345434&os=related")  
            [IMG]http://lh3.googleusercontent.com/public/msCUGBne6pibRYFFDnfz1uCb-7l6ulSpQi-GkwkCTzywbEJwPDN6ZFrAnwjM8K9qThB97aRtgSstxmnWIE8XRYhLs-hD7yrqeHksPivnlbmz2xfOCOHov1b6Y4puipZtIUC5tK0x4g[/IMG]  
          $10 [online]("http://www.google.com/products/catalog?client=ubuntu&q=tl-sf1005d&oe=utf-8&cid=13171447467756345434&os=sellers")    
       [1 review]("http://www.google.com/products/catalog?client=ubuntu&q=tl-sf1005d&oe=utf-8&cid=13171447467756345434&os=reviews")  
      All ports support Auto MDI/MDIX function, eliminating the need for  crossover cables or Uplink ports. The Switch is Plug-and-Play and each  port can be used as general ports or Uplink ports and can be simply  plugged into a server, a hub or a switch, using straight cable or  crossover cable.

---

### Post by AlecTeal on 2011-01-08
i've tried again, same problem. but now i keep getting eth0 is not ready - even when things are plugged into the switch

---

### Post by AlecTeal on 2011-01-09
bump

---

### Post by AlecTeal on 2011-01-10
bump

---

### Post by AlecTeal on 2011-01-14
bump

---

### Post by AlecTeal on 2011-01-14
bump

---

### Post by AlecTeal on 2011-01-16
bump

---

### Post by AlecTeal on 2011-01-21
bump

---

### Post by mciverza on 2011-01-21
I would like to check that there isn't anything else blocking your traffic

Please would you attach the output of 
sudo iptables-save -c

as a text file. 

Please include the output of  the following commands in your reply
ip a

netstat -tulnp

Please attach your dnsmasq configuration file.

ip a is to see all your ip address configuration (like a compact version of ifconfig)
netstat is to see which ports your system is running services on, to make sure dnsmasq is listening on the correct interfaces.

---

