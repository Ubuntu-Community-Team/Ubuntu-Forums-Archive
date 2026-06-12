---
title: "I can't download repositories"
date: 2006-03-19
forum: General Help
---

### Post by mikes34 on 2006-03-19
Hi 
I need help... I want to instal new applications in synaptic, but I can't download repositories... 
I can use internet by firefox, I turned off ipv6 in firefox and aliases also, but in terminal I can't ping any address, telnet don't works too...
can anybody help me please?

---

### Post by dermotti on 2006-03-19
Thats odd.

try **sudo apt-get update** from command line and see if it downloads.

---

### Post by Ramses de Norre on 2006-03-19
You can't ping but you can browse the internet? Can you visit every page? Does nslookup [http://www.ubuntu.org](http://www.ubuntu.org) (or any other site) show any errors?
If so it might be DNS that's malconfigured.

---

### Post by mikes34 on 2006-03-19
No it doesn't download anything :( 

matus@mygateway:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by mikes34 on 2006-03-19
matus@mygateway:~$ nslookup [http://www.ubuntu.org](http://www.ubuntu.org)
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find [http://www.ubuntu.org:](http://www.ubuntu.org:) SERVFAIL

---

### Post by Ramses de Norre on 2006-03-19
I think it's your DNS then. Have you configure your servers in system > administration > networking ?

---

### Post by mikes34 on 2006-03-19
no... i'm connected through dsl router, configured by dhcp

---

### Post by Ramses de Norre on 2006-03-19
Are your servers corectly configured in the dhcp settings of your router? I've experienced it myself, the router detected the right servers from the modem but I had to manually set them in the dhcp settings.

---

### Post by dermotti on 2006-03-19
open up a terminal and type **ifconfig** and paste the results in here

---

### Post by mikes34 on 2006-03-19
I'm not sure, I am not very experienced linux user yet... how can I find it? 
I tried to use static IP but then firefox doesn't work too...

---

### Post by mikes34 on 2006-03-19
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:A1:77:6E:3C
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4848196 (4.6 MiB)  TX bytes:911731 (890.3 KiB)
          Interrupt:16 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1407669 (1.3 MiB)  TX bytes:1407669 (1.3 MiB)

---

### Post by dermotti on 2006-03-19
hmmm, that looks fine.

 goto System --> networking

do you have any DNS servers listed?

In addition to using my router for dns, i also use 6.2.2.2 as a backup dns server...

---

### Post by mikes34 on 2006-03-19
yes, 192.168.1.1... I changed it, but after reboot changes is lost

---

### Post by mikes34 on 2006-03-19
nobody knows how to fix it?:(

---

### Post by Ramses de Norre on 2006-03-19
If you're sure you've got the right dns's, I don't know what could be the reason you can't resolve names..

---

### Post by mikes34 on 2006-03-19
but how can I change the dns server so, that it remain after reboot...

---

### Post by mikes34 on 2006-03-19
Can anybody help me? please...
I don't know why, but I can browse every page in firefox, but in terminal I can't ping every page... e.g. I can ping [www.ubuntuforums.org](www.ubuntuforums.org), but [www.azet.sk](www.azet.sk) I can't...

---

