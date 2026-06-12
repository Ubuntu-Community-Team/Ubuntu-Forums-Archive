---
title: "resolve hostname to two or more ip addresses"
date: 2011-10-12
forum: General Help
---

### Post by darthpenguin on 2011-10-12
Hi All

I have a Linksys with DD-wrt installed. I have a laptop with Ubuntu 11.04 which is connected to the network either by wireless (802.11n) or Ethernet or both (wireless doesn't turn off automatically when RJ-45 is plugged in). Obviously it has 2 ip addresses (wlan0 192.168.1.100, eth0 192.168.1.101). I would like to have both of these addresses resolve to the same host name (Thinkpad). I would also like the Ethernet connection to take priority if it is available (it is faster). I have been in the 'hosts' file in DD-wrt and added this

```

192.168.1.100   Thinkpad
192.168.1.101   Thinkpad

```
and
```

192.168.1.100 192.168.1.101 Thinkpad

```

But both just resolve 192.168.1.100 (wireless) and pinging the host name fails if I disable the wireless adapter on the Thinkpad (i.e. not falling back to eth0).

Is it possible to 'bind' two ip addresses to a single host name? Can it be done in the /etc/hosts file? Do I just have the syntax wrong? Is there something I need to do on the Thinkpad instead of the router? Do I just need to suck it up and have two host names for one machine?

---

### Post by darthpenguin on 2011-10-12
OK... funny thing. If I remove all entries for the Thinkpad from dd-wrt's hosts file I can ping the thinkpad using ping Thinkpad.local which will resolve to 192.168.1.101 first and 192.168.1.100 if the wired connection is not available. That is exactly the behavior I want but I'd rather not have to add the .local at the end (I don't need to for my other machines). Why do I need the .local? Is that a FQDN? Can I change it? Maybe add an alias to the router or something?

Thanks guys.

---

### Post by jonobr on 2011-10-12
I used to work with a solution that had two interfaces, each had an ip address  and one virtual IP address that attached onto the active interface. If one interface went down , the virutal IP was unplumbed from that one interface and plumbed onto the new interface,always staying with the active interface.

The Virtual Ip address could most likely have a name association with it, but the client machine would always attach to the virtual name/ip thus always going to the active interface
Ill take a look around and see If I can find it , as I think it was a common enough solution for nix systems.

---

### Post by jonobr on 2011-10-12
MMmmm looking at this I think it was doing what hearbeat does for ubuntu, howeverm, now that I read it, I think is more for 2 servers and attaching clients rather then one machine

---

### Post by prodigy_ on 2011-10-12
Try [this HOWTO](http://www.zivtech.com/blog/setting-ip-failover-heartbeat-and-pacemaker-ubuntu-lucid). A lot of reading and tinkering with configs but it's about dynamic switching of IP adresses between two interfaces which seems to be exactly what you want to do. This way you'll be able to use hosts file as usual (one IP - one hostname) and you'll be using the preferred (wired) connection when it's available.

---

### Post by The Sorrow on 2011-10-12
Can i ask why you would want multiple IPs to resolve the same host?

---

### Post by SeijiSensei on 2011-10-12
Try editing /etc/resolv.conf and adding the line

```
search local
```

at the top.  That will append .local to unqualified names like "thinkpad". 

If you use DHCP to obtain your IP configurations from the router, you need to take a different approach.  Edit /etc/dhcp3/dhclient.conf.  You'll see a line that demonstrates the use of the "prepend" directive to set a different DNS server.  In your case we want to add the search directive, so add the line:

```
prepend domain-search "local";
```

That will add the "search local" line to the top of /etc/resolv.conf automatically when the NICs get their addresses.

.local isn't a publicly-supported domain, but it's commonly used in small network settings like yours.

---

### Post by darthpenguin on 2011-10-12
> **prodigy_ said:**
> Try [this HOWTO](http://www.zivtech.com/blog/setting-ip-failover-heartbeat-and-pacemaker-ubuntu-lucid). A lot of reading and tinkering with configs but it's about dynamic switching of IP adresses between two interfaces which seems to be exactly what you want to do. This way you'll be able to use hosts file as usual (one IP - one hostname) and you'll be using the preferred (wired) connection when it's available.

Wow. That seems really complicated. This tutorial is for servers, though I guess it could be adapted to a workstation. I might look into this if I can't find a simpler solution. I'd rather not modify my Ubuntu installation too much. But thanks.

---

### Post by darthpenguin on 2011-10-12
> **SeijiSensei said:**
> Try editing /etc/resolv.conf and adding the line

```
search local
```

at the top.  That will append .local to unqualified names like "thinkpad". 

If you use DHCP to obtain your IP configurations from the router, you need to take a different approach.  Edit /etc/dhcp3/dhclient.conf.  You'll see a line that demonstrates the use of the "prepend" directive to set a different DNS server.  In your case we want to add the search directive, so add the line:

```
prepend domain-search "local";
```

That will add the "search local" line to the top of /etc/resolv.conf automatically when the NICs get their addresses.

.local isn't a publicly-supported domain, but it's commonly used in small network settings like yours.

I am using dhcp but have given the laptop 2 static IPs (one for each mac address). I can't find /etc/dhcp3/dhclient.conf on dd-wrt. Are you asking me to edit that file on the laptop?

---

### Post by darthpenguin on 2011-10-12
Here is a question. What is "Cloned MAC address"? It is a blank field in the "Editing Network" dialogs. Can I spoof a mac address or something? What is Cloned MAC address for? If I spoof the same mac address for both interfaces on the laptop could I then give that mac address a static ip on the router?

---

### Post by dcstar on 2011-10-13
> **darthpenguin said:**
> Here is a question. What is "Cloned MAC address"? It is a blank field in the "Editing Network" dialogs. Can I spoof a mac address or something? What is Cloned MAC address for? If I spoof the same mac address for both interfaces on the laptop could I then give that mac address a static ip on the router?
[LIST=1]
[*]It is changing the native MAC address on the hardware to use the MAC address of another Ethernet interface.
[*]Yes, if you know exactly what you are doing.
[*]For seamlessly replacing hardware so other equipment does not need to learn or adjust to a different MAC address.
[*]Maybe: ```
man arp
```
[/LIST]

---

### Post by SeijiSensei on 2011-10-13
> **darthpenguin said:**
> I am using dhcp but have given the laptop 2 static IPs (one for each mac address). I can't find /etc/dhcp3/dhclient.conf on dd-wrt. Are you asking me to edit that file on the laptop?

If you're using static IPs via entries in /etc/network/interfaces, then just add "search local" to resolv.conf manually.  If you made the addresses static by configuring them on the router, you need to edit the dhclient.conf on the laptop.

---

