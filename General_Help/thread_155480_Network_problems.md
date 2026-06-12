---
title: "Network problems"
date: 2006-04-05
forum: General Help
---

### Post by kate on 2006-04-05
I can connect my laptop to the internet via either the hub or straight to the modem. My desktop won't connect either way. Both are running Ubuntu 5.10 (I should probably mention I've only been running Linux about a year, and I haven't had much time other than learning the basics). With the desktop, I've tried various NICs (ethernet, here), different PCI slots etc. Also different cables so it's probably not any of them.

The Ubuntu Network Manager says eth0 is active, but I can't do anything. Any ideas?

---

### Post by Sendervictorius on 2006-04-05
Can you please run ifconfig eth0 in terminal, and post the output.

---

### Post by shof2k on 2006-04-05
Right, firstly how are you connecting to the net, wired or wirelessly?  Please give details of the nics used.

Try opening a terminal and typing "ifconfig" to see if your nic is recognised.  If so, try pinging the router, then try pinging [www.google.com](www.google.com) to see if you can connect.

The following post gives lots of help.
[http://www.ubuntuforums.org/showthread.php?t=25557&highlight=network+troubleshooting](http://www.ubuntuforums.org/showthread.php?t=25557&highlight=network+troubleshooting)

---

### Post by kate on 2006-04-05
[QUOTE=Sendervictorius]Can you please run ifconfig eth0 in terminal, and post the output.[/QUOTE]

bash: ipconfig: command not found

not exactly helpful, eh?

---

### Post by kate on 2006-04-05
[QUOTE=shof2k]Right, firstly how are you connecting to the net, wired or wirelessly?  Please give details of the nics used.

Try opening a terminal and typing "ifconfig" to see if your nic is recognised.  If so, try pinging the router, then try pinging [www.google.com](www.google.com) to see if you can connect.

The following post gives lots of help.
[http://www.ubuntuforums.org/showthread.php?t=25557&highlight=network+troubleshooting](http://www.ubuntuforums.org/showthread.php?t=25557&highlight=network+troubleshooting)[/QUOTE]

Wired network, NICs to hub, which has my laptop, my desktop, and the modem all plugged in. Not exactly perfect but it's the best I've got.

Desktop NIC: 3Com PCI  3c905C-TX/TX-M, MAC address- 00:01:02:94:0B:45

laptop:  Xircom thing, MAC address- 00:10:A4:7D:15:9A

EDIT: sorry, typo with the Desktop NIC, is infact 3c905C

---

### Post by halfvolle melk on 2006-04-05
ipconfig is a Windows kind of thing ;)

Try i**f**config.

---

### Post by jamesr on 2006-04-05
I do not recognise > Desktop NIC: 3Com PCI 3c095C-TX/TX-M, MAC address- 00:01:02:94:0B:45do you mean 3c905C

```
sudo lspci
```

---

### Post by lleb on 2006-04-05
[QUOTE=kate]bash: ipconfig: command not found

not exactly helpful, eh?[/QUOTE]

you will need to type the following:

```
sudo **ifconfig**
```

enter the root p/w and then it will print out something like the following:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:81:7C:9F  
          inet addr:192.168.10.55  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe81:7c9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34786119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11839935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2365219225 (2.2 GiB)  TX bytes:844272181 (805.1 MiB)
          Interrupt:12 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5409929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5409929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110928574 (105.7 MiB)  TX bytes:110928574 (105.7 MiB)

```

---

### Post by shof2k on 2006-04-05
Kate, we need the above kind of output to help you.

Good luck

---

### Post by kate on 2006-04-06
here's the output:


eth0     Link encap:Ethernet  HWaddr 00:01:02:94:0B:45
            inet6 addr: fe80::201:2ff:fe94:b45/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
            RX packets:32901 errors:0 dropped:0 overruns:1 frame:0
            TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:2076890 (1.9 MiB)  TX bytes:8964 (8.7 KiB)
            Interrupt: 11 Base address:0xec00

lo       Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:6926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:623783 (609.1 KiB) TX bytes:623782 (609.1 KiB)

---

### Post by jamesr on 2006-04-06
Please post the output of ```
sudo dhclient eth0
```

---

### Post by kate on 2006-04-07
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:01:02:94:0b:45
Sending on  LPF/eth0/00:01:02:94:0b:45
Sending on  Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Just so you know, I have absolutely NO idea what any of that means :confused:

---

### Post by jamesr on 2006-04-07
The system is trying to get a TCP/IP address from the DHCP server in your router> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
 is the request and > No DHCPOFFERS received.
No working leases in persistent database - sleeping.

 is the reply/result ie no working leases if successful there would have been an address and a time in secs.. 

I mentioned that it is trying ipv6 . I will to find my notes on disabling ipv6.

---

