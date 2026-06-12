---
title: "Firestarter &quot;The device ppp0 is not ready&quot;"
date: 2011-10-19
forum: General Help
---

### Post by bala150985 on 2011-10-19
I have two types of internet connection, one with ADSL modem from there cat5 cable goes to my eth0 and I get an IP using DHCP, with this connection I get ppp0 interface and my firewall firestarter starts successfully.

Now coming to my second type of connection where in my eth0 gets a direct cat5 cable.  In this scenario Firestarter refuses to start. 

This is the error message which I got.

the device ppp0 is not ready. pls check your network device settings and make sure your internet connection is active.

I found exactly the same problem in the link [http://ubuntuforums.org//showthread.php?t=267324](http://ubuntuforums.org//showthread.php?t=267324)  However my problem is still not solved after following what is given on that link.

---

### Post by bala150985 on 2011-10-19
Found one small work around to get the firewall started.  Change IF from 'ppp0' to 'eth0' then try to start the firewall, it starts normally.  However this configuration evaporates if I restart the system :confused:

Edit this file as sudo user /etc/firestarter/configuration

#-----------( Firestarter Configuration File )-----------#

# --(External Interface)--
# Name of external network interface
IF=**"eth0"**
# Network interface is a PPP link
EXT_PPP="off"

# --(Internal Interface--)
# Name of internal network interface
INIF="eth1"

---

### Post by 3rdalbum on 2011-10-19
If your ADSL modem connects to your computer via Ethernet, then your computer is on a different network to the rest of the Internet.

This is a good thing - it means that incoming connections from the internet can't find your computer unless you have forwarded a port.

If incoming connections from the internet can't reach your computer, then you have no need for an additional firewall.

---

### Post by collisionystm on 2011-10-19
> **bala150985 said:**
> I have two types of internet connection, one with ADSL modem from there cat5 cable goes to my eth0 and I get an IP using DHCP, with this connection I get ppp0 interface and my firewall firestarter starts successfully.

Now coming to my second type of connection where in my eth0 gets a direct cat5 cable.  In this scenario Firestarter refuses to start. 

This is the error message which I got.

the device ppp0 is not ready. pls check your network device settings and make sure your internet connection is active.

I found exactly the same problem in the link [http://ubuntuforums.org//showthread.php?t=267324](http://ubuntuforums.org//showthread.php?t=267324)  However my problem is still not solved after following what is given on that link.


Okay, so you are plugging your computer directly into the modem?

Do this

> I have two types of internet connection, one with ADSL modem from there cat5 cable goes to my eth0 and I get an IP using DHCP, with this connection I get ppp0 interface and my firewall firestarter starts successfully.

Open terminal, 

Ifconfig eth0

inet addr:172.16.64.10

Post the output of your inet addr: but please only do the first 2 categories.

I.E. 64.83.xxx.xxx

Use the x's.

I want to see what kind of IP you are getting. You should be getting an Internet visible IP address with that setup. Good reason to have a firewall enabled.

---

### Post by lovinglinux on 2011-10-19
I am not sure about your particular configuration needs, but I would recommend removing Firestarter and installing Gufw, which is a frontend for UFW, the default firewall manager.

---

### Post by bala150985 on 2011-10-27
You are absolutely correct [3rdalbum]("http://ubuntuforums.org/member.php?u=61044"),  Till now I had a public IP of 122.164.x.x landing on my machine when I am using ADSL connection and recently I switched over to a configuration where in the public IP stays on my modem and I just get a private IP on my machine.

---

### Post by bala150985 on 2011-10-27
[collisionystm]("http://ubuntuforums.org/member.php?u=1249225") up until now I use to get 122.164.x.x IP on PPP0 when I am using ADSL and 113.x.x.x IP on eth0 when I use direct cat5 cable.

Now I have made some configuration changes on my ADSL so that I just get private IP on my machine when I use ADSL.

---

