---
title: "How to install packages on Ubuntu Server"
date: 2012-10-02
forum: General Help
---

### Post by Johnyburd on 2012-10-02
I installed the server on one of my computers and set it up with my network.  However whenever I try to install a package it says it can't find it.  I tested it by pinging Google and it worked, but it never found any package even the ones it suggested I use.  How can I install packages and specifically the desktop for the server?

---

### Post by wojox on 2012-10-02
Try:
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by papibe on 2012-10-02
Hi Johnyburd. Welcome to the forums ):P

First start by updating your sources:
```
sudo apt-get update
```
Then, let's search for 'nmap':
```
apt-cache search nmap
```
this would be the results:
```
**nmap - The Network Mapper**
doscan - port scanner for discovering services on large networks
foomatic-gui - GNOME interface for configuring the Foomatic printer filter system
honeyd - Small daemon that creates virtual hosts simulating their services and behaviour
knmap - KDE interface to nmap, the Network Mapper
knmap-docs - KDE interface to nmap, the Network Mapper &#8212; manual
libnmap-parser-perl - parse nmap scan data with perl
nmapsi4 - graphical interface to nmap, the network scanner
p0f - Passive OS fingerprinting tool
pads - Passive Asset Detection System
pbnj - a suite of tools to monitor changes on a network
piwi - P(erl|relude) IDS Web Interface - A frontend to your Prelude database
pnscan - Multi threaded port scanner
psad - The Port Scan Attack Detector
python-scapy - Packet generator/sniffer and network scanner/discovery
umit - network tool and graphical frontend for nmap
xprobe - Remote OS identification
zenmap - The Network Mapper Front End

```
To install the actual 'nmap' package:
```
sudo apt-get install nmap
```
Hope it helps, and let us know how it goes.
Regards.

---

### Post by Johnyburd on 2012-10-03
When I try
sudo apt-get update
it just list a one bunch of packages and says it can't find them either.
Is there something I need to do when I first install the server?

---

### Post by Cheesemill on 2012-10-03
Can you post the full output of 'sudo apt-get update' so we can see what the problem is please.

---

### Post by Cheesemill on 2012-10-03
I've just noticed that in your first post you want to install a desktop on your server. If this is the case then you may as well just install the desktop version of Ubuntu to start with.

---

### Post by Johnyburd on 2012-10-04
If I do that can I still make a server?  That would be a lot easier.

---

### Post by robgraves on 2012-10-04
> **Johnyburd said:**
> If I do that can I still make a server?  That would be a lot easier.

You would need whatever packages related to what you wanted your server to do: i.e. Apache, MySQL, PHP, etc.  but yes you could just install the desktop version of Ubuntu and retrieve the packages you want to run a server.  It's just that people usually don't run a server-only system with a desktop...which from what I assume is the aim of Ubuntu Server Edition.

Check this out for more info:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Johnyburd on 2012-10-06
Yeah I'll do that. I'm going to Install FOG on Ubuntu.
thx,
johnyburd ;)

---

