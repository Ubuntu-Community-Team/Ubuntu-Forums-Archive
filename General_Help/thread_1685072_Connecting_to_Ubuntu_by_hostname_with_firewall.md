---
title: "Connecting to Ubuntu by hostname with firewall"
date: 2011-02-10
forum: General Help
---

### Post by dstein on 2011-02-10
When I enable a firewall on my Ubuntu machine using gufw, I am able to ping the machine from Windows using its IP address, but I am unable to ping it using a hostname. I can ping by hostname if the firewall is turned off, or if the firewall is turned on it will ping the Ubuntu machine by hostname only if I did so at some earlier point when the firewall was off and I had not shut down since.

Any help with configuring the connection to the Ubuntu machine by hostname while the firewall is turned on would be greatly appreciated. I would like to access open ports using a hostname since I have not set up static IP addresses. Thanks.

---

### Post by gmargo on 2011-02-10
Sounds like the windows box is going through the linux box to get it's dns.  So you might need to open port 53. (A description of your network layout might help.)

Easiest way to find out which port is to inspect your **/var/log/syslog** file, where **ufw** logs a message for each blocked packet.

Sample:  Here's my windows box trying to come in on port 135:
Feb  8 07:31:21 bohr kernel: [246124.041833] [UFW BLOCK] IN=eth0 OUT= MAC=[snip] SRC=192.168.1.7 DST=192.168.1.8 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=24364 DF PROTO=TCP SPT=51307 [COLOR=Red]DPT=135[/COLOR] WINDOW=8192 RES=0x00 SYN URGP=0

---

