---
title: "I can't connect to the Internet with Ubuntu 5.10 Live, even if with Win XP it is OK.."
date: 2006-05-24
forum: General Help
---

### Post by Eduardo F. del Peloso on 2006-05-24
Hi, people!

I am having trouble to connect to the Internet with Ubuntu 5.10 Live. My connection works OK with Windows XP Pro. Here is the output of the "ipconfig /all" command in WinXP:

Windows IP configuration
        Host Name . . . . . . . . . . . : vialactea
        Primary DNS Suffix. . . . . . . . : 
        Node Type . . . . . . . . . . . . : unknown
        IP Routing Enabled . . . . . : No
        WINS Proxy Enabled . . . . . . . . : No
        DNS Suffix Search List. . : cybernet.com.br

Ethernet adapter Local Area Connection
        Connection-specific DNS Suffix  . : cybernet.com.br
        Description . . . . . . . . . . . . . : VIA Rhine II Fast Ethernet Adapter
        Physical Address . . . . . . . . . . : 00-13-D4-3E-4A-EC
        DHCP Enabled. . . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.25
        Subnet Mask . . . . . . . . : 255.255.255.252
        Default Gateway. . . . . . . . . . . : 192.168.0.1
        DHCP Server. . . . . . . . . . . : 192.168.0.1
        DNS Servers. . . . . . . . . . . : 192.168.0.1
        what is lease. . . . . . . . . . : 24 May 2006 17:58:09
        Lease Expires. . . . . . . . . . : 24 May 2006 18:58:09

When I boot the computer through the Ubuntu 5.10 Live CD, and it tries to configure the network ("Configuring network with DHCP"), this message is issued:

"The Network Autoconfiguration was successful. However , no default route was set: the system does not know how to communicate with hosts on the INTERNET. This will make it impossible to continue with the installation unless u have the First Official Ubuntu CD-ROM, a NetInst CD-ROM, or packages avaible on a local network"

It then asks me "Continue without default route?". If I say "No", boot proceeds, but I don't get to access any website. If I say "Yes", it asks for a "Name Server" (the DNS, if I am not wrong) number. I tried to enter "192.168.0.1", which is the number displayed when I issue the "ipconfig /all" command in WinXP. The result is the same: boot proceeds, but I can't connect to any website.

Just one other piece of information: this is the output of the "ifconfig -a" command when running Ubuntu:

ubuntu@ubuntu:/media/KINGSTON$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D4:3E:4A:EC
          inet addr:192.168.0.25  Bcast:192.168.0.27  Mask:255.255.255.252
          inet6 addr: fe80::213:d4ff:fe3e:4aec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14238 (13.9 KiB)  TX bytes:2772 (2.7 KiB)
          Interrupt:23 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:613253 (598.8 KiB)  TX bytes:613253 (598.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

And this is the output of the "netstat -nr" command:

ubuntu@ubuntu:/media/KINGSTON$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.24    *               255.255.255.252 U         0 0          0 eth0

Anyone has any idea what I can do? 
Thank you, advance!!!!!

---

### Post by an.echte.trilingue on 2006-05-24
are you behind a router or a so-called dsl modem?

---

### Post by Eduardo F. del Peloso on 2006-05-24
[QUOTE=an.echte.trilingue]are you behind a router or a so-called dsl modem?[/QUOTE]

I must confess I do not understand networks well enough to answer your question... But I can try to describe how my Internet access is implemented.

I have contracted an ISP that provides access for a number of apartments in my building. One cable reaches one computer in my building, coming from the telephone company. The ISP distributes the access from this computer to those in the apartments. I do not have a modem in my apartment: the network cable (blue with a RJ-45 plug) comes out of the wall and is connected directly into my standard 10/100 Ethernet card.

Hope this information is enough for you to determine if I am behind a router or a "dsl modem"...

Thanks!

---

### Post by jvictor on 2006-05-25
Looks like u r getting the connection shared. What you need to do is after u boot up in 5.10, go to Sytem> admin > networking ; 
select ehternet >properties , change it to static ip and type in 

192.168.0.25::  as ur ip
Subnet Mask : : 255.255.255.252
Default Gateway:: 192.168.0.1


Next go to DNS tab ,
Add 192.168.0.1 as default gateway

Also u can try the cmd

route add -n gw 192.168.0.1

and reactivate the ethernet ifc

I also doubt if ur router 192.168.0.1 supports IPv6 and ubuntu is speaking IPV6 to it ?!

---

### Post by Slim Odds on 2006-05-25
[QUOTE=jvictor]Looks like u r getting the connection shared. What you need to do is after u boot up in 5.10, go to Sytem> admin > networking ; 
select ehternet >properties , change it to static ip and type in 

192.168.0.25::  as ur ip
Subnet Mask : : 255.255.255.252
Default Gateway:: 192.168.0.1


Next go to DNS tab ,
Add 192.168.0.1 as default gateway

Also u can try the cmd

route add -n gw 192.168.0.1

and reactivate the ethernet ifc

I also doubt if ur router 192.168.0.1 supports IPv6 and ubuntu is speaking IPV6 to it ?![/QUOTE]

This is **bad** advise. If your Windows setup uses DHCP, your Ubuntu setup should use DHCP. If you start *hard coding* IP addresses in a shared environment like this and you **will** have trouble at some point.

For some reason, it seems like the default route is missing.

Try this:```
route add default gw 192.168.0.1 eth0
```

---

### Post by Eduardo F. del Peloso on 2006-05-25
When I arrive at home, in a few hours, I will try the things you suggested.

Meanwhile, there are somethings I did not understand about what you said:

[QUOTE=jvictor]I also doubt if ur router 192.168.0.1 supports IPv6 and ubuntu is speaking IPV6 to it ?![/QUOTE]

I do not know:
1) What "IPV6" is...
2) If my router supports it.....
3) If ubuntu is actually "speaking IPV6 to it".........

How do I verify if topics 2 and 3 above are true?

By the way, do I have a router???? I mean, I do not have one at home. The network cable comes directly from the wall to the Ethernet card in my computer. When you say "ur router", do you mean that the computer that my ISP is using to distribute the connection to the building (to my appartment and the others) has one?

---

### Post by Slim Odds on 2006-05-25
[QUOTE=Eduardo F. del Peloso]When I arrive at home, in a few hours, I will try the things you suggested.

Meanwhile, there are somethings I did not understand about what you said:



I do not know:
1) What "IPV6" is...
2) If my router supports it.....
3) If ubuntu is actually "speaking IPV6 to it".........

How do I verify if topics 2 and 3 above are true?

By the way, do I have a router???? I mean, I do not have one at home. The network cable comes directly from the wall to the Ethernet card in my computer. When you say "ur router", do you mean that the computer that my ISP is using to distribute the connection to the building (to my appartment and the others) has one?[/QUOTE]

It is highly likely that you do have a router that allows the people in your building to share that internet connection. You should ask your provider for some more details about the configuration that they are using.

But, like I said in my previous post, **DO NOT use a STATIC IP address**. Your Windows configuration was clearly setup using DHCP. With DHCP, no one is guaranteed to get a same IP address all the time. Therefore, if you use a static address you will someday conflict with someone. Also, DHCP takes care of assigning the DNS servers, the default gateway, etc.

If DHCP is not working correctly, that is what you need to look into. I have used the Live CD for 5.10 with a router at home, and it worked fine with DHCP.

---

### Post by Eduardo F. del Peloso on 2006-05-25
[QUOTE=Slim Odds]Try this:```
route add default gw 192.168.0.1 eth0
```[/QUOTE]

Yesterday I was surfing the Internet at home (via Win XP :( ), searching for a solution to my problem, and I found a text that suggested almost the same thing you suggested, but without the 'eth0' in the end. I tried it, but it did not work. Here is the output I got:

```
ubuntu@ubuntu:~$ sudo route add default gw 192.168.0.1
SIOCADDRT: Network is unreachable
```

Would it be different if I tried "route add default gw 192.168.0.1 eth0" (as you suggested) instead of "route add default gw 192.168.0.1"? I can try it latter, when I arrive home (I am at my work now, where my Internet connection works quite well both with Win and Linux...).

---

### Post by Eduardo F. del Peloso on 2006-05-25
[QUOTE=Slim Odds]You should ask your provider for some more details about the configuration that they are using.[/QUOTE]

What should I ask, that will help me find a solution? My ISP has said very clearly that they do not provide support for Linux. So if I just ask someone "please, help me configure my Linux connection", they will say "no"...

But I believe that if I ask them things about the software/hardware they are using, they will answer. I just do not know what to ask...

---

### Post by jvictor on 2006-05-25
I admit Static IP was a kludge , but I suggested it to see if things are working. its **NOT** a permanent solution 

IPV6 is a 'futurstic' version of Ip addresses ( to be most  simple)

U are geting a shared conxn that eventually connects to a swtich / hub which eventually connects to a router, I am just guessing that these components maynot be understanding ipv6 whereas ubuntu is using IPV6, u can disable it , plz search the forums on how to do it

What are things u need to know from ur ISP..
1) Ur ISPs DNS Server
2) Ur default gateway IP

---

### Post by Eduardo F. del Peloso on 2006-05-26
[QUOTE=jvictor]I admit Static IP was a kludge , but I suggested it to see if things are working. its **NOT** a permanent solution 

IPV6 is a 'futurstic' version of Ip addresses ( to be most  simple)

U are geting a shared conxn that eventually connects to a swtich / hub which eventually connects to a router, I am just guessing that these components maynot be understanding ipv6 whereas ubuntu is using IPV6, u can disable it , plz search the forums on how to do it

What are things u need to know from ur ISP..
1) Ur ISPs DNS Server
2) Ur default gateway IP[/QUOTE]

I found out, thru the forum, how to disable IPV6 (renaming a certain file I don't remember the name right now...). It did not work.

I also tried to change the conection settings from DHCP to  static, entering the number I got from the "ipconfig" Win XP command. Nothing happened... :(

I will contact my ISP and ask for the DNS and default gateway IP numbers.

---

### Post by jvictor on 2006-05-26
Ok we have a prob here. 
Bcoz to what I know we need to rstart with IPV6 disabled. Now since everything is in volatile memory & since u r using the live cd we are held up here. ie all chages u make are temporary 

Next part, you need a valid IP address that is assigned to u. mostly DHCP should work, but again we need to work on it.


Finally we need the DNS ( preferably both primary DNS and secondary DNS from ur ISP)

The default gateway will be usually your router that the ISP has installed in your building. ie 192.168.0.1

can u plz paste the o/p of

$route

---

### Post by Slim Odds on 2006-05-26
[QUOTE=Eduardo F. del Peloso]
I will contact my ISP and ask for the DNS and default gateway IP numbers.[/QUOTE]

Your first post shows you everything that you need to know. Windows is working properly with DHCP and it's getting all the information that your ISP wants you to use (DNS, gateway, etc.)

---

### Post by Eduardo F. del Peloso on 2006-05-26
Just before your last post, I contacted my ISP to ask the numbers. You are right, the numbers my ISP gave me are the same that I get from the "ipconfig" Win XP command.

So, now the million-dollar-question: if Windows works correctly with DHCP, why can't I use the Internet with Ubuntu?????

Did you read my post in which I wrote the output of the "sudo route add default gw 192.168.0.1" command, by the way? Even though I don't understand it, it sounds like useful information...:

```
ubuntu@ubuntu:~$ sudo route add default gw 192.168.0.1
SIOCADDRT: Network is unreachable
```

I have also tried to issue a "sudo dhclient eth0" command. Here is the output:

```
ubuntu@ubuntu:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 24869
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:d4:3e:4a:ec
Sending on   LPF/eth0/00:13:d4:3e:4a:ec
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
SIOCADDRT: Network is unreachable
bound to 192.168.0.25 -- renewal in 1693 seconds.
```

See? Here is the "SIOCADDRT: Network is unreachable" message again...

I have tried to find info about this error message in the Internet. I have found somethings, like the following (at [http://www.uit.co.uk/practical-tcpip/w-rterr-015.htm](http://www.uit.co.uk/practical-tcpip/w-rterr-015.htm))

```
SIOCADDRT: Network is unreachable

route add default gw 1.2.3.4

The routeraddr isn’t on a directly-connected network so this machine would be unable to forward packets to it.
```

and the following (at [http://www.scyld.com/pipermail/realtek/2000-February/000392.html](http://www.scyld.com/pipermail/realtek/2000-February/000392.html))

```
> SIOCADDRT: Network is unreachable

That's a routing problem, not a network driver problem.  That can happen
if the gateway you specified is not reachable *within one hop*.  Either
you've specified the wrong gateway, the wrong network, or the wrong
subnet mask.  Without your routing table, it's hard to guess which.
```

I don't fully understand what these explanations, but I believe that I got the correct numbers (IP, subnet mask, gateway, etc.) because Win work OK with them, and they are the same numbers my ISP gave me...

---

### Post by 3rdalbum on 2006-05-26
DHCP is extraordinarily fickle. For reasons I can't comprehend, I could never get my Mac to use my ADSL modem with DHCP (although it should've), and I had to type in IP addresses. Same with Ubuntu PPC.

On my x86 computer (not sharing the connection), Windows detected with DHCP correctly and Ubuntu seemed to still require the IP addresses. I've seen another Mac setup where the DHCP works, but only on one computer at a time.

In short, DHCP sucks, and I'm not surprised you are having problems with it. Sorry this doesn't help at all; it's just a dose of reality.

---

### Post by jvictor on 2006-05-26
To add on, I guess most of the routers and switches that are commonly available are 'adjusted to satisfy' windows. I'd serious issues with my ADSL router (DLINK 502T ) when I used DHCP. So i switched to a static IP and things work smooth.

---

### Post by Eduardo F. del Peloso on 2006-05-26
I am *absolutely NOT* a fan of Micro$oft, but... If Windows works OK with DHCP, and Mac and Ubuntu don't, shouldn't we say that "Mac and Ubuntu suck"????? I mean, why is it DHCP's fault? 

Please, once again: I am no defender of Windows. I'd much rather use free software, like Ubuntu. But I must admit that it is letting me down with this Network problem...

To connect with Win XP all I have to do is say "use DHCP" and everything is setup automatically and correctly. Everything works smoothly. Ubuntu just says "Well, configuration was OK, but I can't find the router. Sorry!" and I stay without a connection....

---

### Post by jvictor on 2006-05-26
plz post the o/p of 

route -n

less /etc/resolv.conf

---

### Post by Slim Odds on 2006-05-26
[quote=Eduardo F. del Peloso]I am *absolutely NOT* a fan of Micro$oft, but... If Windows works OK with DHCP, and Mac and Ubuntu don't, shouldn't we say that "Mac and Ubuntu suck"????? I mean, why is it DHCP's fault? 

Please, once again: I am no defender of Windows. I'd much rather use free software, like Ubuntu. But I must admit that it is letting me down with this Network problem...

To connect with Win XP all I have to do is say "use DHCP" and everything is setup automatically and correctly. Everything works smoothly. Ubuntu just says "Well, configuration was OK, but I can't find the router. Sorry!" and I stay without a connection....[/quote] 
Don't get your hopes to high on Microsoft's DHCP implementation. It's got notorious timing issues of it's own. There is nothing wrong with DHCP in general and it's extremely valuable for moble system, like laptops.

As another example, Windows XP will **NOT** play nice with DHCP on my Netgear WGR614. Whereas, all of my linux machines work just fine. Sometimes it's other issues and can be a little hard to pin down.

But don't think for a minute that Windows is good at DHCP and linux is not, because that's just not true. In general, networking on linux is much, much better than under Windows.

---

### Post by Eduardo F. del Peloso on 2006-05-26
[QUOTE=jvictor]plz post the o/p of 

route -n

less /etc/resolv.conf[/QUOTE]

Here is the output of "route -n", imediatelly after boot:

```
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.24    0.0.0.0         255.255.255.252 U     0      0        0 eth0

```

Right after boot, there is simply no file named resolv.conf in the /etc directory...

If I issue a "sudo dhclient eth0" command:

```
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:13:d4:3e:4a:ec
Sending on   LPF/eth0/00:13:d4:3e:4a:ec
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
SIOCADDRT: Network is unreachable
chown: failed to get attributes of `/etc/resolv.conf': No such file or directorychmod:
failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.0.25 -- renewal in 1398 seconds.

```

the file is created:

```

ubuntu@ubuntu:~$ more /etc/resolv.conf
search cybernet.com.br
nameserver 192.168.0.1

```

---

### Post by jvictor on 2006-05-27
ok this is a ditch try .. to be honest

first run 

$ sudo dhclient eth0

plz post o/p after dhclient is run
$ route -n 


that will give you an ip address and gateway

now the next thing to do is add this gateway as the default gateway

$sudo route add -n gw 192.168.0.1

now try 

$nslookup yahoo.com

$ping 192.168.0.1

---

### Post by Slim Odds on 2006-05-27
The route table is definitely missing a **DEFAULT** route.

That's kind of important :D 

There should be a line that looks something like:```
0.0.0.0    192.168.0.1    0.0.0.0    UG    0    0    0    eth0
```

You add a default route like this:```
route add default gw 102.168.0.1
```

Hope that helps.

---

