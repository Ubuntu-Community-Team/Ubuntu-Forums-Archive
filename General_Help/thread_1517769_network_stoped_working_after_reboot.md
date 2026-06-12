---
title: "network stoped working after reboot"
date: 2010-06-25
forum: General Help
---

### Post by pernest on 2010-06-25
Hi,

Using 10.04, everything working fine every day since the install a month or so ago. I shut down the machine normally, when I returned a few hours later it started up without a hitch, but without network.

I found a thread suggesting the following (in the case of a failed suspend, which did happent to me a few weeks ago)
```
  service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start 
```but it didn't help.
My ifconfig looks like this
```
 eth0      Link encap:Ethernet  HWaddr e0:cb:4e:32:2e:10  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x6000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```I would be greatful for any help anyone can offer. If I knew more diagnostic information to give, I would give it, so if I've left anything out, then let me know and I will include it.

Thanks

Paul

---

### Post by t1nm@n on 2010-06-25
try these commands
===========================
ifconfig eth0 down
ifconfig eth0 up
===========================
Now wait for a while if nothing happens run this command too
===========================
dhclient

===========================

reply back with what you get..best of luck

---

### Post by pernest on 2010-06-25
Thanks, but still no network.
result of both
```
sudo ifconfig eth0 down
```
and
```
sudo ifconfig eth0 up
```
where to return the command promt without any output, and the network didn't start working.
The result of dhclient was
```

Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/e0:cb:4e:32:2e:10
Sending on LPF/eth0/e0:cb:4e:32:2e:10
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Please let me know if there are any other diagnostics that I can run, so that you might be able to help me more easily.

thanks for trying.

Paul

---

### Post by pernest on 2010-06-25
I've been trying a little more but to no avail.

I tried to completly uninstal and then reinstall network manager, but this achieved nothing.

If I bring the device up manually (at least thats what I think I'm doing) [sudo ifconfig eth0 192.168.1.5] and then try and ping my router, I still get nothing.

Please can anyone help me as I'm really stuck and just can't make any headway with what I'm finding with google.

---

### Post by t1nm@n on 2010-06-26
hey if you are using windows and are able to get internet from it
go to the commandprompt ant type 

system info

also if you dont mind type lspci in ubuntu terminal and paste the outputs here..

---

