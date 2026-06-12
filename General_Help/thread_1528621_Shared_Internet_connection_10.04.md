---
title: "Shared Internet connection 10.04"
date: 2010-07-11
forum: General Help
---

### Post by tom.swartz07 on 2010-07-11
Hi all,

Okay, so- Here is my predicament. I just got a new XBox 360, and I would like to get it connected to the internet. 

I cannot run hardline Ethernet to it, as the nearest line is across the house.

I have, in the past and on friends machines, had success setting up a shared internet connection from my Ubuntu box to the XBox in question. I would always follow this guide, and it would work right away. [http://linuxers.org/howto/how-share-internet-with-other-computers-linux](http://linuxers.org/howto/how-share-internet-with-other-computers-linux)

Recently, I have purchased a new wifi router. This has changed the DHCP makeup of my home network from 192.xxx.xxx.x numbers to 10.0.0.x. I dont know why, but thats how the Netgear router set things up. I have reserved addresses 10.0.0.(2-4) for specific computers because of remote access needs, anything above 10.0.0.5 is empty. 

Following the guide that I linked above, I cannot get the XBox connected.

I believe that the fact that the rest of the network is listed under 10.x.x.x may be the culprit, as the DCHP server on MY computer would be assigning the same Local IP as the other devices on the network. (I.E. Giving the XBox 10.0.0.2 and my computer 10.0.0.2)

*To clarify how my network is connected; this is how the network is setup:*

**[SIZE="1"]Internet/Phone line ---> Verizon Westell DSL modem in 'bridged mode' (IP 192.168.x.x) ----> Netgear WGR614v10 Wireless (IP 10.0.0.1) ----> Computer connected via wifi (10.0.0.x) ====> Shared connection to XBox (IP ? supposedly 10.0.0.x)[/SIZE]**

Somewhere between the computer and the shared connection, The xBox is getting lost, and cannot connect. The troubleshooting shows that it could connect to the network, but it cannot access the internet as a whole.


Does anyone know what I could do to get this guy online? Even for just a few minutes? haha

---

### Post by tom.swartz07 on 2010-07-11
Bump

---

### Post by tom.swartz07 on 2010-07-11
Now when I plug the ethernet in to the xbox from the computer, I cannot access the internet from the computer.

---

### Post by Iowan on 2010-07-11
> **tom.swartz07 said:**
> Now when I plug the ethernet in to the xbox from the computer, I cannot access the internet from the computer.I hate it when things start slipping backwards...
With the xbox plugged in, check (from a terminal) **route -n** - I'm wondering if the default gateway got set to the xbox interface (that machine has two interfaces, I presume...)

---

### Post by tom.swartz07 on 2010-07-11
Haha! yeah, at least before i could still use the internet when I plugged in...

```
tom@tardis:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
tom@tardis:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 eth1
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
tom@tardis:~$ 

```

First one is with it plugged in, second is when its unplugged.
Again, plugged in I cannot access the internet on the host computer, unplugged its fine.

---

### Post by Iowan on 2010-07-11
A little translation... 
Which interface (eth0 or eth1) connects to internet, and which one connects to xbox? The gateway doesn't seem to change, but the "local" (?) net seems to have routes on both interfaces... that'll probably confuse things...

---

### Post by tom.swartz07 on 2010-07-11
> **Iowan said:**
> A little translation... 
Which interface (eth0 or eth1) connects to internet, and which one connects to xbox? The gateway doesn't seem to change, but the "local" (?) net seems to have routes on both interfaces... that'll probably confuse things...

Ah, My oversight. 

Eth1 is the Wifi that is connected to the internet.
Eth0 is the ethernet that is connected to the xbox with the (supposedly) shared connection.

Here's ifconfig, if that helps at all

```
tom@tardis:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:b9:84:59:33  
          inet6 addr: fe80::219:b9ff:fe84:5933/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75690 (75.6 KB)  TX bytes:194384 (194.3 KB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1c:26:0f:25:7c  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe0f:257c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:787768 errors:26 dropped:0 overruns:0 frame:489071
          TX packets:530057 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:909491149 (909.4 MB)  TX bytes:119932121 (119.9 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:346338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59234810 (59.2 MB)  TX bytes:59234810 (59.2 MB)

tom@tardis:~$ 

```

---

### Post by tom.swartz07 on 2010-07-11
Now when you say > The gateway doesn't seem to change, but the "local" (?) net seems to have routes on both interfaces... that'll probably confuse things...
What exactly do you mean?

How does one change this?

---

### Post by tom.swartz07 on 2010-07-12
13 hour bump?

---

### Post by Iowan on 2010-07-12
Let's back up and regroup for a moment...

Your Ubuntu machine has a DHCP server on eth0?
Is eth0 supposed to have a static address? (none shows in the **ifconfig** you just posted) 
You could probably change the range used by the router - otherwise, you should pick a different subnet for eth0 and it's DHCP clients (the xbox). Having eth0 and eth1 in the same 10.0.0.X subnet is likely a problem.
I think you mentioned that in your first post - it's just taken awhile for me to absorb it.  :)

---

### Post by tom.swartz07 on 2010-07-12
Eth1 (the wifi) has a static address (10.0.0.2)

Eth0 (connected to the xbox) doesnt currently have a static IP, but is allotted a range from 10.0.0.5 - 10.0.0.200


What other subnet could I use? 192.xxx is taken by the modem, 10.xxxxx is taken by the other devices and computers... 

What else is there to use? I tried several others but to no avail, it says theyre out of range?

---

### Post by Iowan on 2010-07-12
How many devices are using the 10.X.X.X subnet? 
10.0.0.X might be used, but I suspect 10.0.1.X or 10.0.2.X, etc., should be available. (???)
If you have a DHCP server handing out leases on eth0, then eth0 *should* have an address in the DHCP subnet (but outside the lease range).

The modem might use 192.168.0.X or 192.168.1.X - but that leaves several others in the 192.168.X.X range... In addition, the router *should* insulate the modem from the ICS box.
For what it's worth - there's another private IP range: 172.16.0.0 &#8211; 172.31.255.255
Hmmm... maybe we're getting too many options...

---

### Post by tom.swartz07 on 2010-07-12
> **Iowan said:**
> How many devices are using the 10.X.X.X subnet? 
10.0.0.X might be used, but I suspect 10.0.1.X or 10.0.2.X, etc., should be available. (???)
If you have a DHCP server handing out leases on eth0, then eth0 *should* have an address in the DHCP subnet (but outside the lease range).

The modem might use 192.168.0.X or 192.168.1.X - but that leaves several others in the 192.168.X.X range... In addition, the router *should* insulate the modem from the ICS box.
Hmmm... maybe we're getting too many options...

AHA!
I never thought about using 10.0.2.x

Ill see if that works!

---

### Post by tom.swartz07 on 2010-07-12
Now I can finally use the internet while plugged in, but still no success with the XBox.


I tried changing the IP to 10.0.2.1 in the network manager applet and firestarter, but nothing worked. I cannot use 10.0.1.x because it gives an error again. 

Looking on the XBox, while plugged into the computer, 
The Xbox reports the following information

IP 169.254.125.2
subnet 255.255.0.0
gateway 0.0.0.0

DNS 0.0.0.0
2nd DNS 0.0.0.0



But the Computer should have assigned the xbox a 10.0.2.x IP, right?

Whats going on here?

---

### Post by tom.swartz07 on 2010-07-12
Note: I forgot the output of the new route:```
tom@tardis:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 eth1
10.0.2.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
tom@tardis:~$ 

```

For some reason, it wont let me restart the DCHP server either.

Im calling it quits for tonight- Ill be back to try again tomorrow after work.

---

### Post by tom.swartz07 on 2010-07-13
21 hour bump?

---

### Post by tom.swartz07 on 2010-07-14
48 hour bump?

---

