---
title: "VPN access"
date: 2011-04-29
forum: General Help
---

### Post by sierra8804 on 2011-04-29
I have an Ubuntu server 10.10 acting as a file server in a small office.
 
The server receives a static IP from an AT&T DSL wireless modem/router with DHCP. This address is in the range of 65.x.x.x. The other computers in our office receive a dynamic IP via DHCP either wireless or hard wired from the same DSL box.
 
Access to the file server is either HTTP or SSH both on the internal network and the external network. SSH for subversion and HTTP for document versioning. There is some traffic, internally only, using SAMBA.
 
I want to use a VPN connection for external access to improve my security.
 
I installed pptpd using apt-get.
 
I edited the /etc/pptp.conf file and added the following lines at the bottom"
 
localip 65.x.x.x
remoteip 192.168.x.xxx-xxx
 
I edited the /etc/ppp/chap-secrets and added the following:
 
# client server secret IP Address
username pptdp somepassword *
 
restarted the pptpd daemon.
 
It did not work. I can not log in either internally from the local LAN or externally.
 
It doesn't actually refuse my connection it just dies [FONT=Calibri]prematurely.[/FONT]

[FONT=Calibri]I've tried usin both windows XP and MAC OS with no luck.[/FONT]

[FONT=Calibri]Should you be able to log in on the local LAN?[/FONT]

[FONT=Calibri]Since the Ubuntu server is not a DHCP server it really can't give out local IP's. Do I need more static IP's to accomplish this task?[/FONT]

[FONT=Calibri]Any suggestions would be welcome. I'm new at all this.[/FONT]

---

