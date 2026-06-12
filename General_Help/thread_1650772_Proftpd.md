---
title: "Proftpd"
date: 2010-12-22
forum: General Help
---

### Post by Mladen80 on 2010-12-22
Hello,
I am very new on Linux distribution and i need some help.
I use Ubuntu 10.10 and setup Proftpd apps which i would like to use to access to my files  from outside of my SOHO LAN network.
This is work on LAN very well but from outside i get some error msg. However i establish connection with my Ubuntu FTP Server machine but i can't get list of files and folders on server.
I get this error msg:
*227 Entering Passive Mode 89,216,116,8 243,96 *--> i know what this no means: my Stat IP and the port 
[I]
500 Illegal Port Command
Get Directory

FTP Port Command failed
[/I]
Some Additional Information:
On the edge of SOHO LAN i use Cisco router for access to the Internet. 
NAT is configured, PAT (NAT overload) is configured also. 
I forward ports which i needed for FTP: 21 and 20, and passive ports 60000 - 60001.

When i use Windows OS and BUlletProof FTP server (port 21 or some custom port i.e. 65021) i only forward that port (21 or custom port i.e. 65021) and everything works great.

Please, can anybody help?!

---

### Post by Whyzer on 2011-01-01
just for giggles try using a browser to access it. the syntax is
[ftp://username:password@YourIPAddress:21](ftp://username:password@YourIPAddress:21) 
Personally I use a free dyndns.org account so I don't have to remember IP addresses (unless yours is static) and then just enable the MasqueradeAddress line in proftpd.conf 
example 
MasqueradeAddress      yourhostname.dyndns-home.com
then you just substitute that for your IP address.
I don't know if this will solve your problem.
I also never use port 21, way too many ftp sniffers try to get in, I changed my port to 1234 and just used the passive ports that are already in proftpd (60000 - 65534 i think).

---

