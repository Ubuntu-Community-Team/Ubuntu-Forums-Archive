---
title: "Ubuntu Won't Connect to the Internet"
date: 2010-06-04
forum: General Help
---

### Post by Bradj47 on 2010-06-04
After upgrading to Ubuntu 10.04, I'm not able to make any connection to the internet with either my netbook through WiFi or my computer on wired LAN. I can, however, ping my Solaris machines and Macbook. How do I fix this?

---

### Post by fragos on 2010-06-04
Right click the network manager icon and insure Networking is enabled. You can also edit connections from here.

---

### Post by Bradj47 on 2010-06-04
> **fragos said:**
> Right click the network manager icon and insure Networking is enabled. You can also edit connections from here.

I know networking is enabled because I can ping my other non-ubuntu computers.

---

### Post by fragos on 2010-06-04
Try powering down your modem, router and Ethernet connected PC completely and then power up again to initialize. Note that on your PC Shutdown doesn't completely power down your system and you'll need to do that so that DCHP will get new DNS settings rather than falling back on the old ones.

---

### Post by Bradj47 on 2010-06-04
No, I figured everything out. I first assigned myself a fixed IP on my local network by running **ifconfig wlan0 xxx.xxx.x.xxx netmask 255.255.255.0** then I changed my default route by running **sudo route add default gw 192.168.1.1**
Thanks anyway, though.

---

### Post by fragos on 2010-06-04
FYI: if you power down that PC when it powers up it may get a different IP in the 192.168.1.0-255 series.

---

### Post by Bradj47 on 2010-06-05
> **fragos said:**
> FYI: if you power down that PC when it powers up it may get a different IP in the 192.168.1.0-255 series.

Yeah, I found that out the hard way. Everything reset after I rebooted. How do I get my route and IP set permanently?

---

### Post by RJ12 on 2010-06-05
You might be able to make it in a script and have it run on start up, I don't know how to make it run on startup though.

---

### Post by fragos on 2010-06-05
> **Bradj47 said:**
> Yeah, I found that out the hard way. Everything reset after I rebooted. How do I get my route and IP set permanently?

edit /etc/rc.local to add commands needed to run at the end of boot time.  rc.local runs as root so sudo isn't required.

---

### Post by Bradj47 on 2010-06-05
> **fragos said:**
> edit /etc/rc.local to add commands needed to run at the end of boot time.  rc.local runs as root so sudo isn't required.


Thanks. I'm assuming that will work. But now I have yet another problem. It turns out that the route command on worked with the wifi. It had no effect when I tried it on my desktop computer and when I plug an ethernet cable into my netbook the network icon gives that little loading symbol with the two dots and the blue thing going between them then after a while the alert box in the upper left hand corner comes up and says "No network connection" or whatever it says when there is no network connection. Now what's wrong?

---

### Post by fragos on 2010-06-05
Not sure on that. Let me offer a substitute for numerical IP's on your local network. All your PC's should have a unique hostname. They can be adressed as "{hostname}.local" as in my case my nain PC is "Geo" and it can be addressed on my LAN as "Geo.local" which allows the actual IP to be reassigned by DCHP.

---

### Post by Bradj47 on 2010-06-05
> **fragos said:**
> Not sure on that. Let me offer a substitute for numerical IP's on your local network. All your PC's should have a unique hostname. They can be adressed as "{hostname}.local" as in my case my nain PC is "Geo" and it can be addressed on my LAN as "Geo.local" which allows the actual IP to be reassigned by DCHP.

I don't have much control over that. I'm not the network admin. I only have root access to my two Ubuntu computers. Besides, how will that help? My computers already have hostnames and I usually refer to them when I ssh or ftp. I don't see how enabling DHCP will help me at all. I think it would only make things worse meaning I won't be able to ssh/ftp to my different machines by referring to them by hostname. I already have a whole list of hostnames and IPs in my /etc/hosts files.

---

### Post by fragos on 2010-06-05
I recommend you talk to the administrators of your network. It is they who determine the use of DCHP, DNS and IP addresses. The value of DCHP is that if supported in your network it makes most settings for you. All major ISP's all use DCHP, for example Comcast and AT&T. Some administrators prefer static IP's to directly identify particular pieces of equipment and their physical location with them. They accept the configuration complexity that this approach places on them as a fair trade off.

---

