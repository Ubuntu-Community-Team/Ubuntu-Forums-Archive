---
title: "Terminal Cant Connect To The Internet"
date: 2009-08-30
forum: General Help
---

### Post by TaNXC on 2009-08-30
It just doesent. Cant update or install things from it at all!

---

### Post by kellemes on 2009-08-30
> **TaNXC said:**
> It just doesent. Cant update or install things from it at all!

Details please...

---

### Post by TaNXC on 2009-08-30
It would say something like,

sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list
[sudo] password for dad: 
--2009-08-30 14:11:52--  [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list)
Connecting to 116.50.216.186:3128... failed: Connection timed out.
Retrying.

--2009-08-30 14:15:02--  (try: 2)  [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list)
Connecting to 116.50.216.186:3128... failed: Connection timed out.
Retrying.

Etc, etc. For everything that has to do with internet used in the terminal.

---

### Post by NoaHall on 2009-08-30
Can you get online through the gui? Are you talking about recovery terminal, terminal in the gui, or the "ctrl + alt + 1" terminal?

---

### Post by TaNXC on 2009-08-30
Im talking about the Applications>Accessories>Terminal terminal.

---

### Post by TaNXC on 2009-08-30
Bummmmmmmmppppppppppppppppppp

---

### Post by fluffman86 on 2009-08-30
But you can get online using Firefox?  As in, are you using the same computer to post here?

---

### Post by TaNXC on 2009-08-30
Yes. I just cant do it through terminal...................

---

### Post by fluffman86 on 2009-08-30
Try again, maybe the site was down.

---

### Post by t0p on 2009-08-30
Can you run the following command in your terminal and post the output please.  (Note: you'll need to wait several seconds for the output):

```
ping -c 5 google.com
```

---

### Post by oldos2er on 2009-08-30
> **TaNXC said:**
> It would say something like,

sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list
[sudo] password for dad: 
--2009-08-30 14:11:52--  [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list)
Connecting to 116.50.216.186:3128... failed: Connection timed out.
Retrying.

--2009-08-30 14:15:02--  (try: 2)  [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list)
Connecting to 116.50.216.186:3128... failed: Connection timed out.
Retrying.

Etc, etc. For everything that has to do with internet used in the terminal.

 I just tried the URL, it worked fine. If it's still not working for you, manually add **deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main** to your sources.list by running the command **gksu gedit /etc/apt/sources.list**. Then run **sudo apt-get update**.

---

### Post by TaNXC on 2009-08-30
Suprisingly, pinging happens in seconds for me, just stuff like sudo apt-get update doesent work anymore :/

PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=53 time=48.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=53 time=47.7 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=53 time=51.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=53 time=50.1 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=5 ttl=53 time=50.1 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4008ms
rtt min/avg/max/mdev = 47.742/49.591/51.476/1.367 ms
dad@dad-laptop:~$

---

### Post by TaNXC on 2009-08-30
Bummmppppppppppppppppppppppppppppppppppppppppppppppppp

---

### Post by TaNXC on 2009-08-30
Help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by TaNXC on 2009-08-30
Bummmmmmmmmmmmmmmmmmmmmppppppppppppppppppppppppppppp

---

