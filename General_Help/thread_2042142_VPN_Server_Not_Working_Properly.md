---
title: "VPN Server Not Working Properly"
date: 2012-08-14
forum: General Help
---

### Post by Zukaro on 2012-08-14
I've set up a PPTP VPN server on Ubuntu 12.04, it works but only on the LAN (I can't connect to it using my public IP address).

The way my network is currently set up I've got three different networks; 192.168.1.1 is in the middle (and is also the one with Internet connection, giving it to the other routers), then there's the network I'm on and finally the one the VPN is behind.  I'm able to connect to the VPN using 192.168.1.100 (the IP address of the router the VPN is behind), but using the IP address of the router in the middle doesn't work, so I'm not sure if this is related somehow to my public IP address not working.

Despite being able to connect, it disconnects after just a few minutes and I'm also unable to access the Internet (it will try to load the page but it never loads until after the VPN has lost connection).

I've put the VPN behind a DMZ to try and rule out ports being the issue although that hasn't fixed anything.

After putting my VPN on a DMZ I'm unable to connect to SSH using the public IP address anymore (and instead need to connect using 192.168.1.100).



I've been looking on Google for a few hours about the VPN issues and I haven't gotten anywhere.  The closest I've got to figuring it out is a post about how a Linksys WRT54G V4 with factory firmware or DD-WRT firmware can't forward GRE 47 from WAN to LAN (it can be done using the DD-WRT VPN firmware though).  My router (on the 192.168.1.1 network) is a WRT54G2 V1.5, so I don't think it'd be affected by this (I could be wrong however, so I'm going to test bypassing it in a little while).

---

### Post by Zukaro on 2012-08-14
Does anyone know what the problem is?

(I have yet to swap out that other router as I'd need to replace it with another one or change all the IP addressed used with the VPN to be on the 192.168.1.1 network (I'll be swapping it out sometime soon if I have to))

---

### Post by rukiaEnix on 2012-08-14
Hello, will it be too much if you could upload a small diagram of your network?

To understand better.

---

### Post by Zukaro on 2012-08-14
I've attached a diagram.

All routers have NAT enabled (I know, I should fix that :P I'm gonna make some changes to my network eventually).  Router C has a DMZ set up for the VPN and Router A has it's ports forwarded (I'm going to forward the ports on Router C rather than leave it behind a DMZ eventually however).  I had tested it with both routers using a DMZ for the VPN however.

I've been trying to connect from Router D, and I'm able to do so using 192.168.1.100 (which is what Router C appears as on Router A's network).  I can't use my public IP address to connect however, which is what I need to use.

Also, currently the VPN disconnects after just a few minutes, and wihle connected I can't access the Internet (it tries to load the page but it takes way too long and the VPN disconnects before it's able to).

---

### Post by Zukaro on 2012-08-14
Does anyone have any ideas?

---

### Post by Zukaro on 2012-08-15
anyone?  I can't find anything at all on Google about this (*has been looking for awhile now*)

---

### Post by rukiaEnix on 2012-08-15
Can you ping from the router A (192.168.1.1) to the VPN Server (192.168.3.100)?

---

### Post by Zukaro on 2012-08-15
No.  However, I'm able to access other things I have running on this server (such as SSH) using my public IP address.
(*is confused*)

The router's WAN IP is 192.168.1.100 (the one infront of the VPN server) and I can't ping that from Router A.  However, from another router behind Router A I'm able to connect to the VPN using that IP address (but I'm able to connect to SSH using my public IP address, despite Router A being unable to ping Router C).  I'm guessing the reason I'm able to connect is because of the switch, but that doesn't explain why I'm able to SSH in using the public IP address.

---

### Post by rukiaEnix on 2012-08-15
I think router A isn't reading the 192.168.3.0 network adresses

---

### Post by Zukaro on 2012-08-15
What do you mean?

---

### Post by rukiaEnix on 2012-08-15
How did you configured your routes on the router?. To make things work the A router should be able to ping the C router and therefore the VPN Server

---

### Post by Zukaro on 2012-08-15
I didn't really configure them at all (the only things I changed were the IP addresses).  Basically any router in front of another router can't communicate with the one behind it.  But for some reason I'm still able to get Internet access, and even access stuff behind the router using my public IP address as long as the proper ports are open, so I never bothered trying to set up routes (I can't communicate with them using the IP from their network (for example, 192.168.2.1), I can use their WAN IP however, but for some reason the WAN IP of Router C doesn't seem to be pingable from Router A, yet Router B's is (and so is D's)).

I'm going to fix my network though (remove some of the routers which are currently doing absolutely nothing and actually make routes (and disable NAT one some of the routers which don't need it :P)).  Then if the VPN still doesn't work I'll be back (although I know the VPN disconnects after about a minute and can't really load pages).

---

### Post by Zukaro on 2012-08-15
For some reason when I try to set up routes everything stops working (I get no Internet access and when I try to access the first router it displays text sometimes rather than the GUI).

Also, setting up routes wont fix the fact Router A can't even ping 192.168.1.100 (the WAN IP of Router C (at least, I don't think it will fix it)).



I figured out why I can't ping it from 192.168.1.1; the WAN Ping Response option is set to disabled, so it wont respond to WAN pings (on Router C).  :P

I'm able to connect the same way with SSH (I can connect using 192.168.1.100, but not with 192.168.1.1), the only difference is I can connect using the public IP address for SSH.  I'm guessing my ISP blocks VPN servers from running on their service (although I'm not sure).

If this is the case, is there a way to get around this without having to pay them extra (such as just changing the ports it uses or something similar)?

---

### Post by Zukaro on 2012-08-15
I've called the ISP to find out if they block running VPN servers on our service and they don't.

---

### Post by Zukaro on 2012-08-17
Is there any way to change the ports a PPTP VPN uses?
(I'm using the pptpd package for my VPN)

---

### Post by SeijiSensei on 2012-08-17
If you have a firewall, do you permit TCP connections on port 1723, the port assigned to PPTP?

---

### Post by Zukaro on 2012-08-19
The only firewall I have is the one on my router, and it's set up to allow all the VPN protocols to pass through it (I've also forwarded the ports for port 1723 and 47).

---

### Post by rukiaEnix on 2012-08-20
I still think is the route configurations... Are you using as firewall a Cisco or a Linux machine?

---

### Post by SeijiSensei on 2012-08-20
Try scanning your router from [nmap-online](http://nmap-online.com/) and see if port 1723 is reachable.

---

### Post by Zukaro on 2012-08-22
> **rukiaEnix said:**
> I still think is the route configurations...  Are you using as firewall a Cisco or a Linux machine?

The computer running the VPN server is behind two routers; one is a  DLink and the other a Linksys.  On the DLink it's behind a DMZ (the  ports are also forwarded however) and on the Linksys the ports are  forwarded.  I did try both behind a DMZ however.  Also, both routers allow VPN's to pass through the firewall.

The computer running the VPN server has no firewall on it.

> **SeijiSensei said:**
> Try scanning your router from [nmap-online]("http://nmap-online.com/") and see if port 1723 is reachable.

It says

"Starting Nmap 4.75 ( [http://nmap.org](http://nmap.org) ) at 2012-08-22 17:43 Central Europe Daylight Time
Note: Host seems down.  If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.61 seconds)"

---

### Post by SeijiSensei on 2012-08-22
> **Zukaro said:**
> Note: Host seems down.  If it is really up, but blocking our ping probes, try -PN

Add the parameter "-P0" to the command.  That will disable ping probes and have it just scan using TCP.

Here is the [manual page for nmap]("http://linux.die.net/man/1/nmap").  Anyone who works with networks should have a copy of nmap around for diagnostics.  Install it with "sudo apt-get install nmap".  Nmap-online is a useful site for those who don't have access to an external machine on which to run the utility.

---

### Post by Zukaro on 2012-08-23
> **SeijiSensei said:**
> Add the parameter "-P0" to the command.  That will disable ping probes and have it just scan using TCP.

Here is the [manual page for nmap]("http://linux.die.net/man/1/nmap").  Anyone who works with networks should have a copy of nmap around for diagnostics.  Install it with "sudo apt-get install nmap".  Nmap-online is a useful site for those who don't have access to an external machine on which to run the utility.

Okay.  What do you mean by an external machine?
(just a machine that's not my VPN server for example or a machine not on my home network?)


As for nmap online, it says
"PORT     STATE SERVICE
1723/tcp open  pptp

Nmap done: 1 IP address (1 host up) scanned in 0.87 seconds"

---

