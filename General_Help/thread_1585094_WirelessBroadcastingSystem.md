---
title: "WirelessBroadcastingSystem"
date: 2010-09-30
forum: General Help
---

### Post by ngibuhenua on 2010-09-30
This is a bit old but I've been trying to follow this and have had some issues. I'm not very experienced with Linux.

[https://help.ubuntu.com/community/WifiDocs/WirelessBroadcastSystem](https://help.ubuntu.com/community/WifiDocs/WirelessBroadcastSystem)

I have it working - almost. I can connect to the AP with another computer, which is given an IP address in the right range, and by default the index file in /var/www appears in the browser. But I can't go anywhere else. I want to be able to browse an installation of Wordpress on the server, but it won't display it. I think it is an issue with permissions. I set ErrorDocument 404 to the Wordpress index file and it just returns a strange error

I used Ubuntu 10, latest versions of LAMP and dnsmasq, all installed with apt-get. No problems in the install. I'm not using a wireless adapter on ath0 but rather a machine with two NICs, and with an access point on the eth1 network. I set the interface in dnsmasq.conf to eth1 and gave eth1 a fixed IP 10.0.0.1.

---

