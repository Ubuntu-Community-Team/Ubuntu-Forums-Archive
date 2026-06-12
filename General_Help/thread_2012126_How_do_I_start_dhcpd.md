---
title: "How do I start dhcpd?"
date: 2012-06-28
forum: General Help
---

### Post by AlexBooton on 2012-06-28
Hi,

I'm having a bit of trouble getting dhcpd to run as a service.

Here's what I see:
```
root@mbh:/etc# service isc-dhcp-server6 start
isc-dhcp-server6 stop/pre-start, process 1451
```
It would seem the server started but ps -A | grep 1451 doesn't find the service nor does ps -A | grep dhcp!?

If I run from a terminal I get:

```
root@mbh:/etc# dhcpd -f
Internet Systems Consortium DHCP Server 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 1 leases to leases file.

No subnet declaration for nrtap (10.0.0.7).
** Ignoring requests on nrtap.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface nrtap is attached. **


No subnet declaration for eth0 (192.168.1.147).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **

Listening on LPF/eth1/00:26:18:2c:41:f0/192.168.0.0/24
Sending on   LPF/eth1/00:26:18:2c:41:f0/192.168.0.0/24
Sending on   Socket/fallback/fallback-net
```

This looks OK to me.  I don't want to listen on eth0 or nrtap so the messages to that effect don't bother me.

So what's wrong?  Why would it run from a terminal and not as a service?

Thanks,

AB

---

### Post by AlexBooton on 2012-06-28
Well I'm making a bit of progress, I think.  One step forwared and two back.  :(

At least part of the problem is that isc-dhcp-server6 looks for ```
/etc/dhcp/dhcpd6.conf
``` while my system only has ```
/etc/dhcp/dhcpd6.conf
```

I "fixed" that problem by creating a link to the missing file.  I don't know if that's a good fix but it seems to be OK so far.

Now I get an error in syslog ```
subnet_number():inet.c:53: Addr/mask length mismatch.
``` and I have no idea what this means.

I'm posting my dhcpd(6).conf (w/o the comments).  Hope someone can assist me.  I'm desparate so if you have any thoughts at all, please help.  Here it is and thanks...

```
ddns-update-style none;

option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
  option broadcast-address 192.168.0.255;
  default-lease-time 6000;
  max-lease-time 72000;
  option routers 192.168.0.189;
  option subnet-mask 255.255.255.0;
  range 192.168.0.10 192.168.0.100;
  option ntp-servers 192.168.0.189;
  option netbios-name-servers 192.168.0.189;
  option netbios-node-type 8;
}

```

---

