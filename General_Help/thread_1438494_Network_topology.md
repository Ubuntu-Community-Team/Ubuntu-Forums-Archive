---
title: "Network topology"
date: 2010-03-25
forum: General Help
---

### Post by nyu2007 on 2010-03-25
Dear all,

I need advices from my friends :p

I have over 500 PCs on my system.
I already setup an PDC, BDC, DNS, Mail, and some services.

Clients use Windows OS and my systems was infects by virus

My question is:

- Is the best solution for manage PC's, VLAN is one of?
- .....

Thanks for your help.
NyU

---

### Post by Gregorybekkers on 2010-03-25
Does all 500 clients need the same applications and servers?
are they at one location?
do you want your servers Linux or windows based?
how many servers you wanna setup?
do you want redundancy?
do you want it all open source?

Regards,

Gregory

---

### Post by nyu2007 on 2010-03-25
Dear Gregory,

All 500 clients at one location, use same application and servers.
All servers I already setup on Ubuntu distro 8.04LTS
All clients using WinXP.

My range DHCP is 172.16.0.x  to 172.16.3.x so it broadcast many. And my some clients was infect virus. Anh I want to change my system to other topo. 

Thanks for your respon.
NyU

---

### Post by yeleek on 2010-03-25
Change of network topology won't help if traffic such as netbios/smb/ftp is open between all your clients as a virus would spread easily via these means.

If the purpose of the question is to reduce broadcasts then yes smaller vlans will help

If the purpose of the question is to reduce risks of viral transfer, then you need to look at what traffic you allow between your hosts.

---

### Post by Gregorybekkers on 2010-03-25
Use smaller Vlan's but make sure they can connect to your servers.
how many server do u have?
Do you wanna use an Active Directory stucture?

---

### Post by nyu2007 on 2010-03-25
I have 
PDC (Bind9, Dhcpd, Samba, OpenLDAP,..) 
BDC (Backup for PDC)
Mail (Zimbra ZCS)
File (Samba share file) and some servers for my apps
Some VMWARE host for Symantec Anti Management and WSUS for WinXP clients

My solution is small VLAN for Servers, and every department was VLAN. 
- Have an ACL for VLANs every dept can router to Server VLAN and every dept VLAN can not router to other.
- An server good performance to router every VLANs (Linux distro)
- Have and DHCP service to release IP for every VLANs

Any suggestion?

Regards,
NyU

---

### Post by yeleek on 2010-03-26
What is it you are trying to achieve?

---

