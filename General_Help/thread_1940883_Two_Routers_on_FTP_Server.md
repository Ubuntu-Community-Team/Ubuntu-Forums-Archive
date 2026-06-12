---
title: "Two Routers on FTP Server"
date: 2012-03-14
forum: General Help
---

### Post by sibleytr on 2012-03-14
[LIST]
[*]Ubuntu 11.10 Server is installed with proFTP and has one NIC connecting it to a switch
[*]Router 1 sits on the public side of the internet and connects to the server via the switch
[*]Router 2 sits on the private side of the LAN and connects to the server via the switch
[/LIST]
Connection looks as follows:
 
R1 WAN (Intern) ----> R1 LAN (172.16.10.254) -->
--> Swtitch ----> proFTP 172.16.10.245
R2 WAN (10.1.1.14) ----> R2 LAN (172.16.10.252) -->
 
The network configuration for the proFTP server is
address 172.16.10.245
gateway 172.16.10.254
 
 
FTP services work for the Router 1 configuration - Our clients can connect and we can connect. 
However, we are wanting to shave a little time off of the upload process (100 mbs vs 10 mbs) so the Router 2 configuratio was deployed for uploading files from the private side of our network to the proFTP Sv.
From the R2 we can ping both the server and other router however we are unable to connect to the server for either the FTP or SSH services. Double and tripple checked the router configuration with no joy.
 
 
 
Is it because the proFTP server uses R1 as its gateway?
Any ideas would be helpful.

---

### Post by papibe on 2012-03-14
My first guess is that you need some custom static routes. If I understand correctly the routers are running a Linux-like OS?

Could you post the routes on both?
```
route -n

ip route show
```
If you're not able to run that on the routers, run it from the ftp server, and a different  machine on the WAN.

Regards.

---

### Post by sibleytr on 2012-03-15
Attached Text file to make the reading a little easier.

ftpNetwork.txt

---

### Post by papibe on 2012-03-15
Thanks.

I took a look at it, and found a few of anomalies.

First, it looks like there's a disagreement  between the server and Router 1 about what is the actual LAN's mask. The server thinks the network 172.16.254.0's mask is 255.255.255.0, but Router1 says 255.255.255.248.

I also noticed a that Router 1 doesn't know the existence of the WAN (10.1.1.0), so any traffic not intended for LAN is route to the Internet (the default route). I would add this route on Router 1:
```
route add -net 10.1.1.0 netmask 255.255.255.0 gw 172.16.254.252 dev eth1
```
Note that the above command is using Ubuntu/Debian's syntax and options. It may be slightly different on the Routers (also I'm assuming eth0 goes to Internet and eth1 to the LAN).

Router 2 is kind of a puzzle to me. The subnetwork routes are OK: it knows where to go for the LAN and WAN. However its default route is oddly pointing to a machine inside the WAN (10.1.1.2). From what I understood, WAN's way to the rest of the world should be Router 1. 

If that's correct, I would replace that route with this one (Router 2):
```
route add -net default netmask 255.255.255.0 gw 172.16.254.254 dev eth1
```
I hope that helps. Tell us what you think and how it goes.
Regards.

---

