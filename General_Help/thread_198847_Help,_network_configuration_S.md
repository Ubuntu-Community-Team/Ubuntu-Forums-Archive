---
title: "Help, network configuration :S"
date: 2006-06-17
forum: General Help
---

### Post by zefram on 2006-06-17
Hi, I installed Ubuntu a few hours ago and I'm already very impressed with it :D .
The installation went perfect but the internet connection is giving me a lot of headaches. First I could ping but not load websites - I got to fix this reading a thread here about the firefox's ipv6 option (I'm writing this from my new ubuntu box).
When I fixed this I thought that that may have done the trick for the rest of my applications, obviously it didn't. 
I can't use gaim, synaptic and every application that requires a connection...

Help a noob out, please!:sad:

---

### Post by zefram on 2006-06-18
Please reply something, I'm in desperate need for help

---

### Post by Ramses de Norre on 2006-06-18
You can ping and you can load pages with firefox? Do you use dhcp or static? Have you got a proxy configured? What's in /etc/network/interfaces and /etc/resolv.conf?

---

### Post by zefram on 2006-06-18
i have this in **/etc/network/interfaces** :
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

and this in **/etc/resolv.conf** :
nameserver 192.168.1.1

Yes i can see any page with firefox and ping anything in the shell, i use dhcp and as far as i know a have no proxy configured.

---

### Post by Ramses de Norre on 2006-06-18
That dns addres in resolv.conf doesn't look right to me, it seems to be a local ip (probably your router). 
You'll need to go to your router setup and set the dhcp settings to forward your isp's dns (probably two addresses). You can most likely find those addresses at the router page too, at the status page or something.

---

### Post by zefram on 2006-06-18
i can't find that option...
I should also mention that my network has a somewhat strange setup.
I have a dlink 502-T Adsl router connected to a Linksys WRT54g on its second ethernet port (not the specific internet port) - this was the setup recommended by linksys's custommer support, don't know if that could be a problem...

In the meanwhile i'll try a knoppix cd

---

### Post by zefram on 2006-06-18
Ok, i tried the knoppix 3.3 and it also didn't work, however, i also tried Damn Small Linux and strange as it may seem it worked perfectly.
On knoppix i ran the netcardconfig app and it got stuck while doing the DHCP broadcasting so it may have something to do with that. Could it also have to do with kernel versions since one worked and the other did not?

---

