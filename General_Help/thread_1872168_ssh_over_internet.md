---
title: "ssh over internet"
date: 2011-10-30
forum: General Help
---

### Post by matuskap on 2011-10-30
Hello,

I having trouble with ssh connection via internet. So far I managed to create connection via local network. I have 2 computers. One old piece of crap with newest ubuntu server. Second pc is ubuntu desktop 10.10 too with open ssh client/server installed. Both sitting behind router D-link DSL-2641B. I have ports forwarded in router(see snapshot).
[IMG]http://img694.imageshack.us/img694/1874/screenshotzoq.png[/IMG]
My ISP claims not to block any protocols at all. When i try to connect i use

```
ssh -p 8888 user@internet_address
``` 

By internet address i mean my real IP. Im trying to connect with the desktop pc to server. ALso ppl outside my network tried to connect with no success. They claim that it doesnt do anything for a very long time and have to abort. When i try to log i get message like

```
ssh: connect to host <my current address> port 8888: Connection refused
```

Anyone able to guide me here? Thx in advance.

---

### Post by Hawkoon on 2011-10-30
Can you see the port you have opened at all? [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Usually, if the response takes longer, that means the port is open but no service is listening on that port. You can verify this by trying some random port that you know should be closed. 

Did you tell the server to listen at your custom port or port 22?

~H

---

### Post by matuskap on 2011-10-30
Server is listening to 22 (i suppose, thats what is written in /etc/ssh/sshd_config). From what i understand router is redirecting it so that when i contact 8888 on Internet address it goes to stated network address port 22  which is server machine inside the network. Anyway, not 8888 nor 22 appear to be listened to according to CanYouSeeMe.org.

---

### Post by Hawkoon on 2011-10-30
How does your hosts.allow look like on the server? I added a line there: sshd: ALL
to be able to connect from LAN and via www.

Some other thought, are you running any firewall, like ufw?

~H

---

### Post by The Cog on 2011-10-30
Are you running a firewall on the ssh server that could be blocking the connection?

Can you confirm that the ssh server is actually listening on port 22? Use this command and post the results here (the arguments mean **n**umeric, **l**istening, **t**cp):
```
netstat -nlt
```

You don't need to forward UDP 8888 - ssh is a TCP protocol.

---

### Post by matuskap on 2011-10-30
hosts.allow on server edition is all commented completely. After adding sshd: ALL nothing changed in terms of access. Still only able to log via LAN.

```
netstat -nlt
```
returns
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.5:53          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN     
tcp6       0      0 :::995                  :::*                    LISTEN     
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
tcp6       0      0 :::110                  :::*                    LISTEN     
tcp6       0      0 :::143                  :::*                    LISTEN     
tcp6       0      0 :::8080                 :::*                    LISTEN     
tcp6       0      0 :::53                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 ::1:953                 :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
tcp6       0      0 :::993                  :::*                    LISTEN                LISTEN 
```

I dont use any custom firewall and from what i know ubuntu shouldnt block any ports by default, at least the desktop edition, dont know if this server edition is different somehow in this matter. 



```
/etc/ssh/sshd_config

```

looks like this:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

```

I know i dont need UDP but ive spent hours trying various solutions so im trying anything :).

---

### Post by Rhizoid on 2011-10-30
> **matuskap said:**
> I know i dont need UDP but ive spent hours trying various solutions so im trying anything :).

When in doubt - walk before running ;)  Does it work when port 22 is forwarded on the router? Try this first before trying to obfuscate the port number.

Are you trying to connect to the external ip address of the router from the LAN side of the router?  Depending on the router you're using this may not work.  If you are trying this you'll need to test the port forward from another internet connection to be sure it is/isn't working.  From the settings you've listed above it looks correct to me and should work.

Hope that helps,

---

### Post by The Cog on 2011-10-30
This line> tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN shows that you are listening for incoming connections on port 22, on all IP addresses on the PC. Good.
No firewall running, so that's not the problem.
The router port forwarding you posted looks good to me.

I wonder if you are getting confused by the addresses. When you are local to the server, you need to connect to port 22 of the server, e.g.
> ssh user@192.168.1.3
Try this first and verify that it works. You will not be able to connect to your public_address:8888 from the server location - the router's port forwarding won't work that way.

When connecting from elsewhere on the internet, you will need to connect to your publuc address, not your local 192.168.1.3 address:
> ssh -p 8888 user@public_address

Maybe you already understand all this - I'm not clear from your posts. If I'm telling you what you already know, then sorry but I've got no ideas beyond that.

---

### Post by matuskap on 2011-10-30
Local connection works, i already tested that in both ways server<->desktop. It is Access from internet what i cant quite master. I use external address from [http://www.whatismyip.com/](http://www.whatismyip.com/). It also corresponds with address that my router shows me to be my external IP. My ISP tells me im not behind any NAT or anything and no protocols are being blocked. Friends tried to connect from outside with no success. They claim after attempt to connect theres no response and they have to cancel with <Ctrl + c>.

I alone have no other option then to connect while both pcs being behind my router for the time being.

---

### Post by Hawkoon on 2011-10-30
Could you check the LAN IPs of your client and server? 

I've been fiddling around here and just got the same error message that you reported in your first post when I accidentally tried to ssh into the client.

So maybe you have mixed up the LAN IP's, i.e. you used the client IP for the port-forwarding rule.

~H

---

### Post by matuskap on 2011-10-30
In router i only opened port for server and also set static LAN address for it. So its assigned the same subnetwork address every time it reconnects. My internet connection tho isnt static so i have to check that one every time i relog and so...

---

### Post by Slim Odds on 2011-10-30
> **matuskap said:**
> In router i only opened port for server and also set static LAN address for it. So its assigned the same subnetwork address every time it reconnects. My internet connection tho isnt static so i have to check that one every time i relog and so...

It still sounds like port 8888 is not getting to your router. Try port 22 or 23 instead. I once worked at a company that was blocking 22 outbound, so I changed to 23 and that worked fine.

---

### Post by matuskap on 2011-10-30
Port 22 gets me inside the router. I mean router itself... Thats why i tried to redirect via 8888.

---

### Post by Urbanmoth on 2011-10-30
This may sound dumb (and apologies if it is!) but have you tried to connect without a username? i.e. ssh - p 8888 <your_ip> and force a full login?

---

### Post by Slim Odds on 2011-10-30
> **matuskap said:**
> Port 22 gets me inside the router. I mean router itself... Thats why i tried to redirect via 8888.

8888 is not a good choice as it is reserved for other uses.

Why don't you use 22? or 23?

---

### Post by Hawkoon on 2011-10-30
> **matuskap said:**
> Port 22 gets me inside the router. I mean router itself... 

I don't know what you mean by that. Is the router running some service on 22???

Did you try any ports above 50.000 for forwarding, and any other ports on the ssh server apart from 22 (e.g. the same you use for forwarding)? I know you said ssh is working via LAN, but everyone seems to be running out of ideas. Also, you need to restart the server after editing sshd_config (sorry if you know all this already).

And just to double check, can you post output from ifconfig from both server and client and the statement you use to connect via LAN?

~H

---

### Post by Hawkoon on 2011-10-30
ah, seems there ARE still some more ideas out there.... i am such a slow writer :)

---

### Post by matuskap on 2011-10-30
Router has its own remote access, for remote management via ssh. So if i call ssh -p 22 routeruser@internet_address i get into router itself... Not computer sitting behind listening to 22. 

Now: 
Ifconfig of server

```
eth0      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe84:198f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:395505 (395.5 KB)  TX bytes:420332 (420.3 KB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1208743 (1.2 MB)  TX bytes:1208743 (1.2 MB)

virbr0    Link encap:Ethernet  HWaddr 
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Ifconfig of desktop 

```
eth0      Link encap:Ethernet  HWaddr 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146051 (146.0 KB)  TX bytes:146051 (146.0 KB)

wlan0     Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fe65:58c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1795785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1034172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2603521922 (2.6 GB)  TX bytes:109188948 (109.1 MB)

```

To connect via LAN(which is currently working) i use 
```
ssh <user>@192.168.1.5
```

I changed port to 58888 to avoid any collisions with apps using that port by default (apache does so as as ive found out) but outcome still remains the same. 

```
ssh -p 58888 <user>@current_internet_Address
```

says connection refused for me and nothing happening for others outside my network.

---

### Post by Urbanmoth on 2011-10-30
In your first post (screenshot) it looks like you are forwarding to 192.168.1.3 whereas in your post above you seem to suggest that your server is at 192.168.1.5.

May also be a good idea to edit and hide your mac address info in your last post (I know, I'm paranoid!)

---

### Post by Hawkoon on 2011-10-30
Ahhh, your forwarding rule is wrong. ssh is directed to your desktop, not the server IP. Change the destination IP to 192.168.1.5 and things should finally work for you.

~H

---

### Post by matuskap on 2011-10-30
Nono its all set right desktop is 192.168.1.whatever and server is 192.168.1.5 it has changed since last post sorry i didnt mention it in previous post... Ive been testing it a lot since topic rose up so... :) Well to be perfectly clear .5 server .3 desktop and new router redirect: [IMG]http://img36.imageshack.us/img36/8733/screenshot1zg.png[/IMG]

This happened cause before i was always checking servers address after router restart, later i set server address to static so its .5 now and so is the forward rule, in another words problem is elsewhere and still persisting.

---

### Post by Urbanmoth on 2011-10-30
I confess to being stumped.:confused:

As far as I can tell it should work (I have a similar setup working fine myself, albeit with a different make of router). 

Are you totally sure you do not have a firewall running? To be honest if you are thinking of exposing a server on your network to the internet this would be a smart thing to do... 

What is the output of the following on your server?:

```
sudo iptables -L -n
```

The only other possibility that comes to mind is some conflict with any router based firewall (not sure if you have one of those or even if your router provides the option).

---

### Post by Hawkoon on 2011-10-31
I am beginning to wonder... your router has a built-in firewall according to specs, amongst a lot of other security features. So at this point I think your router is what is causing the problem.

Can you try with the security features turned off?

~H

---

### Post by matuskap on 2011-10-31
```
sudo iptables -L -n
```

returns 

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:67 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            192.168.122.0/24    state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.122.0/24     0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

Well about the security features off, i dont know what else could i turn off cause i tried to turn off all that seems to be security related and still no result. Besides id expect the router to be smart enough not block SSH protocol and most certainly not when its even being forwarded through listed port... Well i dont know what else could i try, mby just move the server behind some other router of some friend of mine and try if it works, but this may be a little complicated if possible at all for now, so i need some other solution.

---

### Post by Hawkoon on 2011-10-31
I am not all that familiar with iptables, but your output suggests some rules are active. According to [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) you can temporarily disable iptables
```
sudo iptables -F
```if that still fails you... I can only think of trying a less fancy router.

~H

---

### Post by The Cog on 2011-10-31
Where did that iptables output come from? Your client, server, router?
I don't see anything in post #24 that allows ssh to the INPUT chain. Also, the FORWARD chain looks as though it allows all packets, from any source or destination, which is strange. If you use **iptables -nvL** this will also list any port clauses in the rules.

---

### Post by matuskap on 2011-10-31
```
Chain INPUT (policy ACCEPT 5517 packets, 1290K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
    0     0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
    0     0 ACCEPT     udp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ACCEPT     tcp  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      virbr0  0.0.0.0/0            192.168.122.0/24    state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  virbr0 *       192.168.122.0/24     0.0.0.0/0           
    0     0 ACCEPT     all  --  virbr0 virbr0  0.0.0.0/0            0.0.0.0/0           
    0     0 REJECT     all  --  *      virbr0  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 REJECT     all  --  virbr0 *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT 4546 packets, 1176K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

This is return statement from 

```
iptables -nvL
``` 

Both this and the one in previous post are from server.

---

### Post by The Cog on 2011-10-31
Well that's an odd looking set of rules. It's not blocking anything incoming to the INPUT chain. And I'm not sure what the FORWARD chain is doing. I've never heard of a virbr0 interface either, actually. 

But since the rules are from the server, I don't see why any incoming SSH should be dropped.

My next step would be to use tcpdump or wireshark to see if the packets are actually arriving at the server, and if it responds.

---

### Post by matuskap on 2011-11-01
Well now i tried tshark(cause theres no X on server machine) but im not quite sure what to do with it. So i tried to solve it with logs but auth logs show no sign of traffic when i attempt to login via internet, only via LAN are being shown, so i guess there is no traffic in the first place and the problem really is in the router i use, which is shame since i bought it month ago :( so i hope i can resolve this. Any suggestion on how to use tshark to get desired information?

---

### Post by The Cog on 2011-11-01
If the packets aren't reaching the server (or if the returning connect accept is being dropped) then the auth log won't show any login attempts.

The idea of the sniffer is to try and work out where the problem lies - is a TCP SYN (connect request) arriving at the server, is it on the right port number, is the server replying at all? 

If there is no  connect request (SYN) arriving then your issue is with the router and its config.

If the SYN is arriving as expected but the server ignores it, suspect firewall rules in the server.

If the server is responding to the SYN with a SYN ACK, then there should be another ACK from the client immediately after. If not, then suspect firewalling somewhere preventing the SYN ACK from reply reaching the client.

Tshark won't tell you what the problem is, but will help figure out where it is.

---

### Post by matuskap on 2011-11-01
Well i wont be physically able to access the server from tomorrow and since i havent figured out why im not able to establish a connection from outside i cant work on it any further so im gonna try last few things and hopefully something will work. For now it appears its a routers fault(even with firewall disabled), which in different circumstances might even be called a security feature ^^.

---

### Post by Urbanmoth on 2011-11-01
You have a strange set of rules from the iptables response - I am no expert and cannot logically decider them. Given that you are running out of time here and do not seem to be that bothered about being secure you could try disabling the firewall altogether

To do this enter the following commands

You may want to do a ```
sudo iptables-save > firewall.rules
``` before you do this just in case you need to restore the current config for some reason.


```
$ sudo iptables -X
$ sudo iptables -t nat -F
$ sudo iptables -t nat -X
$ sudo iptables -t mangle -F
$ sudo iptables -t mangle -X
$ sudo iptables -P INPUT ACCEPT
$ sudo iptables -P FORWARD ACCEPT
$ sudo iptables -P OUTPUT ACCEPT
```

This should fully disable the firewall on your server - just to reiterate I would not recommend this as a long term situation but at least you could eliminate the firewall from your investigations.

---

