---
title: "Internet Connection Sharing, attempt 32,479"
date: 2010-04-21
forum: General Help
---

### Post by Objekt on 2010-04-21
Here's what I'm trying to do: share the second wired NIC of my Ubuntu 9.10 desktop with another computer, which is running Windows XP.

Here's what happens instead:
The Windows XP machine gets assigned an IP address, and can ping the Ubuntu machine.  Likewise, the Ubuntu machine can ping the Windows XP machine.  However, attempts at browsing the Web from the XP machine are unsuccessful.  Its traffic is apparently disappearing into a black hole.  Every try at visiting a website results in a "cannot connect" error message.

The players:

-Host: an Ubuntu 9.10 desktop (specs in signature), which has two wired NICs, eth0 and eth1.  eth0 connects to my router, then my cable modem, then the Internet.  eth1 connects to the Windows XP machine.

-Client: an Acer Aspire One netbook, running Microsoft Windows XP.  One wired NIC, connected by normal (e.g. non-crossover) cable to eth1 of the Ubuntu machine.

What I've done so far:
-Edited the "eth1" connection in NetworkManager so that it is "shared to other computers" and accessible to all.  Rebooted for this to take effect.
-Run the Network Wizard on the Windows XP machine, telling it that it is sharing a connection with another computer.  Rebooted.
-Pinged each machine from the other.  They see each other.

So what could be going on here?  While I am very happy that the Windows machine gets an IP address automagically, and there is clearly an active connection between the Windows and Ubuntu machines, somehow the traffic from the Windows machine isn't going anywhere.

Possibly useful data:
-The NIC on the Windows XP machine is configured to obtain an IP address and DNS addresses automagically.
-No firewall installed on the Ubuntu machine (gufw, etc.).
-The Windows XP machine can share the Internet connection of the host, when the host is also running Windows XP.  So I'm pretty sure there's not a hardware problem anywhere.
-ICS also works flawlessly when the host is running a Live CD session of Ubuntu 9.10.

Any ideas what the problem might be?

---

### Post by Objekt on 2010-04-28
Don't be shy.  Surely someone has an idea how to fix this?

I'm encouraged by the fact that the two computers can pass packets back and forth, but baffled that the Windows machine's attempts to reach the outside world simply vanish into the aether.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
What happens when you ping the outside world? ```
ping google.com
```

---

### Post by SRST Technologies on 2010-05-11
> **Objekt said:**
> eth0 connects to my router

Here's the problem.  You're routing through routing on an unroutable IP address.  Almost every router known to man uses nonroutable IP addresses on the private side.  These are unroutable addresses for a reason, it's to help protect the private LAN even further.

You could set the router to not use a nonroutable IP addresses which allows ICS to re-route the packet further, but there's no real reason to do so.  Just plug in what you're connecting to the ICS Ubuntu server into the router directly.  Problem solved.  That's what you bought the router for.

---

### Post by Objekt on 2010-05-11
Yes, I could plug the client box into my router, but then I wouldn't have bothered starting this thread.  That isn't the point at all.

I have the same problem when the netbook is running Ubuntu Netbook Remix 9.10.  While it gets an IP address from the server (Ubuntu desktop), its traffic goes nowhere.

It's really strange that ICS works perfectly when the desktop is running a Live CD session of Ubuntu 9.10, but not with my regular 9.10 install.

Trying to ping cnn.com (or anything else) doesn't work.  Something somewhere is simply discarding any attempt by the netbook to reach the outside world.

---

### Post by SRST Technologies on 2010-05-12
Perhaps you should read up on what a nonroutable IP address is.

---

### Post by Iowan on 2010-05-12
> **Objekt said:**
> 
-Run the Network Wizard on the Windows XP machine, telling it that it is sharing a connection with another computer.  Rebooted.Probably not the problem, but the Windows box isn't sharing it's connection. Sounds like you've seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page.

---

### Post by blueridgedog on 2010-05-12
This is a standard setup using your Linux box as a firewall/masquerading box.  

You will need to use iptables to tell you Linux system to route traffic from the internal lan out to the external lan and mask the ip addresses.

Google "linux iptables masquerade"

See for example:

[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

---

### Post by SRST Technologies on 2010-05-13
Actually, since his Linux box is getting an IP address, Windows IS sharing the connection.  He's only getting an IP address because DHCP is set up on the Windows ICS box and things are fine there.

Once again, I urge you all to look up what a nonroutable IP address is and how it relates to a standardized router setup.

blueridgedog, did you actually read the thread?

---

### Post by blueridgedog on 2010-05-13
> **SRST Technologies said:**
> 

blueridgedog, did you actually read the thread?

Yes, with the essential part being:

> -Host: an Ubuntu 9.10 desktop (specs in signature), which has two wired NICs, eth0 and eth1. eth0 connects to my router, then my cable modem, then the Internet. eth1 connects to the Windows XP machine.

-Client: an Acer Aspire One netbook, running Microsoft Windows XP. One wired NIC, connected by normal (e.g. non-crossover) cable to eth1 of the Ubuntu machine.

He will not accomplish this without configuring the Ubuntu box as a router using iptables.  The Ubuntu system will have no other way of fowarding packets recieved from eth1 to eth0.

---

### Post by Objekt on 2010-05-13
> **blueridgedog said:**
> This is a standard setup using your Linux box as a firewall/masquerading box.  

You will need to use iptables to tell you Linux system to route traffic from the internal lan out to the external lan and mask the ip addresses.

Google "linux iptables masquerade"

See for example:

[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

Thanks for that.  I'm not in front of my Linux box now, but reading over that page, it sounds as if it should make things work.

The missing piece so far has been routing.  As in, none happening between eth0 and eth1.  For some reason, the proper routing gets set up automagically in the Live CD environment, as soon as I designate eth1 as "Shared" in NetworkManager.  It doesn't happen with my 9.10 installation, however.  I am sure the iptables rules are the key, but couldn't figure out how to set them up manually.

---

### Post by Objekt on 2010-05-13
> **SRST Technologies said:**
> Actually, since his Linux box is getting an IP address, Windows IS sharing the connection.  He's only getting an IP address because DHCP is set up on the Windows ICS box and things are fine there.

Once again, I urge you all to look up what a nonroutable IP address is and how it relates to a standardized router setup.

blueridgedog, did you actually read the thread?

He did, but it sounds like you didn't.  You keep going on about nonroutable IP addresses, and for some reason you think I am trying to share an extra NIC on the netbook with the desktop machine.  It's the other way around.  The desktop has 2 wired NICs, and I am trying to share the second one, effectively making the desktop machine itself a router.

That should work, as long as the desktop makes all the traffic from the netbook appear to come from itself, instead of from the actual IP address of the netbook.

Nonroutable IP addresses are not really part of this discussion.  The proper NAT happens in the Live CD environment, so I can't see how it matters what IP address the netbook gets assigned by the desktop machine.  The meat of the issue is this: I can't get the proper NAT happening outside of the Live CD environment.

**Note:** The netbook is now running Ubuntu Netbook Remix instead of Windows XP, because it's a different netbook.  Hardware is of the same type, however, so the problem (and probably the solution) is the same.  I tried to go back and edit my initial post to reflect the change, but it got too confusing.  I'll probably have to start another thread.

---

### Post by blueridgedog on 2010-05-13
In your example, eth0 is external and eth1 is internal.

Each has an IP address.  They may be assigned or dynamic, but the entire setup would work better if they ware assigned.  Eth0 is probably getting an IP address from the router.

To get packets working so that the hosts downstream of the Linux system can access the internet you need to route packets through the Linux box.  

This can be as simple as:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

This tells your system to allow forwarding of packets from eth1 and to mask the IP address of those hosts on the eth1 lan to be the host of the Linux box (server actually), specifically the IP address assigned to eth0.

The IP address assigned to eth1 would then become the gateway address used by all systems on the lan that eth1 is attached to. 

I suggest you configure a specific subnet of IP's for your "internal" network.  

I can give further advice if needed and I think you will find an avalanche of information on the web regarding NAT (network address translation) and Linux.  If you want more help, give me some specifics about the addresses used in each network segment.

---

### Post by Iowan on 2010-05-13
[Here]("http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/") is another ICS/NM page, but it will likely provide no more information than the other link.

---

### Post by blueridgedog on 2010-05-14
> **Iowan said:**
> [Here]("http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/") is another ICS/NM page, but it will likely provide no more information than the other link.

Wow...a graphical tool to setup NAT.  Does it work?  If so, it is drastically simple compared to manually configuring it.

---

### Post by Objekt on 2010-05-14
> **blueridgedog said:**
> Wow...a graphical tool to setup NAT.  Does it work?  If so, it is drastically simple compared to manually configuring it.

Absolutely it works, at least most of the time.  As I've stated, I can easily configure my desktop box to do NAT on its second NIC using NetworkManager, but so far only in the Ubuntu 9.10 Live CD environment.

---

### Post by Objekt on 2010-05-16
> **blueridgedog said:**
> In your example, eth0 is external and eth1 is internal.

Each has an IP address.  They may be assigned or dynamic, but the entire setup would work better if they ware assigned.  Eth0 is probably getting an IP address from the router.

Yes, the router is running its own DHCP server.

> **blueridgedog said:**
> To get packets working so that the hosts downstream of the Linux system can access the internet you need to route packets through the Linux box.  

This can be as simple as:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

This tells your system to allow forwarding of packets from eth1 and to mask the IP address of those hosts on the eth1 lan to be the host of the Linux box (server actually), specifically the IP address assigned to eth0.

The IP address assigned to eth1 would then become the gateway address used by all systems on the lan that eth1 is attached to. 

I tried to run those commands, but the first one failed:

```
objekt910@objekt910-desktop:~$ echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

```

Sudo didn't help:

```
objekt910@objekt910-desktop:~$ sudo echo 1 > /proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

```

I had to do it another way, by running gedit with gksudo to manually edit /etc/sysctl.conf.

FWIW, the other 4 lines have to be run with sudo.  I ran them, but nothing's changed.  I can't get the the 2 machines to see each other.  The client doesn't get an IP address at all.  I'm not sure whether the commands to set up iptables rules are working:

```
objekt910@objekt910-desktop:~$ sudo iptables -L
[sudo] password for objekt910: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

> **blueridgedog said:**
> I suggest you configure a specific subnet of IP's for your "internal" network. 

How?

---

### Post by blueridgedog on 2010-05-16
First, the best way to enter the commands will be:

```
sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

Now, to get your internet facing network and you internal facing network in order, let's document what you have working at the moment.  To do that, I need some infomration.

On the Linux box, can you post for me the output of:

```
ifconfig
```

And on the Windows box, can you post for me the output of:

```
ipconfig
```

Front there, i should be able to document creating a defined internal network address scheme whereby the two boxes can see each other and the windows box uses the Linux box as the gateway and the Linux box allows that.

It will take a small bit of "back and forth" but we should get it working in the end.

---

### Post by Objekt on 2010-05-17
**Take note: The client machine is now running Ubuntu Netbook Remix 9.10, not Windows XP.**  Problem is the same, however - can't get a wired Internet connection through the Ubuntu desktop's second NIC.

First, on the Ubuntu desktop (host) here's the result of running the iptables commands as root, as you suggested:

```
root@objekt910-desktop:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

I don't see anything relating specifically to eth0 and eth1, which might explain the absence of NAT happening.  Does that look right to you?

ifconfig output, Ubuntu desktop (host):
```
root@objekt910-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4f11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18624317 (18.6 MB)  TX bytes:2190364 (2.1 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5340 (5.3 KB)  TX bytes:191796 (191.7 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:209 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19776 (19.7 KB)  TX bytes:19776 (19.7 KB)
```

ifconfig output, Ubuntu Netbook Remix netbook (client):
```
user2@bluenetbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:4e:fe:80  
          inet6 addr: fe80::223:5aff:fe4e:fe80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:1015 (1.0 KB)  TX bytes:5598 (5.5 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:6d:cc:4a  
          inet6 addr: fe80::224:2bff:fe6d:cc4a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2608 (2.6 KB)  TX bytes:6338 (6.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-6D-CC-4A-36-64-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Objekt on 2010-05-17
You know how I said everything works the way I want when the host is running an Ubuntu Live CD (or USB) session?  I just did that, and ran iptables -L and ifconfig in the Live environment (on the "host" machine).  Here's the result:

```
ubuntu@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4f11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123315 (123.3 KB)  TX bytes:38861 (38.8 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29700 (29.7 KB)  TX bytes:118148 (118.1 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

Again, the above is what I get while the host's second NIC is set to "Shared" in NetworkManager, when running an Ubuntu Live session.  I don't know why things don't work the same way when the host runs the installed version of Ubuntu.  That is the meat of the problem, I think.

Note that I didn't do anything to set up those rules with iptables.  It happened automagically, as a result of setting the host's eth1 connection to "shared" mode.  The netbook client was assigned an IP address and its routing set up right away, which is exactly what is NOT happening when I run a normal Ubuntu session on the host.

---

### Post by blueridgedog on 2010-05-17
When booted on the live CD, your internal interface, eth1 has an IPv4 ip address:


```
eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          **inet addr:10.42.43.1 ** Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29700 (29.7 KB)  TX bytes:118148 (118.1 KB)
          Interrupt:19 
```

And there are appropriate rules in the Iptables ruleset to accommodate the forwarding on that network.  I believe that is why it works.

In your current state, you have no IPv4 address on your internal interface:

```
eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5340 (5.3 KB)  TX bytes:191796 (191.7 KB)
          Interrupt:19 
```

Also note that when you are on the LiveCD, you have one network on the outside, 192.168.1.0/24, and one on the inside, 10.42.43.0/24.  

We need define an internal network for eth1 on your outside facing box (we will call it "server") and for eth0 on the new netbook (we will call it client)and hand key that into each system manually.  Since your outside facing network is currently 192.164.1.0/24, then I suggest we use something different for the internal.  10.0.1.0/24 will work.  

Before we can proceed, we do need to know the IP addresses of your name servers as currently assigned by your router.  To get that, go to the server and type:

cat /etc/resolv.conf

You want to write down the IP address of the two or more name servers listed.

The IP assignments will then be:

Server:
eth1 - no change, currently on dhcp and working fine with an IP address assigned by your router 
eth0 10.0.1.1
netmask: 255.255.255.0
broadcast: 10.0.1.255
No gateway specified

Client:
eth1 10.0.1.2
netmask: 255.255.255.0
broadcast: 10.0.1.255
gateway: 10.0.1.1
DNS1 First name server from resolv.conf
DNS2 Second name server from reslov.conf

By configuring these interfaces, the client will look to the server as a "gateway".  The server will then be configured to accept the client's traffic and forward it out to the world at large, just as your router does.

To configure these addresses, right click the network connections icon in the task bar and click "edit connections.

For the server, select eth0, then IPv6 settings and verify that the "method" is set to "ignore", then click the tab that states IPv4 settings, click the "method" button and change it to manual, then click "add" and add an IP address matching the information above.  You will only need to put in the IP and netmask as there will be no gateway on this network for this system and the DNS servers are assigned on the other interface.

For the client, select eth1, then IPv6 settings and verify that the "method" is set to "ignore", then click the tab that states IPv4 settings, click the "method" button and change it to manual, then click "add" and add an IP address matching the information above.  You will need to put in the IP, netmask and gateway as this machine needs to know how to get at neworks that are off the local network.  You will also need to get it a DNS server, which you got via the resolv.conf file above.

Once that is done, you should be able to bring up a terminal and type

ping 10.0.1.1 

And get a reply that you are talking to the server and the server is replying to the client.

Once they are talking to each other, you can try and setup NAT on the server with:

```
sudo -i
echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
/sbin/iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
```

This should produce different results now that there is and IPv4 address on the internal interface.

If this fails to work as expected, we may need to specify IP addresses in the iptalbes commands.

Also, if it fails and we need to "debug" it, post the ifconfig output from each system so that we can verify that the new IP addresses have been entered and accepted.

---

### Post by Objekt on 2010-05-19
The client and server can now see each other - I get a ping result going both ways.  However, the client still cannot reach the Internet.

Here's ifconfig output from both:

server:
```
root@objekt910-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:2f:4f:11  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4f11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7896627 (7.8 MB)  TX bytes:1076677 (1.0 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:2f:4e:b5  
          inet addr:10.0.1.1  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe2f:4eb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25168 (25.1 KB)  TX bytes:16250 (16.2 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14666 (14.6 KB)  TX bytes:14666 (14.6 KB)

```

client:
```
user2@bluenetbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:4e:fe:80  
          inet addr:10.0.1.2  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe4e:fe80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:21603 (21.6 KB)  TX bytes:34810 (34.8 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1084 (1.0 KB)  TX bytes:1084 (1.0 KB)
```

Also, iptables rules on the server, after running the previously-discussed commands:
```
root@objekt910-desktop:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

I'm still not seeing the rules that are established when I do ICS in a Live CD session.  So I guess those were not the right commands.

FWIW, I get no result trying to ping an outside website (e.g. cnn.com) from the client or the server.  However, I'm able to visit the cnn.com webpage on the server.

---

### Post by blueridgedog on 2010-05-20
Two more items to check before we dive in to debugging is the routing on the client and the name resolution.  Can you post the output of the command:

```
route
```

and

```
cat /etc/resolv.conf
```

from the client?

---

### Post by Objekt on 2010-05-21
client:

```
user2@bluenetbook:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.1.0        *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         objekt910-deskt 0.0.0.0         UG    0      0        0 eth0
user2@bluenetbook:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 192.168.1.20
```

This doesn't make any sense at all.  In NetworkManager, the client is set to use my router (192.168.1.1) for DNS, just like the server.  But somehow it seems to be trying one of the OpenDNS servers (208.67.222.222), which you would think would work, and 192.168.1.20, held by nothing on the network.  I have no idea here that address came from.

By the way, when you referenced above an internal address as 192.168.1.0/24, what does the /24 part mean?  I am not familiar with this nomenclature.  I have often seen port numbers appended to IP addresses (e.g. for game servers), but what is the significance of /(number)?

---

