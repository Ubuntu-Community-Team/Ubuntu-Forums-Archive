---
title: "dhcpd3, Vista doesn't request ip"
date: 2011-05-03
forum: General Help
---

### Post by Kvadratrodenaf1 on 2011-05-03
Hi,

I'm having difficulties supporting Vista dhcp clients - all other clients successfully receive IP.
The vista clients don't receive IP at all. They receive an offer but they don't respond.
I'm aware that standard Vista requires dhcp broadcast and it can be fixed with a registry tweak but this is not an option since the users come and go.
When I set "always-broadcast on;" in dhcpd.conf some XP clients suddently doesn't receive IP so this is not a solution.
The firewall allows DHCP, DNS and ICMP. All other requests are routed to the dhcp host where web-based MAC authenticated is performed.

Versions:
Linux: 10.04 LTS - 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
dhcpd3: 3.1.3-2ubuntu3

ifconfig (only the LAN interfaces are shown):
```

eth1      Link encap:Ethernet  HWaddr 00:0d:60:eb:4e:11
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:feeb:4e11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2905753279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68560622 errors:1109157697 dropped:0 overruns:0 carrier:1109157697
          collisions:1397219861 txqueuelen:100
          RX bytes:1265132184 (1.2 GB)  TX bytes:3515590884 (3.5 GB)

eth1.3187 Link encap:Ethernet  HWaddr 00:0d:60:eb:4e:11
          inet addr:10.131.87.1  Bcast:10.131.87.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:feeb:4e11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7902540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11046394 errors:0 dropped:164 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1086729615 (1.0 GB)  TX bytes:3926439780 (3.9 GB)

```

dhcpd.conf:
```

authoritative;
default-lease-time 7200;
max-lease-time 14400;
option domain-name "nordicnetworking.com";
option subnet-mask 255.255.255.0;
log-facility local7;

subnet 10.131.87.0 netmask 255.255.255.0{
    option broadcast-address 10.131.87.255;
    option routers 10.131.87.1;
    server-identifier 10.131.87.1;
    option domain-name-servers 8.8.8.8;
    range 10.131.87.2 10.131.87.200;
    host host59{
        hardware ethernet 00:22:2d:62:e7:c8;
        fixed-address 10.131.87.201;
    }
    host host60{
        hardware ethernet 00:22:2d:62:e6:70;
        fixed-address 10.131.87.202;
    }
}

```

dhcpd.log:
```

May  3 09:30:19 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:30:19 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:35:48 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:35:49 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:35:52 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:35:52 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:36:00 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:36:00 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:36:15 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:36:15 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:22 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:23 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:26 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:26 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:33 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:33 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:48 vlan dhcpd: DHCPDISCOVER from xx:xx:xx:xx:xx:xx (hostname) via eth1.3187
May  3 09:41:48 vlan dhcpd: DHCPOFFER on 10.131.87.25 to xx:xx:xx:xx:xx:xx (hostname) via eth1.3187

```

Br Mathias.

---

