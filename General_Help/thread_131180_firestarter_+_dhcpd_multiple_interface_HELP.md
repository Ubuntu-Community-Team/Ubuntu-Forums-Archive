---
title: "firestarter + dhcpd multiple interface HELP"
date: 2006-02-15
forum: General Help
---

### Post by dananimal on 2006-02-15
HI All

I had previously had a NAT gateway firewall operating using firestarter and using static IP addressing. I am trying to replicate that success with the addition of a DHCP service too.
The problem I am facing is that I cannot convince dhcpd to ignore my external NIC.

I am using Ubuntu 5.10.
I have installed firestarter and dhcpd using apt-get
The external NIC is eth0, which aquires it's IP addressing from the ISP.
The internal (LAN) NIC is eth1 which has the IP address 10.0.0.1

When I restart firestarter I get this error:
[INDENT]Failed to start the firewall
An unknown error occurred.

Please check your network device settings and make sure your Internet connection is active.[/INDENT]

If I: 
```
grep dhcp /var/log/syslog

```
I see:
```
Feb 16 14:31:01 hostname dhcpd: Listening on LPF/eth1/XX:XX:XX:XX:XX:XX/10.0.0.0
Feb 16 14:31:01 hostname dhcpd: Sending on   LPF/eth1/XX:XX:XX:XX:XX:XX/10.0.0.0
Feb 16 14:31:01 hostname dhcpd: No subnet declaration for eth0 (XXX.XX.XX.XXX).
Feb 16 14:31:01 hostname dhcpd: Please write a subnet declaration in your dhcpd.conf file for the
Feb 16 14:31:01 hostname dhcpd: network segment to which interface eth0 is attached.
Feb 16 14:31:01 hostname dhcpd: exiting.
Feb 16 14:31:37 hostname dhcpd: DHCPREQUEST for 10.0.0.10 from XX:XX:XX:XX:XX:XX via eth1
Feb 16 14:31:37 hostname dhcpd: DHCPACK on 10.0.0.10 to XX:XX:XX:XX:XX:XX via eth1


```

/etc/dhcpd.conf looks like:
```
subnet 10.0.0.0 netmask 255.0.0.0 {
  authoritative;
  range 10.0.0.10 10.0.0.202;
  option domain-name-servers XXX.XX.XXX.XX, XXX.XXX.X.XX;
  option domain-name "hostname.ath.cx";
  option routers 10.0.0.1;
  option broadcast-address 10.0.0.254;
  default-lease-time 600;
  max-lease-time 7200;
}
#
# This entry ignores requests on eth0?...
subnet 0.0.0.0 netmask 255.255.255.0 {
       not authoritative;
}
```
/etc/default/dhcp like this:
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"
```
And /etc/init.d/dhcp even has this at the beginning
```
# $Id: dhcp.init.d,v 1.3.2.2 2002/08/11 22:11:54 peloy Exp $
#

test -x /usr/sbin/dhcpd || exit 0

# Defaults
INTERFACES="eth1"
```

The client 10.0.0.10 gets it's IP address and the subnet but not a router address or DNS. There by no Internet either.
I've searched my socks off to no avail, what do I have wrong??:-?

---

### Post by dananimal on 2006-02-16
I have found that if I configure the client IP manually 
ie.
Address = 10.0.0.10
Subnet = 255.0.0.0
Router = 10.0.0.1

The Internet connection is shared fine
So I'm fairly sure that it is purely a DHCP server issue 
As the differnce between the failed DHCP IP details and this manual IP is that the router address was not picked up by the client so I figure that it mostly amounts to the DHCP server not giving the client the router address.
Any Ideas? Help? Please.

---

### Post by dananimal on 2006-02-21
Though I still get the same error upon starting firestarter my NAT system operates OK hosts are supplied with their IPs and they can see the internet.
\\:D/ 
So though I still don't know what is going on it is not such an accute issue.
:-k

---

