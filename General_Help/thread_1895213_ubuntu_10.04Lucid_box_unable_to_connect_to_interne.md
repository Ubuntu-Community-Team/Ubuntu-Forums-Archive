---
title: "ubuntu 10.04Lucid box unable to connect to internet"
date: 2011-12-14
forum: General Help
---

### Post by vej1lr on 2011-12-14
Hi,
 
We have a ubuntu 10.04 Lucid release box & unable to connect to the  internet from this box. While all other machines in the same network has  no issues. Can someone suggest what could be wrong with this. Here is  the output from dmesg.

------------------------
device eth0 left promiscuous mode
eth0: no ipv6 routers present
nfsd: last server has exited, flushing export cache
svc: failed to register lockdv1 RPC service (errno 97)
NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
NFSD: starting 90-second grace period
------------------------

I did notice that tcpdump is running, I stopped that & then eth0 left non-promiscuous mode. Still ping 8.8.8.8 doesn work.
this machine is a NFS server. Obviously there are errors about NFS, but  the NFS exported directory is accessible from all clients. After  googling about the error, got to know that disabling IPv6 would help in  getting rid of these NFS-errors. But does it help in getting the machine  connecting to internet?

Thanks in advance

---

### Post by vej1lr on 2011-12-14
i have tried disabling ipv6 explicitly by adding entries in /etc/sysctl.conf. But this didnt help in getting the problem resolved. Can someone help in getting rid of the problem.

---

### Post by lechien73 on 2011-12-14
Ok, just a few questions ;)

What does dmesg report now? What is the IP address of your router? What is the output of:

```
route
```

and

```
ifconfig
```

Can you ping other computers on the network? If you try:

```
traceroute -n 8.8.8.8
```

at what point does it stop? How are the computers connected to each other and the router?

---

### Post by vej1lr on 2011-12-15
Hi, here are the details. I dont see any more errors (or) warning regarding ipv6 in dmesg. Couldnot find any other explicit error messages as well.

----------------------------------
*# route *
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.65.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.65.1    0.0.0.0         UG    100    0        0 eth0
----------------------------------
I can ping to the gateway & all other machines in the same subnet.

----------------------------------
# *ifconfig*
eth0      Link encap:Ethernet  HWaddr 00:50:56:9f:00:1c
          inet addr:192.168.65.30  Bcast:192.168.65.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:366589 (366.5 KB)  TX bytes:249385 (249.3 KB)
          Interrupt:18 Base address:0x2024

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8560 (8.5 KB)  TX bytes:8560 (8.5 KB)
-----------------------------------

Unfortunately traceroute is not available on the machine, since it is not able to connect to internet attempt to install  is also failing. This is a VM-instance runnin gon vmware-version 7 with vmtools-up-to-date.

---

### Post by vej1lr on 2011-12-15
There is an error message in dmesg which says
IPv6: loaded, but administratively disabled, reboot required to enable

Not sure whether this could be causing any problem.

---

### Post by lechien73 on 2011-12-15
Is the network card set to NAT or Bridged on the VMWare host? I often find that Bridged mode is easier, if your network isn't complex.

Are the other computers in the subnet also VMWare guests, or standalone machines?

---

### Post by vej1lr on 2011-12-15
It is a bridged network. Other machines are VM-guests.

---

### Post by lechien73 on 2011-12-15
Very odd. If you try changing the IP address does that work? I'm starting to wonder if the address is somehow blocked on your firewall or router?

Have you tried telnetting directly to an IP address? For example:

```
telnet 159.134.198.135 25
```

Should get you a welcome banner.

---

### Post by vej1lr on 2011-12-16
-------------------------------------------------
$ traceroute -n 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
-----------------------------------------------

I tried running tcpdump, but it reports 0-packets dropped by kernel.

Tried running nmap from another machine & All 1000 scanned ports on 192.168.234.30 are filtered.

---

