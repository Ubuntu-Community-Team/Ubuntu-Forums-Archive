---
title: "Setting up a static IP"
date: 2010-07-16
forum: General Help
---

### Post by themusicalduck on 2010-07-16
I'm trying to setup a static IP on my network so that I can do some port forwarding with my router.

I've searched around and tried a few things, none of which worked. Mostly they just broke my internet connection completely.

What is the best way to set up a static IP in 10.04?

---

### Post by bodhi.zazen on 2010-07-16
Simply stating that you are having problems or that it is broken is not very helpful.

Set a static IP address either in your router or via Networkmanager =)

If that is not working, what have you done and what is broken ?

personally on a server I would remove networkmanager (assuming you have it installed) and configure a static IP in /etc/networking/interfaces =)

Post your config files or tell us what you have done and what is broken.

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by The Cog on 2010-07-16
The best way is probably to configure your DHCP server (probably your router) to always apply the same IP address to the PC's MAC address. Most DHCP servers allow this, and it is easier than messing around with static configuration files.

Second option would be to use the network manager icon in the taskbar to configure a static IP address, network mask, default gateway and nameserver. I think you right-click the icon for options but can't remember for sure - this PC isn't running network manager.

Last option is to configure the more old-school way. You edit /etc/network/interfaces to look a bit like this (making sure you avoid addresses that the DHCP server might lease to other PCs but still using addresses in the same network number):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
and edit /etc/resolv.conf to have an entry for your name server like this:
> nameserver 192.168.1.1

---

### Post by themusicalduck on 2010-07-16
Thanks for the replies. Sorry my post wasn't too helpful, I think I figured that it would be something so silly that I'd missed that I would just ask for the best method to do it, or if anyone knew a link that was updated for 10.04.

Anyway, I actually found a link which gave me the right steps and I now have a static IP working. (I can spend hours on a problem, and as soon as I ask for the help, will often find the fix a few minutes after ;))

My next problem is this though, even though I've tried to forward the ports on my modem, I'm still getting "Connection refused" errors.

I'm trying to setup my computer to run as a shoutcast server, so I opened ports 8000-8001.

This is how I have it set up on my modems config page under NAT:

```
Rule Flavor	Redirect
IF Name	All
Protocol	TCP
Local Address From	192.168.1.20
Local Address To	192.168.1.20
Global IP From	0.0.0.0
Global IP To	0.0.0.0
Destination Port From	8000
Destination Port To	8001
Local Port	8000
```

Anyone have an idea why it would still be refusing connections?

---

### Post by betlog on 2010-07-16
Related question:
After editing /etc/network/interfaces and/or /etc/resolv.conf  how do we reinitialize them to make sure the changes take effect?
Do we need to do:
  reboot? 
  sudo dhclient -r eth0 & sudo dhclient ?
  sudo /etc/init.d/networking restart ?
  nothng at all? 
And if they reinitialize all by themselves, is there a delay? how much of a delay? (network stuff often is a bit slow)

---

### Post by Iowan on 2010-07-16
**sudo /etc/init.d/networking restart** is _my_ preferred method (unless you're running Network Manager - then a reboot is just easier). I haven't really gotten familiar with the "service" version, yet...

---

### Post by The Cog on 2010-07-16
Connection Refused would indicate that your shoutcast server isn't running, or listening on the right address. What's the output of ```
netstat -lntu
``` on the server?

---

### Post by themusicalduck on 2010-07-16
The server is definitely running. I've actually got it to work before on a different connection, so it seems like either the modem or the ISP is the problem.

Here is the result of netsat -lntu:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:50071         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:55226         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8001            0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:34541           0.0.0.0:*      
```

On these lines it says the right ports:```
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:8001            0.0.0.0:*               LISTEN   
```but the IP address is 0.0.0.0 rather than 127.0.0.1 like the others. Might that be related to the problem?

Also interesting, if I try to connect to the stream with VLC on the server using 127.0.0.1:8000 then the server outputs```
[dest: 127.0.0.1] server unavailable, disconnecting

```and VLC asks me for a login and password. Which I'm not sure what to put in for (there isn't a login name as far as I know).

---

### Post by dcstar on 2010-07-17
This thread now has basically nothing to do with the Title.

Start other threads with the actual problems so those of us cease wasting time trying to help someone who **doesn't** have a problem with "Setting up a static IP".

---

### Post by The Cog on 2010-07-17
0.0.0.0 is the correct address - it means it's listening on any address the machine has - the "wild card" address.

127.0.0.1 is the "loopback" address and is only used for the computer talking to itself. Every computer has a loopback port with this address on it.

The command **ifconfig** will show you your interfaces and what IP address they have. Other machines must connect to your non-loopback address, which should be the static assress you configured, so this is the address the router should forward to.

I am guessing that "connection refused" was because you were trying to connect to 127.0.0.1 on a different computer, and it was therefore trying to connect to its own server which wasn't there.

---

### Post by themusicalduck on 2010-07-17
EDIT: it seems like you can't connect to the server using the server itself as I got a chance to try connecting from another PC and it actually worked (once I started playing something). I assumed it would work on the same PC because it has before.

Anyway, I guess this is solved. Thanks for all the help everyone.



----------------
Actually I was getting connection refused while trying to connect with my actual IP address using the same computer as the server. (I assume it would work this way, just for testing purposes.) I only tried using 127.0.0.1, on the server, to see if it would work with a direct connection to localhost, circumventing the modem entirely.

This is how I tried to connect:

Open VLC, go to Open Network Stream, use [http://www.whatismyip.com/](http://www.whatismyip.com/) (for some reason ifconfig doesn't show my internet address but just my network address instead) and then use *ipaddress*:8000 with protocol http. I tried with port 8001 as well.

Then VLC terminal output gives me this ```
[0x87ba6d8] main access error: connection failed: Connection refused
[0x87ba6d8] access_http access error: cannot connect to 78.147.216.246:8000
[0x87ba6d8] main access error: connection failed: Connection refused
[0x87ba6d8] access_mms access error: cannot connect to 78.147.216.246:8000
[0xb6e029b0] main input error: open of `http://78.147.216.246:8000' failed: (null)


```

---

### Post by The Cog on 2010-07-18
Ah. You should appreciate that your internet router is doing address translation. The address shown is the server's "real" address, and this is the address you must use when talking to the server from inside your house. The address whatsmyip shows you is the public internet address that the router is translating to/from, and is the address that should be used by people connecting to your home via the internet. 

In general, it's not possible to connect to your public translated internet address from inside your home. I can think of technical reasons why it wouldn't work, and can't think of any easy way to overcome those.

---

