---
title: "[Ubuntu Server] VM Virtualbox (attempting to make VPS communicate with VB host)."
date: 2010-07-09
forum: General Help
---

### Post by ZnoteOT on 2010-07-09
Hello, I have a bit complicated network. 
Here is the thingy:

Wireless router - wireless signals to laptop.

Laptop receive connection on wireless network card

Laptop sends connection to local network card

Using a cross-network cable over to my desktop computer.

desktop computer receives internet connection from laptop.

Wireless router IP: 10.0.0.138

Laptop wireless IP: 10.0.0.8
Laptop local cable IP: 192.168.0.2

This is how the laptop is configurated:
Sharing wireless ethernet with: local ethernet

Desktop computer local cable IP: 192.168.0.5
desktop computer local cable gateway: 192.168.0.2
desktop computer local cable DNS server: 192.168.0.2
(If I remove the dns server IP I loose internet access). 

Everything works fine so far. Both my laptop and desktop computer is using Windows.
**[COLOR="Red"]Both the laptop and desktop computer have internet, no problems.[/COLOR]**

Now I wanted to test out Ubuntu Server.

I launched it through VM Virtualbox.

And whollah, we got another network in our system, the "VirtualBox Host-Only Network". 

Desktop computer "VirtualBox Host-Only Network" default IP: 192.168.56.1? (don't quite remember)

VPS Ubuntu Server default IP: 10.0.2.15 

VPS Ubuntu Server had access to Internet on default IP. 
VPS Ubuntu Server could neither ping 192.168.56.1? OR 192.168.0.5 (the desktop computer that hosts the virtualbox ubuntu server). 

I wanted to make the virtual server communicate with its host properly, so i did

Configure desktop computer:
Sharing local ethernet with: VirtualBox Host-Only Network

desktop virtualbox network IP: 192.168.2.1
desktop virtualbox network netmask: 255.255.255.0

And in linux:
sudo nano /etc/network/interfaces

and wrote this:
```
auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1
```

after saving this i did sudo /etc/resolv.conf
```
nameserver 192.168.2.1
```

Well, it ended with that: I do not get access to Internet any longer.
Neither am I able to communicate with the desktop computer (host of this ubuntu server). [From the ubuntu server] I have no problems communicating between laptop and desktop. 

**I am a complete newbie in Linux, I did not do this out of my head, I just try to get as much help as I can through google and the little networking experience I got from Windows.** 

And now im stuck. :(

If there is something I havent mentioned regarding the IP (for an example DNS of laptop) it means I have no IP, blank.

---

### Post by ballgame on 2012-03-05
ZnoteOT - Are you still doing this? How is it going?

---

### Post by nothingspecial on 2012-03-06
This thread is old.

Closed.

---

