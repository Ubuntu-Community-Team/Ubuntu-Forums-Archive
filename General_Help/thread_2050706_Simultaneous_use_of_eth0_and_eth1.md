---
title: "Simultaneous use of eth0 and eth1"
date: 2012-08-31
forum: General Help
---

### Post by jzambon on 2012-08-31
I've got 3 servers running Ubuntu.  These servers are designed to hold a lot (>20TB) of data each.  Each server has 2 10/100/1000 mbps ethernet ports.  Across all the servers one port (eth0) is connected to the external network (DHCP), where the servers distribute information to the "world".  Unfortunately the network in my building is 10 mbps.  So, I need another network interface available (eth1) between the three that would transfer data at (somewhat) gigabit speeds.

I have connected all three together using a gigabit *switch* (no router), the lights are all green.  I attempted to configure a network connection, giving static IPs across all of the systems.  In /etc/network/interfaces I have....

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# LAN network interface
auto eth1
iface eth1 inet static
address 192.168.1.101
netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
#gateway 192.168.1.1

The address varies from device to device (192.168.1.101, 192.168.1.102, 192.168.1.103).

With the gateway enabled under eth1, I am unable to connect to anything (I assume because multiple gateways for one device is a bad idea).  I have also tried commenting out the network and broadcast IPs with no success.  Any pings between the devices (192.168.1.101, 192.168.1.102, 192.168.1.103) do not find the other devices.

I'm sure that I'm missing something here, being naive, I thought I could simply set up a second interface (eth1), set a static IP address, and SSH/SCP into the other machines via their static addresses (192.168...).  Now I am confused as to how Ubuntu would "know" when I tell it to SCP/SSH/ping/SFTP to 192.168.1.101, I mean over eth1 and not eth0.

Eventually, I would like to configure a fast way to transfer data between the devices.  If there is a better (faster, more secure) way than Samba of mounting a networked Ubuntu box across this "closed" network (eth1), please let me know!

Thanks!

---

### Post by papibe on 2012-08-31
Hi jzambon.

Could you describe your network a little more? I don't understand how your subnetwork is connected to the building network.

What is the building network's DHCP range?

Regards.

---

### Post by jzambon on 2012-08-31
The building network is part of a major university.  I believe we own the entire range xxx.xxx.1-255.1-255 (65,025 IP addresses).  I was able to get the machines registered to the network by my sysadmin, but other than that, have no knowledge of the network topology.

So eth0 on all 3 devices goes out the door, no idea what happens after that.  However, if I initiate a file transfer between the devices on eth0, they go at the building speed of ~10MB/s.  eth1 sits inside the room, connects all devices over Cat6 to a switch.  This switch is not connected to anything else.  Trying to get the 3 devices to communicate with each other over this switch while simultaneously being available to traffic outside.

Hopefully this helps, unfortunately specifics about the university network are not well known to me.

---

### Post by papibe on 2012-08-31
Thanks.

You need to create a subnet.

The simples alternative is to get a router that supports an external DHCP connection (instead of just DSL). Set the WAN to use th University's DHCP service, and set a LAN range for your private network. All your machines would be connected to the router (they will be using only one ethernet interface).

If your router is just 100Mb/s, connect one cable to the gigabit switch, and all machines to the switch so you can have gigabit LAN speeds.

Another alternative is to set one machine as a router of the subnet. These would be the basic steps:
[LIST=1]
[*]Set one machine connected to the university network using eth0 (let's call it main).
[*]Set a static LAN IP on main's eth1 (for instance 192.168.1.1). You'll need all settings (netmask, network, etc).
[*]Install a DHCP server on main. 'dnsmasq' is the simplest to use. Use the same LAN range, i.e. 192.168.1.*. Important: the server must provide services only to eth1.
[*]Connect the switch to main's eth1.
[*]For machines two and three, connect just one ethernet interface to the switch. Set them to use DHCP.
[*]You may need to add some extra configuration to the main machine in order to work 100% transparent (either routes or iptables rules). See [here]("https://help.ubuntu.com/community/Router") for more details.
[/LIST]
I hope that points you in the right direction. Let us know how it goes.
Regards.

---

### Post by jzambon on 2012-08-31
Thanks for your help!

We have individual machine names for each of these servers srv1, srv2, srv3 that need to be visible to the outside world.  This is so that people can remote (SSH) in from wherever.

Will I be able to make the DHCP transparent enough so that when someone attempts to SSH to either non-main server, that they will be able to?

---

### Post by papibe on 2012-08-31
> **jzambon said:**
> We have individual machine names for each of these servers srv1, srv2, srv3 that need to be visible to the outside world.

Ohh, I see. I think I may have misinterpreted your main concern.

Both setups I suggested were more intended for security and privacy, not providing services.

My guess right now is that your servers need to be on the University DHCP range and DNS.

If you are allow to have multiple IPs on your department/lab, this would be the simplest solution I can think of:
[LIST]
[*]Connect a cable from the wall (University network) to the gigabit switch.
[*]Connect every machine to the switch (one ethernet interface per machine).
[*]Set the machines to DHCP.
[/LIST]
With that setup you'll have all machines available to the University's users, and they'll have gigabit speed between them.

I hope this helps you (and not confuse you more).
Regards.

---

### Post by jzambon on 2012-08-31
The current setup on eth0 is exactly that, which is why I thought a closed LAN with a separate ethernet link would be a solution.  We have 1000Mb/s speeds on these interface listed using ethtool.  However, when I initiate a file transfer, we only get ~10.7MB/s.  I would expect at least around 80-90MB/s.  These speeds (to me) demonstrate that the data is being sent beyond the router through the building's 10mbps network.

Thanks!

This is across all of the servers...

user@srv1:~$ sudo ethtool eth0 | grep -i speed
	Speed: 1000Mb/s

---

### Post by papibe on 2012-08-31
Interesting, maybe there's a proxy configured.

Try tracing the connection to each other using 'tracepath' and 'traceroute'.

Also you can check raw transfer speeds using iperf (example [here]("http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes")).

Regards.

---

### Post by SeijiSensei on 2012-08-31
Another option to consider is [bonding]("http://www.kernel.org/doc/Documentation/networking/bonding.txt") the two interfaces together.

---

### Post by jzambon on 2012-08-31
Sorry if cleaning up my logs for security obscures some data...

Can't see a proxy being used.  But the data is definitely going beyond this room.

results of tracepath...

user@srv3:~$ tracepath srv1
 1:  srv3                                 0.104ms pmtu 1500
 1:  hub-xxxx                        1.015ms 
 1:  hub-xxxx                        0.980ms 
 2:  srv1                                 1.267ms reached
     Resume: pmtu 1500 hops 2 back 63 



results of iperf...

user@srv3:~$ iperf -c srv1
------------------------------------------------------------
Client connecting to srv1, TCP port 5001
TCP window size: 23.5 KByte (default)
------------------------------------------------------------
[  3] local xxx.x.xxx.xx port 41296 connected with xxx.x.xxx.xx port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec   113 MBytes  93.9 Mbits/sec

iperf results seem consistent with ~10-11 MB/s

Thanks again!!

---

### Post by jzambon on 2012-08-31
> **SeijiSensei said:**
> Another option to consider is [bonding]("http://www.kernel.org/doc/Documentation/networking/bonding.txt") the two interfaces together.

Would bonding work if the network on the eth1 interface is not configured correctly?  I assume that I need to figure out how to correctly set eth1 (IP, netmask, gateway, etc) to work concurrently with eth0...

# Connection to other servers
auto eth1
iface eth1 inet static
address 192.168.1.102
netmask 255.255.255.0


This afternoon I have been going down the "route" route.  Can I configure route to point traffic to srv2 (from srv1) to go only through eth1.  I have not been able to figure out a way to configure this correctly and ping the other server with any success.

user@srv2:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         hub-xxxx 0.0.0.0         UG    100    0        0 eth0
xxx.x.xxx.xx     *               255.255.255.192 U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1


Thanks!

---

### Post by SeijiSensei on 2012-08-31
I've not done that myself.  I just know that the bonding driver enables you to treat multiple adapters as one.  You'll have to read the howto and experiment.

---

### Post by papibe on 2012-08-31
There you go: 2 hops.

```
user@srv3:~$ tracepath srv1
 1:  srv3                            0.104ms pmtu 1500
 1:  hub-xxxx                        1.015ms 
 1:  hub-xxxx                        0.980ms 
 2:  srv1                            1.267ms reached
     Resume: pmtu 1500 hops [COLOR="Red"]**2**[/COLOR] back 63 

```
Since the switch should be absolute transparent (unmanaged), it is going some place else before going back to your other server.

Regards.

---

### Post by jzambon on 2012-09-06
Well, I just simply connected 2 of the servers via a cat-6 cable, connected each of them with the help of this post...

> **unutbu said:**
> Use a crossover cable to connect the two machines, NIC <--> NIC.

I assume:
[LIST]
[*]the NIC interface on both machines is called eth0.
[*]Computer A has ip address 192.168.0.1
[*]Computer B has ip address 192.168.0.2
[/LIST]

On Computer A:
```

/sbin/ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.2 eth0

```On Computer B:
```

/sbin/ifconfig eth0 192.168.0.2 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.1 eth0

```Now on Computer A you should be able to ping Computer B:
```
ping 192.168.0.2
``` (And vice versa, B should be able to ping A.)

I let the transfer start Friday afternoon and by Wednesday afternoon, I had transferred all 19TB without a problem (as far as I can tell).  On the university network, this would have taken 20 days!

While this solution helped in the short term to get the data dump completed, long term I would still like to be able to use both network interfaces across all 3 servers.

So, going on the above thread, I attempted to configure my /etc/network/interfaces file as follows...

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

```(Computer B has an identical configuration, except the address on eth1 is 192.168.0.2)

I restart the network connection and then route the hosts to each other...

```

sudo /sbin/route add -host 192.168.0.2 eth1

```(Again, Computer B is identical, except connecting to host 192.168.0.1)

When I do this, I get a momentary (~30s) connection...

```

user@srv3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
...

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: XXXXXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1595428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2418276459 (2.4 GB)  TX bytes:54653097 (54.6 MB)
          Interrupt:17 Memory:c7200000-c7220000 

lo        Link encap:Local Loopback  
...

```and am able to ping the other computer, and have access to the outside world.  More importantly, I am able to get gigabit speeds out of it!

```

user@srv3:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.2 port 5001 connected with 192.168.0.1 port 33422
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.07 GBytes   920 Mbits/sec

```

However, after a few moments the connection drops and a popup comes up saying "Wired network Disconnected".   The 192.168.0.1(2) address is flushed from eth1, but eth0 is still operational.  Why is the connection dropping after it successfully is up?  I feel like I'm really close here...

Thanks!

---

