---
title: "Synergy - Ubuntu / Winxp"
date: 2011-01-11
forum: General Help
---

### Post by Gordonisnz on 2011-01-11
Hello. I had Synergy up & running before - but one pc broke. I've now had it repaired, & re-installing / setting up Synergy.

Client :- Ubuntu
Main pc = Winxp.

I've done a 'ifconfig' on ubuntu, & found my "inet addr" - & using that for synergy.

How / which ip do i use on winxp - "ipconfig" ??

Server starts - but i get *no* error messages at all - & no connection

---

### Post by Alan James on 2011-01-11
What are the ipaddresses of each? Copy paste all of what ipconfig on Windows prints out on here so we can see what's going on.

Also, make sure that the screens are named and configured properly on the server.

---

### Post by howefield on 2011-01-11
As an alternative to IP addresses, you can also use the machine names.

---

### Post by Gordonisnz on 2011-01-11
WIN XP :- IPCONFIG


Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

D:\Documents and Settings\gordon>ipconfig

Windows IP Configuration


Ethernet adapter VMware Network Adapter VMnet8:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.119.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter VMware Network Adapter VMnet1:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.116.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

D:\Documents and Settings\gordon>

---

### Post by Gordonisnz on 2011-01-11
LINUX BOX 


gordon@gordon-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:1d:52:c0  
          inet addr:192.168.0.134  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe1d:52c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:283280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:403475812 (403.4 MB)  TX bytes:13514294 (13.5 MB)
          Interrupt:27 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23874 (23.8 KB)  TX bytes:23874 (23.8 KB)

---

### Post by Grenage on 2011-01-11
As Howefield mentioned, you can use hostnames:

```
section: screens
	ubqd:
	nwdiag:
end

section: links
	ubqd:
		left = nwdiag
	nwdiag:
		right = ubqd
end
```

This is from a Linux machine; I presume that XP has a GUI as well as config files.

---

