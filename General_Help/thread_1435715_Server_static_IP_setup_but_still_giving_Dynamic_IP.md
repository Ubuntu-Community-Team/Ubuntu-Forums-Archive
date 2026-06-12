---
title: "Server static IP setup but still giving Dynamic IP's"
date: 2010-03-21
forum: General Help
---

### Post by OX!DE on 2010-03-21
I have setup like instructed in online tutorials.

Here is a copy of my interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet static
	address 192.168.0.6
	netmask 255.255.255.0
	gateway 192.168.0.1
```

and my resolv.conf
```
nameserver 194.168.4.100
nameserver 194.168.8.100
```

Thanks

---

### Post by dcstar on 2010-03-21
Do you actually have any sort of problem?

---

### Post by OX!DE on 2010-03-21
Yes. What is a server with a dynamic ip? I cannot do anything until it has a static ip which it is configured to do but is not doing it???

---

### Post by OX!DE on 2010-03-21
Bump**[B][B][B][B][B]**[/B][/B][/B][/B][/B]

---

### Post by dcstar on 2010-03-21
> **OX!DE said:**
> Yes. What is a server with a dynamic ip? I cannot do anything until it has a static ip which it is configured to do but is not doing it???

Server as supposed to **give **Dynamic IPs, if your problem is that the sever still **gets** an Dynamic IP then you should have clearly stated that.

---

### Post by OX!DE on 2010-03-21
> **dcstar said:**
> Server as supposed to **give **Dynamic IPs, if your problem is that the sever still **gets** an Dynamic IP then you should have clearly stated that.

Apologies, yes the server still gets an Dynamic IP can you help?

---

### Post by asmoore82 on 2010-03-21
It looks like you've got it, except for the line
```
#auto eth0
```
you need to uncomment this line to be
```
auto eth0
```

This "auto" does not enable DHCP, it controls whether or not the interface is
automatically started up at boot time.

If it still doesn't work you probably need to disable NetworkManager - see the link in my Signature.

---

### Post by lisati on 2010-03-21
Why not set your ROUTER to hand out a static IP to your server?

---

### Post by OX!DE on 2010-03-21
Yes I tried it with and without the comment. Disable network manager? I never knew Ubuntu Server came with that :/ (maybe it is just me). Maybe I should remove the dhcp client?

---

### Post by phen0m on 2010-03-21
*DELETED*
for realizing it was Ubuntu Server and probably doesn't have NetworkManager.

---

### Post by OX!DE on 2010-03-21
> **lisati said:**
> Why not set your ROUTER to hand out a static IP to your server?


and how do I do that..

---

### Post by lisati on 2010-03-21
> **OX!DE said:**
> and how do I do that..

It can depend on the router. On my Thomson Speedtouch router, I use its browser-based control panel, and check "always use the same address" on the configuration page for my server.

---

### Post by OX!DE on 2010-03-21
Well, I have got this..

[IMG]http://img444.imageshack.us/img444/1440/screenshotnetgearrouter.png[/IMG]

---

### Post by asmoore82 on 2010-03-21
> **OX!DE said:**
> Yes I tried it with and without the comment. Disable network manager? I never knew Ubuntu Server came with that :/ (maybe it is just me). Maybe I should remove the dhcp client?

NetworkManager is a dependency for a lot of stuff. If you've added any of Gnome, you probably have it.

---

### Post by lisati on 2010-03-21
> **OX!DE said:**
> Well, I have got this..

It looks similar (but not identical) to the control panel for my second router, a Netgear WGR614v7. Further down the menu on the left on mine there's a link for "LAN IP setup". Assuming yours is similar to mine, near the bottom of the LAN ip page there will be a section "address reservation" - you can click on "add" to choose a particular device that's not already listed as having a set address. Hope this helps.

---

### Post by OX!DE on 2010-03-22
> **lisati said:**
> It looks similar (but not identical) to the control panel for my second router, a Netgear WGR614v7. Further down the menu on the left on mine there's a link for "LAN IP setup". Assuming yours is similar to mine, near the bottom of the LAN ip page there will be a section "address reservation" - you can click on "add" to choose a particular device that's not already listed as having a set address. Hope this helps.

Ok, I added the device then restarted my router, guess what? The server was givin another new IP :(

[IMG]http://img535.imageshack.us/img535/1440/screenshotnetgearrouter.png[/IMG]

---

### Post by JigglyWiggly_ on 2010-03-22
I would just install the gui, and go to network manager and configure it from there. When you're done, closed gnome.
/etc/init.d/gdm stop

---

### Post by OX!DE on 2010-03-22
> **JigglyWiggly_ said:**
> I would just install the gui, and go to network manager and configure it from there. When you're done, closed gnome.
/etc/init.d/gdm stop

You gotta be kidding?

---

### Post by OX!DE on 2010-03-22
Bump

---

### Post by pbrane on 2010-03-22
If you have a default server setup then what you have should have do it. This is my interfaces file

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Make sure you are not using an IP address that is in the DHCP pool. Using the router to assign a static IP is completely unneccessary. Also it looks like you are using DNS from your router. Without DHCP your router won't give you the DNS nameservers. You should get your ISP nameservers and use those. Or openDNS if you like.
After that make sure you restart your network.
```

sudo /etc/init.d/networking restart

```

If you have installed NetworkManager you may need to remove it.

---

### Post by l4zy on 2010-03-22
auto iface eth0 static
ip xxx.xxx.xxx.xxx


and so on....

---

### Post by OX!DE on 2010-03-22
> **pbrane said:**
> If you have a default server setup then what you have should have do it. This is my interfaces file

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Make sure you are not using an IP address that is in the DHCP pool. Using the router to assign a static IP is completely unneccessary. Also it looks like you are using DNS from your router. Without DHCP your router won't give you the DNS nameservers. You should get your ISP nameservers and use those. Or openDNS if you like.
After that make sure you restart your network.
```

sudo /etc/init.d/networking restart

```

If you have installed NetworkManager you may need to remove it.

How would I find an IP address not in the DHCP Pool? Can you please elaborate I am a bit noob with this. Also how can I find my ISP nameservers? I thought 192.168.0.1 should work? How would I use openDNS?

Thanks.


EDIT: I looked opendns.com and use the name servers found at the bottom of the page. Now I guess it is just finding an IP that is not in the DHCP pool?

---

### Post by pbrane on 2010-03-22
I don't know what kind of router you're using, but generally you can see what address you get on a computer using DHCP and then try anything lower than that. Some where in your router there may be a LAN config page that shows the addresses that are administered by the DHCP server in your router. In a linksys it's on the basic setup page under DHCP starting address. Anything lower than this is not in the pool. Linksys wireless routers like the WRT54G generally start at 192.168.1.100. 

You maybe able to look on your ISP's website and find out their DNS IPs. On a linksys router using Ubuntu 9.10 I can see those in the Connection Information after right-clicking on the wireless icon in the notification area.

Okay, do you have a Netgear router? On page 2 in this thread it looks like a screenshot of your router. If so then your DHCP server is administering all of the addresses from 192.168.0.2 to 192.168.0.254. Which is all you can have on that network with a 24bit netmask. If you don't normally have 252 nodes needing addresses on your network then you can change this to something else. I only have about eight devices (computers, game consoles, etc.) that use my router, so I only allow 10 addresses in the DHCP pool. In your case you could change your starting IP to 192.168.0.100 and ending IP to 192.168.0.254. That would allow for 155 DHCP addresses and from 192.168.0.2 to 192.168.0.99 would bee free to use for static IPs.

---

### Post by OX!DE on 2010-03-22
Yes I have a netgear router. I have used the opendns nameservers and changed the DHCP pool then applied a new IP like you instructed. I then restart my router and again the webserver is given a new IP.

---

### Post by pbrane on 2010-03-22
Something on your server is requesting an address. Double check your /etc/network/interfaces file, make sure the static keyword is used. Also make sure that your ethernet card is actually *eth0*. type *ipconfig* in a terminal. It could be that you are not using eth0. If that is the case then you need to change your interfaces file to the correct ethx. udev will assign the ethx designation based on the MAC address of the ethernet card. If you changed the card after you installed ubuntu server then you may be running on eth1 and not eth0.

---

### Post by OX!DE on 2010-03-22
> **pbrane said:**
> Something on your server is requesting an address. Double check your /etc/network/interfaces file, make sure the static keyword is used. Also make sure that your ethernet card is actually *eth0*. type *ipconfig* in a terminal. It could be that you are not using eth0. If that is the case then you need to change your interfaces file to the correct ethx. udev will assign the ethx designation based on the MAC address of the ethernet card. If you changed the card after you installed ubuntu server then you may be running on eth1 and not eth0.

Ok here is my /etc/network/interfaces file
```

  GNU nano 2.0.9         File: /etc/network/interfaces                          

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.50
        netmask 255.255.255.0
        gateway 192.168.0.1
        broadcast 192.168.0.255


```

Here is my /etc/resolv.conf file
```

  GNU nano 2.0.9            File: /etc/resolv.conf                              

nameserver 208.67.222.222
nameserver 208.67.220.220

```

Here is the outcome of ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:b3:a2:71  
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:feb3:a271/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52216 (52.2 KB)  TX bytes:43872 (43.8 KB)
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

ipconfig returns this
```

No command 'ipconfig' found, did you mean:
 Command 'tpconfig' from package 'tpconfig' (universe)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'ifconfig' from package 'net-tools' (main)
ipconfig: command not found

```

do you mean ifconfig?

Thanks.

Lol just incase I am talking about my external IP so I can access the server from anywhere (durr).

---

### Post by OX!DE on 2010-03-22
Bump**[B][B][B][B][B]**[/B][/B][/B][/B][/B]

---

### Post by pbrane on 2010-03-22
oops, ifconfig is correct. And I don't even have a windows machine! From what you are showing me you ARE using a static IP of 192.168.0.50 on your server. If you want a static IP from your ISP you will most likely have to request and purchase one. You could use DynDNS for free though. Go to dyndns.org and setup a free domain name. Maybe your router has support for dyndns, if your IP changes the router will update the dyndns record. There are other free dynamic dns sites where you can get a domain name for free. You will of course have to choose from one of their subdomains. I use dyndns and can access my server from anywhere. If you have ssh access to your machine I would recommend finding a tutorial on how to change the default port and use key based authentication instead of passwords. I had several hundred password attempts on my ssh server before I changed the port and disabled passwords. In one week. All from the same country. Guess Google's not the only one being attacked.

You should be more specific about what you are trying to do. We could have helped you much sooner if all you wanted was a static IP from your provider. We all thought you were trying to set a static IP for your server on your LAN.

---

