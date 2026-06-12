---
title: "Networking Problem with Slackware on VirtualBox on Ubuntu 11.04 as host"
date: 2012-04-11
forum: General Help
---

### Post by wannabelinuxgeek on 2012-04-11
Hi

I have successfully installed Slackware 13.1 in virtualbox.

But,now I see that I can't connect to the internet in the virtualbox. The host OS is Ubuntu 11.04 and Virtualbox guest additions are installed and configured on Slackware 13.1 which is the host OS running on VirtualBox.

I am connected to the internet through wifi on my host.but my Guest is unable to connect to the internet.
I have tried NAT and Bridged Adapter settings on VirtualBox but still i am unable to connect to internet on my Host.

How do I proceed to configure the internet connection on Slackware 13.1 (running on VirtualBox)?

The result of route and ifconfig commands on guest(Slackware) are below.

#route:
Kernel IP routing table
Destination Gateway Genmask   Flags Metric Ref Use Iface
loopback       *    255.0.0.0   U     0      0  0  lo

#ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

Any help would be appreciated.

P.S. This is my first post on ubuntuforums so excuse me if its in wrong place.

---

### Post by Herpythebrony on 2012-04-11
You might want to take a look at this.

[http://www.linuxquestions.org/questions/slackware-14/slackware-13-37-no-internet-connection-911329/](http://www.linuxquestions.org/questions/slackware-14/slackware-13-37-no-internet-connection-911329/)

---

### Post by wannabelinuxgeek on 2012-04-11
@ Herpythebrony thanks for instant reply but
I am using Slackware on virtualbox.My host OS (Ubuntu 11.04) is connected to internet.my problem is on my Guest OS (Slackware 13.1).

---

### Post by Herpythebrony on 2012-04-11
> **wannabelinuxgeek said:**
> @ Herpythebrony thanks for instant reply but
I am using Slackware on virtualbox.My host OS (Ubuntu 11.04) is connected to internet.my problem is on my Guest OS (Slackware 13.1).
IT worked for me when I used slackware in virtual box.

---

