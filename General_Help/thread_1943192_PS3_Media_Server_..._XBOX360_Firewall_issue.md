---
title: "PS3 Media Server ... XBOX360 Firewall issue"
date: 2012-03-19
forum: General Help
---

### Post by tavrion on 2012-03-19
Hi.  I have reached the end of my search and about to give up.  Hopefully someone here has had a similar experience and able to help.  Fingers crossed!

I am running Ubuntu 11.04 and PS3 Media Server 1.50.2 which claims to support xbox 360.

Everything is running fine from the PS3 but whenever I try to to view files from my Xbox, I get an error about a firewall and that the xbox is unable to connect.  This would be a nice option seeing that I will not have to run another server (ushare?) to accommodate my xbox, but from other threads it appears that ushare has similar issues.  


When I search the network from the xbox it does find the server, but that is as far as it goes.  From the PS3 Media Server interface - it detects the xbox! So something is blocking connection or something needs to be configured?

Any ideas please?  :confused:

---

### Post by syerges on 2012-05-06
Mine only works on both XBox 360 and playstation 3 with the following settings exactly...if i change any of them, then it stops working.
USHARE_OVERRIDE_ICONV_ERR=yes
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no


The enable_dlna really messed me up because it says ps3 won't work without it, but it's wrong. also make sure to look up your xbox and ps3 ip addresses and open up the port to them from your pc.

My computer's IP address was found by right clicking on my internet connection and then clicking on "connection information" and it is 192.168.0.11

My Xbox and PS3's IP addresses were found by going to network settings, they are 192.168.0.10 and 192.168.0.13 so I had to use the following codes in terminal. sorry, don't know how to do that code thing here....

You need to find the port you used for the port.

sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.10 port 49153
sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.13 port 49153

---

