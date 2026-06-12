---
title: "Static IP at startup"
date: 2010-08-16
forum: General Help
---

### Post by venom20 on 2010-08-16
Hello all, I ran through some search criteria and was unable to find  anything that fit this issue. This probably belongs in a newbie forum,  but I couldn't find an active one here. Just to let you know, I have  only been using kubuntu for about a week now. 

My problem seems fairly straight-forward, but I cannot find a solution  to it. I want to start kubuntu up with a static IP. I have already set  up the IP in the list of connections (in fact it is the only one  present). Once kubuntu loads up, I can click on the ethernet connection  in the task manager and it shows 2 connection: a dynamic connection  (with a heart beside it) and a connection called static. I can then  select static (and a heart is placed beside it) and everything works  perfectly fine. The problem is that I cannot set this static IP to be  the default connection. I have edited interfaces at /etc/network/ but  this did not seem to correct the issue either. I"m hoping that someone  can assist me in this newbish task. Here is what my interfaces currently  looks like

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.131
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

thanks for any assistance

---

### Post by lokojones on 2010-08-16
> **venom20 said:**
> Hello all, I ran through some search criteria and was unable to find  anything that fit this issue. This probably belongs in a newbie forum,  but I couldn't find an active one here. Just to let you know, I have  only been using kubuntu for about a week now. 

My problem seems fairly straight-forward, but I cannot find a solution  to it. I want to start kubuntu up with a static IP. I have already set  up the IP in the list of connections (in fact it is the only one  present). Once kubuntu loads up, I can click on the ethernet connection  in the task manager and it shows 2 connection: a dynamic connection  (with a heart beside it) and a connection called static. I can then  select static (and a heart is placed beside it) and everything works  perfectly fine. The problem is that I cannot set this static IP to be  the default connection. I have edited interfaces at /etc/network/ but  this did not seem to correct the issue either. I"m hoping that someone  can assist me in this newbish task. Here is what my interfaces currently  looks like

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.131
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

thanks for any assistance

Haven't used Kubuntu in a while, but if I was in plain debian, I would just remove the third line "auto eth1", that makes eth1 use DHCP to configure the interface. But again, I don't know how Kubuntu network settings manage the interfaces files, probably it would just replace the line after you delete it, but its worth trying anyways.

---

### Post by venom20 on 2010-08-16
I removed the line as suggested but that just loaded the DHCP connection upon a reboot. Upon closer inspection, when connected it stated that the connection was actually on eth0 and not eth1, so I switched the lines in interfaces to read eth0. Tried it with and without the third line, and both times it stated that my connection was now unmanaged :(. Back to the drawing board.

---

### Post by Iowan on 2010-08-16
Ordinarily, interfaces defined in */etc/network/interfaces* are ignored by Network Manager. You can probably change that by editing */etc/NetworkManager/nm-system-settings.conf*.

At least on Ubuntu. On Kubuntu ???

---

### Post by venom20 on 2010-08-16
Success!!

I edited my *etc/network/interfaces* so that it looked like this

auto eth0
iface eth0 inet static
address 192.168.0.131
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

then I followed what Iowan had suggested. In */etc/NetworkManager/nm-system-settings.conf* I edited the managed line to that it reads 

managed=true

one quick restart later and it booted right up with the static IP that I had specified. Only problem is aesthetics now (name of the connection) but I don't really care about that. Thank you kindly all.

---

### Post by lokojones on 2010-08-17
No problem. Add [SOLVED] in the begining of the topic's title so that people know it's solved :).

---

### Post by venom20 on 2010-08-17
I will, but I booted it up this morning and neither of the connections  were working. I am going to hold out on the resolved thing for now. It  loaded up with the correct connection, like last night but I was unable  to connect. The connection had no domain name servers listed in it (it  was blank). I could surf by IP but not fqdn. 

I know what is lacking, but I do not know what to call them in  interfaces. Should I just put a like like *Name Servers 192.168.0.1*

---

### Post by Iowan on 2010-08-17
DHCP usually provides a list of nameservers. Network Manager can be configured with nameservers. Ordinarily, */etc/resolv.conf* contains the address of nameservers, but it is usually used (overwritten) by other programs. You can try entering the addresses of your nameservers there, but they may not stick. **resolvconf** *might* help - but I've seen some threads that solved problems by *removing* r**esolvconf**.

---

### Post by bergfly on 2010-08-19
Just wondering, but when you open System Settings ---> Network settings and then double click on the wired connection (assuming eth0 is wired)

What are the settings under IP address tab? This is how I would have set the static address. (set to manual and put in parameters)

You will enter your DNS server on that tab. If in doubt, you can always use opendns for DNS [http://www.opendns.com/]("http://www.opendns.com/")
 208.67.222.222
208.67.220.220

---

### Post by jaya28inside on 2010-08-23
> **Iowan said:**
> DHCP usually provides a list of nameservers. Network Manager can be configured with nameservers. Ordinarily, */etc/resolv.conf* contains the address of nameservers, but it is usually used (overwritten) by other programs. You can try entering the addresses of your nameservers there, but they may not stick. **resolvconf** *might* help - but I've seen some threads that solved problems by *removing* r**esolvconf**.

bump!

sorry Iowan,,, what does nameserver effects us?
Well, in this static and dhcp case,

I remember about one single pc could have multiple nameserver,
what's the effect for that anyway? 


-pardon me if it out of the topic. ;)
I hope it's still relevant.

---

### Post by lokojones on 2010-08-23
> **jaya28inside said:**
> bump!

sorry Iowan,,, what does nameserver effects us?
Well, in this static and dhcp case,

I remember about one single pc could have multiple nameserver,
what's the effect for that anyway? 


-pardon me if it out of the topic. ;)
I hope it's still relevant.

He mentions nameservers because with that symptoms (having connection, and beeing able to ping remote hosts by IP, but not beeing able to navigate using domain names), it's very likely that the local list of nameservers is not working.

And yes, one computer can have prefered and alternative DNS servers.

If you want a quick fix, you can manually edit resolv.conf and change its permissions so it cant be overwritten :P

---

### Post by jaya28inside on 2010-08-23
well yes, i also read about the description of the resolve.cnf

> 
DESCRIPTION
       The  resolver is a set of routines in the C library that provide access
       to the Internet Domain Name System (DNS).  The  resolver  configuration
       file  contains  information  that  is read by the resolver routines the
       first time they are invoked by a process.  The file is designed  to  be
       human readable and contains a list of keywords with values that provide
       various types of resolver information.

       If this file doesn&#8217;t exist the only name server to be queried  will  be
       on  the  local machine; the domain name is determined from the hostname
       and the domain search path is constructed from the domain name.


I'm kindda bit feel weird, 
no I mean confused a bit.

you just replied, > And yes, one computer can have prefered and alternative DNS servers.

in otherwords,,, all of the nameserver value is DNS IP Target only... rite? 
okay2. 

forgive me if i'm wrong.

---

### Post by Slegge on 2010-09-09
Unless I'm entirely mistaken, you just need to add a dns line at the bottom like so:


```
dns-nameserver 8.8.8.8
```

---

