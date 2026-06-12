---
title: "internet connection problem"
date: 2010-04-25
forum: General Help
---

### Post by nos09 on 2010-04-25
ok here is the problem .. i have installed ubuntu in my pc but was not able to connect to internet with my new broadband connection (which sucks ) so i installed windows 7 and tried and i succeed but i have no idea how to do it on linux !

i want to get rid of this windows. but first i want to make sure that my internet connection is working properly with this. so i made myself a bookable usb stick to mess with internet until I get a final solution.

i m giving some screen shot to describe which type of connection i m having right now in windows 7 :confused:

---

### Post by dino99 on 2010-04-25
google about your modem+ubuntu

into ubuntu goto system-pref-network and tweak your settings

info with ifconfig into console

---

### Post by nos09 on 2010-04-25
> **dino99 said:**
> google about your modem+ubuntu

into ubuntu goto system-pref-network and tweak your settings

info with ifconfig into console

i tried to tweak settings all night long a lot but no luck !!!
and also tired to google but it says it should work with it ?!?!:P

and can you help me if i give you all the screen shots of how i did connected internet in windows 7 ? it would be a lot easier for me 'caase i m little dumb !:lolflag:

and btw thanks for quick reply

---

### Post by -humanaut- on 2010-04-25
> **nos09 said:**
> :


Love the Green Day Avatar buddy! 

if your in windows can you run command and type ipconfig -all and post it back here if in Ubuntu type ifconfig in a terminal and post back please

---

### Post by pqwoerituytrueiwoq on 2010-04-25
network connection icon connection is at the top right of the screen
are you using wireless or hardwire
the command "lspci" can tell us what hardware you have
edit
*i think it is hardwire link speed is 100 not 54*

---

### Post by nos09 on 2010-04-25
> **-humanaut- said:**
> Love the Green Day Avatar buddy! 

if your in windows can you run command and type ipconfig -all and post it back here if in Ubuntu type ifconfig in a terminal and post back please

Thanks green day is my fav.

C:\Users\hardik>ipconfig -all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : hardik-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

PPP adapter Broadband Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadband Connection
   Physical Address. . . . . . . . . :
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 117.198.165.195(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 218.248.255.212
                                       218.248.255.139
   NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet
 NIC
   Physical Address. . . . . . . . . : 00-19-21-1E-90-B9
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d42d:ed50:bb2f:499%11(Preferred)
   Autoconfiguration IPv4 Address. . : 169.254.4.153(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   IPv4 Address. . . . . . . . . . . : 192.168.1.1(Duplicate)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 234887457
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-13-66-1D-15-00-19-21-1E-90-B9

   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:75c6:a5c3::75c6:a5c3(Preferred)
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 218.248.255.212
                                       218.248.255.139
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Teredo Tunneling Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:82e:30ac:8a39:5a3c(Prefe
rred)
   Link-local IPv6 Address . . . . . : fe80::82e:30ac:8a39:5a3c%20(Preferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.{122574D6-CD3E-4BF0-98DF-56664A84A2DD}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
[/QUOTE]

---

### Post by -humanaut- on 2010-04-25
Your modem card is support i have the same one are if your running through a router you could try enabling DHCP.

---

### Post by nos09 on 2010-04-26
i got it worked with backtrack with " sudo pppoeconf" command..
but why i couldn;t get it work with ubuntu !

---

### Post by awax on 2010-04-26
I am having the same hassel, just installed Ubunt 9, my first attempt at Linix. I need to connect to the internet via an 3G express card provided by the Australian Telstra/Bigpond. Any help appreiated.:)

---

### Post by nos09 on 2010-04-29
hey guys problem solved : there is the bug in ubuntu 9.10 for pppoe
and i get it worked under kubuntu 10.4 with the same command of course !!

---

### Post by gordintoronto on 2010-04-29
> **awax said:**
> I am having the same hassel, just installed Ubunt 9, my first attempt at Linix. I need to connect to the internet via an 3G express card provided by the Australian Telstra/Bigpond. Any help appreiated.:)

Welcome aboard!

It would be a good idea to start your own thread, since your problem is completely different from the Original Poster.

By the way, you installed Ubuntu 9.04 or, more likely, 9.10.

---

