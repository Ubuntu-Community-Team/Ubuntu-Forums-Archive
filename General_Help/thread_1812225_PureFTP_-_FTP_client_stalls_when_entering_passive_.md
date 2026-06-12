---
title: "PureFTP - FTP client stalls when entering passive mode"
date: 2011-07-26
forum: General Help
---

### Post by MockY on 2011-07-26
I successfully installed PureFTP on one of my Ubuntu servers and even with correct server settings, any client (tried 2 on Windows and 3 on Linux) times out when entering passive mode. The behavior is the same as if the ports on the router for the passive port range would not be opened. However, they are. I can connect with a client within the LAN just fine, so I know that the PureFTP install was done successfully and the virtual accounts set up in a functioning manner. 

So something is not properly functioning once connecting from outside the LAN. So I wonder if I'm missing something other than opening the designated port number as well as the passive port range.

**Server LAN IP:** 192.20.20.21

_Files in /etc/pure-ftpd/conf and its contents_

**Bind**
,35

**ForcePassiveIP**
192.20.20.21
[B]
PassivePortRange[/B]
50100 50150

_Router Ports Open_
TCP/35
TCP 50100-50150


Is there some other port I am missing or setting? Again, connection within the LAN works just fine, but not outside, indicating issues with the router settings. But other than opening ports, is there something I am overlooking?

---

### Post by jim_deadlock on 2011-07-26
You need to set up ***port forwarding*** on your router to tell it which local IP (192.168.x.x) your FTP service is running on. [COLOR="Red"]_[portforward.com]("http://portforward.com")_[/COLOR] is a useful site for instructions.

---

### Post by MockY on 2011-07-26
I stated in the original post that port 35 and the passive port range 50100-50150 is already forwarded (open) to this machine (in this case 192.20.20.21). And since it still does not work, I'm wondering if there is something in the PureFTP settings I am bypassing.

---

### Post by jim_deadlock on 2011-07-26
192.20.20.21 is your external IP address.

The computer that your FTP service is running on has a ***local*** IP address (probably 192.168.1.x). Connections from outside will not be able to connect to your FTP service until you tell your router what local IP address your FTP service is running on - this is done in the *port forwarding* section of your router settings. Setting your port numbers is not sufficient, and by the way those port numbers may give you further problems, the standard FTP ports are 20 and 21.

You can find your local IP by running 'ifconfig' in a terminal.

---

### Post by MockY on 2011-07-29
> **jim_deadlock said:**
> 192.20.20.21 is your external IP address.
It most certainly is not. Again, my LAN address of the server in question is **192.20.20.21** (I have multiple servers in the same subnet that serves many different services to the WAN already, where the last octet ends with 18, 19, and 20). I in fact have 3 different subnets within the same network behind a smoothwall, where the third octet is 10 (which I use for the machines in the house to protect it from the network where the publicly available servers are), and 30 (where I have all Wireless connections) respectively. It kind of seems to me that both of you assume that the first 2 octets in a LAN address must start with 192.168

OT, I can connect from a remote machine to this server and authenticate just fine. This would not occur at all if the forwarding of the control port (which I set to 35) was not working properly. It's when the client enters passive mode where it hangs. It in other words behaves exactly the same as if the ports used were not forwarded, which they actually are. I'm very baffled and because of this, my suspicion is that I am missing something in the PureFTP setup.

---

### Post by jim_deadlock on 2011-07-29
The only other thing I can think of is maybe try using the standard FTP ports (20,21) and see if that has any effect. I have pureFTP running on one of my ubuntu computers (via router) without any problem, all standard settings, so I know it should definitely work.

Apart from that I'm out of ideas and it seems you're not getting much of a response on here, so I would recommend trying at [http://forums.cpanel.net]("http://forums.cpanel.net") good luck with it.

---

