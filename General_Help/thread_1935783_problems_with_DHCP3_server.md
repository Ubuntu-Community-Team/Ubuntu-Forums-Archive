---
title: "problems with DHCP3 server"
date: 2012-03-05
forum: General Help
---

### Post by Justeri on 2012-03-05
Hi,
 
I want to setup local dhcp3 server which returns for example ip address for my FTPS server ( option 66 ) . I don't want to get ip for my self :)
 
I have two network card and DHCP3 server is set to correct interface
 
INTERFACES=&#8221;eth0&#8243;
 
and this interface is configured like below

[INDENT]auto eth0
iface eth0 inet static
address 192.168.1.0
netmask 255.255.255.0
[/INDENT]dhcpd.conf is the following

[INDENT]default-lease-time 600;
max-lease-time 7200;
 
option domain-name "xxxxxx.com";
 
subnet 192.168.1.0 netmask 255.255.255.0 {
option server-name "xxxxxxx";
}
 
[/INDENT]Is this looking like it should?? BTW: Do I need to set subnet at all, could i just list all needed options without subnet definition?
 
Could you please help me how I can test this somehow or what I have done incorrectly.
 
I have tried** pump -i eth0** and **dhcping -s xxx commands** but i do not receive answer from eth0.
 
Thanks in advance.

---

### Post by Iowan on 2012-03-05
Closed - duplicate:
[http://ubuntuforums.org/showthread.php?t=1936021](http://ubuntuforums.org/showthread.php?t=1936021)

---

