---
title: "NAT problems"
date: 2006-01-29
forum: General Help
---

### Post by ivancruz on 2006-01-29
I have a small network here at home with just 2 computers: 
mine, running Ubuntu, 2 network cards, connected to Internet via DSL modem.
wife, running Win 2000, 1 network card, connected to my machine via old coax cables.

That is my second Ubuntu install. In the first one, I had success in sharing my internet connection by following instructions from that FAQ:

[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

After changing to a shinning new Athlon64 (also 2 network cards, same DSL modem), I could not put it to work again.

The internal network is just fine. Both computeres ping each other, I can browse shares on W2000, W2000 can open pages on my apache etc... To make things worst, DNS maskerading **works**. Problem is only on ip maskerading.

My configuration:

eth0: 192.168.1.1/24     connects to DSL modem.
eth1: 192.168.0.1/24     connects to wife.

My wife:

eth0: ip: 192.168.0.100/24
         gateway 192.168.0.1
         Prefered DNS: 192.168.0.1

To help trobleshooting, I installed Ethereal and captured packages generated from
a "ping ubuntulinux.org" on wife:

```

 # Time    Source              Destination         Protocol  Info
79 6.0771  192.168.0.100       82.211.81.166       ICMP      Echo (ping) request
80 6.0771  200.216.103.107     82.211.81.166       ICMP      Echo (ping) request
81 6.0771  200.216.103.107     82.211.81.166       ICMP      Echo (ping) request
82 6.4917  82.211.81.166       200.216.103.107     ICMP      Echo (ping) reply
83 6.4917  82.211.81.166       200.216.103.107     ICMP      Echo (ping) reply
84 7.3928  192.168.0.100       82.211.81.166       ICMP      Echo (ping) request
....

```

I interpreted those infos these way:

Packet #79 was the fist ping request from wife, arriving on my machine.
#80 was the same package, routed to my internet gateway on "ppp0".
#81 was the request encapsuled on a PPP envelope.
#82 (half a second after) was the original response from ubuntulinux, PPP encapsuled.
#83 was the reply without PPP envelope.
#84 (almost 1 second after) was the second ping request from wife.

I believe that it would have to exists a extra package between 83 and 84, routing the reply back to wife. On DNS requests, that reply exists.

Are my assumptions correct? Where is my mistake? There is another tool I can use to help troubleshooting that problem? Firestarter can help in some way?

Thanks in advance.

Ivan.

---

### Post by dcstar on 2006-01-29
[QUOTE=ivancruz]I have a small network here at home with just 2 computers: 
mine, running Ubuntu, 2 network cards, connected to Internet via DSL modem.
wife, running Win 2000, 1 network card, connected to my machine via old coax cables.

That is my second Ubuntu install. In the first one, I had success in sharing my internet connection by following instructions from that FAQ:

[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

After changing to a shinning new Athlon64 (also 2 network cards, same DSL modem), I could not put it to work again.
......[/QUOTE]
sudo sysctl -a | grep ip_forward

If it says "0", then

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

And if you want this to "stick" after a reboot, edit /etc/sysctl.conf and add the following line:

net.ipv4.ip_forward = 1

---

### Post by ivancruz on 2006-01-30
Already set to 1 David, but anyway, thanks for trying.

---

### Post by Peter76 on 2006-01-30
In this etup I would use firestarter ( sudo apt-get install firestarter ) to share your connection

---

### Post by dcstar on 2006-01-30
[QUOTE=ivancruz]Already set to 1 David, but anyway, thanks for trying.[/QUOTE]
Check /etc/network/options and see if "ip_forward=yes"

---

### Post by ivancruz on 2006-02-01
Too bad, Firestarter didn't do the magic :cry:.

---

### Post by ivancruz on 2006-02-01
> 
Check /etc/network/options and see if "ip_forward=yes"


It was set to "no" but the change also didn't help. :-?

---

