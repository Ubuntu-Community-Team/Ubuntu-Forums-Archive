---
title: "Unresolved Network/Firestarter Issue"
date: 2011-12-11
forum: General Help
---

### Post by UltimateCat on 2011-12-11
I still have not been able to get Ubuntu 10.04 Ultimate Edition 2.7 onto the internet.
 Here's what I have done and what the terminal has given me.
 In Firestarter I went in Edit, Preferences, Network Setting and saw ethernet device already showing and checked Enable DHCP.
 Firestarter cautions me.  Failed to start firewall device etho is not ready.
 In Netword Admin under “Wired” I put in the Mac address. I ran the Wizard as well and completed that.
 Firefox says : Offline mode
 Under “Wired” it says Auto etho...Should I leave that alone or edit it to something else?
 Under “Wireless” I filled in the fields for SSID, BSSID, Mac and set Mtu to automatic.
 Then I filled in the “DSL” service and password. I no longer have the old USB device from Criket.  Could that still be in the terminal and causing me this problem?
 I downloaded the driver for the RT73 to accommodate the adapter but I did not install it because for one I don't want to wreck my OS and the Windows XP side of my partition works just fine with my wireless connection.  
 I didn”t have to install the software that came with the adapter because the wireless signal on Windows showed and was very strong.  I am a newbie so if there is something I should do, I'm asking for some enlightment. Also I didn't uninstall the UFW because I have to learn how to do that.
 When I typed sudo iwconfig into the terminal it asked for my password, I typed it in and got nothing else: no other message or anything came up except my name.
 My husband encouraged me to type into the terminal ip addr   and this is what I saw:
 1:<LoopBACK, up, LOWER_up>mtu 16436 qdisc no queue state UNKNOWN
 link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00:
 intel 127.0.0.1/8scope host lo intel 6 : : 1/128 scope host calid_ lift forever preferred_1ft forever
 2:etho: <No-Carrier, BROADCAST, MULTICAST, up> mty 1500 qdisc pf ifo_ fast state DOW N qlen1000
 link/ether 00:21:85:66:7a:d1 brd ff:ff:ff:ff:ff:ff
 3:wlano:<NO-CARRIER, BROADCAST, MULTICAST, up> mtu 1500 qdisc mq state DOWN glen
 1000
 link/ether 00:23:69:d7:3f:of brd ff:ff:ff:ff:ff:FF
 I do not understand most of this.  Please be as specific as possible.  Any help would be very much appreciated as my head is spinning and am very close to my wits end.  :(
 Thanks in advance:)

---

