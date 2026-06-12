---
title: "a intresting problem of pptp and windows firewall"
date: 2006-03-20
forum: General Help
---

### Post by boliang319 on 2006-03-20
My linux pptp client cannot connect to my VPN server which is a windows server 2003 system.
My linux system is ubuntu 5.1 which has supported the mppe as someone says in the forum. and I configed my pptp clent by using pptp client.
Sometimes, I can connected to the server successfully, but by almost all the time it failed.
I have read the docs on the website [http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/). And as it saying on its website, I installed ethereal to monitor the network packets exchanging between my linux client and the server.
I found a intresting problem: when I turn on the firewall of the server, the pptp connect must be failed, because a packet called "Outgoing-call-reply" cannot be received by the client, but all will be Ok when I shutdown the firewall.
I have also monitered the packets exchanges between a windows pptp client and the server, the windows pptp client can receive the "Outgoing-call-reply" seccessfully whenever the firewall is on or off. 
By the way,  My VPN server is  windows server 2003 system(SP1), and I configed the VPN and NAT service by the guid of the system provided. The firewall is seted on the outgoing interface.
here is the error informations of my pptpclient :
==================================================
using channel 9
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x2d312b58> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
===============================================
and in the accessory, there are two files of packetes captured by ethreal.

---

