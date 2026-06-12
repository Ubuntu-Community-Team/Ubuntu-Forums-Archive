---
title: "Samba has stopped working."
date: 2012-02-24
forum: General Help
---

### Post by jamesm46 on 2012-02-24
I am running Ubuntu 11.10, and using samba, it ***WAS*** sat happily as a file sever for several Windows Vista/7 PC's. I have a DLink Router acting as an Internet Gateway and a DHCP Server. I was Happily running on IP Range 192.160.0.1 - 255 on a Subnet of 255.255.255.0 With the router as 192.168.0.1 and the Ubuntu Box a fixed IP of 192.168.0.110.

For many reasons (mainly because I want to install openvpn) I changed the Subnet that the whole lot works on. to use 10.7.1.0 - 10.7.1.255 (255.255.255.0) The router is Now on 10.7.1.100 and the Ubuntu box is on 10.7.1.110 everything is working fine EXCEPT Samba, the Unbuntu box has Disappear from "Network" on the Windows PC's.

I have got desperate enough, to uninstall iptables, UFW, and samba, them reinstall them and have started the Samba config from scratch, and still I cannot get it to appear on the Windows PC's

This a copy of my *smb.conf* file at the moment.

[global]
netbios name = Father1
workgroup = CCS
security = user
server string = CCS File Server

[CCS-Common]
path = /var/CCSshares/Public
comment = CCS Members Common Share
valid users = ccsadmin jamesm robinac arnoldb markr beng jeanh ginnyb danm
write list = ccsadmin jamesm robinac arnoldb markr beng jeanh ginnyb danm
read only = no
available = no
browseable = no
writable = no
guest ok = yes
public = no
printable = no
locking = no
strict locking = no

If have have missed something, to with the change in the IP Addressing, but what?

---

### Post by wyliecoyoteuk on 2012-02-24
available = no
browseable = no
writable = no

At a first glance, these settings should be yes.
I'd also set 

locking = no

to yes.

Remember with SMB/CIFS browsing changes can take up to 15 minutes to refresh.

Are your DNS settings right?

Also, make sure that the users can access /var/CCSshares/public.
Just a comment, but I would use /home instead of /var for shared folders, but that's just my preference.

---

