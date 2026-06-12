---
title: "How to set up dhcp server"
date: 2011-09-18
forum: General Help
---

### Post by AlexBooton on 2011-09-18
No sooner did I post this message that the dhcp server started working.

The one element I neglected to mention in this post was that I'm using firestarter as a firewall front end.  I decided to re-run the firestarter wizard and SHAZAM! everything fell into place.



Hi, 

I don't know just where to begin. I'm probably providing more info than needed.  I just need to know where my problem is:

Trying to make my ubuntu 11.04 system serve as a dhcp server for the other PC's on the LAN.  But can't quite get it to work.

I have two nics.  eth0 connects to the WAN.  This works.  eth1 should be the dhcp server for the rest of the LAN

1. Installed isc-dhcp-server package

2. Here are my settings in /etc/dhcp/dhcpd.conf
ddns-update-style none;

(Note:  I don't have a registered domain.  I just made up a domain for the next two lines.  Does it matter?)
option domain-name "pti.com";
option domain-name-servers pti.com;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7; (what is this?)

subnet 192.168.0.0 netmask 255.255.255.0 {
  option broadcast-address 192.168.0.255;
  default-lease-time 6000;
  max-lease-time 72000;
  option routers 192.168.0.189;
  option subnet-mask 255.255.255.0;
  range dynamic-bootp 192.168.0.10 192.168.0.100;

(Note: I think "option routers 192.168.0.189;" sets the ip for the server itself on the interface (eth1).  Right?  I want the server to have that ip.)

3. and settings for /etc/default/isc-dhcp-server 
INTERFACES="eth1"  (This seems to be working OK)

4. Start the dhcp server:
# /etc/init.d/isc-dhcp-server restart
(This also works and does not produce an error)

5. syslog says it gave out one lease:
Sep 18 12:18:26 pti-server dhcpd: Wrote 1 leases to leases file.

6. But on my Windows 7 test system I cannot get the the link to work.  The network connection for the Local Area Connection says "No internet access"
Here are the connection details from Win 7:
DHCP Enabled: Yes
IP Address: 192.168.0.10  (this agrees with number 5 above)
Subnet Mask 255.255.255.0
Default Gateway: 192.168.0.189 (the ip of the ubuntu dhcp server)
DHCP Server: 192.168.0.189
DNS Servers: 208.67.222.222 (this is the OpenDNS ip address)
WINS Server: <none>
NetBIOSServer over Tcpip: Yes 

7. Here are the results of route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
 

At this point I'm stumped.  How do I proceed?

Thanks!

---

### Post by Azdour on 2011-09-19
Hi,

So has the issue been resolved? If so could you mark this thread as closed thanks.

---

### Post by raja.genupula on 2011-09-19
> **AlexBooton said:**
> No sooner did I post this message that the dhcp server started working.

The one element I neglected to mention in this post was that I'm using firestarter as a firewall front end.  I decided to re-run the firestarter wizard and SHAZAM! everything fell into place.



Hi, 

I don't know just where to begin. I'm probably providing more info than needed.  I just need to know where my problem is:

Trying to make my ubuntu 11.04 system serve as a dhcp server for the other PC's on the LAN.  But can't quite get it to work.

I have two nics.  eth0 connects to the WAN.  This works.  eth1 should be the dhcp server for the rest of the LAN

1. Installed isc-dhcp-server package

2. Here are my settings in /etc/dhcp/dhcpd.conf
ddns-update-style none;

(Note:  I don't have a registered domain.  I just made up a domain for the next two lines.  Does it matter?)
option domain-name "pti.com";
option domain-name-servers pti.com;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7; (what is this?)

subnet 192.168.0.0 netmask 255.255.255.0 {
  option broadcast-address 192.168.0.255;
  default-lease-time 6000;
  max-lease-time 72000;
  option routers 192.168.0.189;
  option subnet-mask 255.255.255.0;
  range dynamic-bootp 192.168.0.10 192.168.0.100;

(Note: I think "option routers 192.168.0.189;" sets the ip for the server itself on the interface (eth1).  Right?  I want the server to have that ip.)

3. and settings for /etc/default/isc-dhcp-server 
INTERFACES="eth1"  (This seems to be working OK)

4. Start the dhcp server:
# /etc/init.d/isc-dhcp-server restart
(This also works and does not produce an error)

5. syslog says it gave out one lease:
Sep 18 12:18:26 pti-server dhcpd: Wrote 1 leases to leases file.

6. But on my Windows 7 test system I cannot get the the link to work.  The network connection for the Local Area Connection says "No internet access"
Here are the connection details from Win 7:
DHCP Enabled: Yes
IP Address: 192.168.0.10  (this agrees with number 5 above)
Subnet Mask 255.255.255.0
Default Gateway: 192.168.0.189 (the ip of the ubuntu dhcp server)
DHCP Server: 192.168.0.189
DNS Servers: 208.67.222.222 (this is the OpenDNS ip address)
WINS Server: <none>
NetBIOSServer over Tcpip: Yes 

7. Here are the results of route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
 

At this point I'm stumped.  How do I proceed?

Thanks!

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

---

### Post by AlexBooton on 2011-09-19
> **Azdour said:**
> Hi,

So has the issue been resolved? If so could you mark this thread as closed thanks.

Sorry,  I don't see how to do that. :confused:  

Yes, it's resolved.

---

### Post by Azdour on 2011-09-19
Hi,

Up the top you should find 'Thread Tools'. This has a dropdown box where you should be able to mark the thread as solved.

---

### Post by AlexBooton on 2011-09-19
> **Azdour said:**
> Hi,

Up the top you should find 'Thread Tools'. This has a dropdown box where you should be able to mark the thread as solved.

Thanks.  It's done. ):P

---

