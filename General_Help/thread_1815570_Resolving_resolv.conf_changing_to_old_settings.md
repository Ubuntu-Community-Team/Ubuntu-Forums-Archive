---
title: "Resolving resolv.conf changing to old settings"
date: 2011-07-31
forum: General Help
---

### Post by spleach on 2011-07-31
I've been annoyed by this for some time now.
Every time I restart the  network connections (I've been playing with IPv6 and bind settings a  lot), the resolv.conf file keeps changing my nameserver addresses to  old, outdated ones.

Manually changing /etc/resolv.conf is not persistent.

According  to various advice posted on the internet, I've changed settings in  /etc/dhcp[3]/dhclient.conf  to use the new, updated addresses as fixed  nameserver addresses. Still, the nameserver address in /etc/resolv.conf  changes every time I run
```
$ /etc/init.d/networking restart
```

A few recursive grep commands have helped me find a few files which contain the old address:-
e.g.
```
 sudo grep -r '192.168.old.IP' /etc/ /var/ /usr/ 
```

I since found a few files which contain the old addresses:-
/var/lib/dhcp[3]/dhclient.leases    (don't think I should update these though, as should be automatically  updated when dhcp restarts / reloads / refreshes)

I've obviously  changed /etc/network/interfaces and any custom scripts within that  directory tree to match the new adress, but still, resolv.conf keeps  changing back!!

The latest file I've found with the old address in is:-
/proc/net/arp

Even  the root user doesn't have write permission on this file, so I can't  change it by hand. Digging around google and a few 'man' pages, I see  that this can be changed with the `ip` or `arp` comands, but that arp  tables should NEVER be fixed! 

After running ```
$ /etc/init.d/networking restart
```, these are relevant parts of my settings:-

```

$ cat /etc/resolv.conf
nameserver 192.168.0.old  # Dead IP! Should be either 192.168.0.new or 127.0.0.1
nameserver 192.168.0.router
nameserver [VPN_DNS_server1]
nameserver [VPN_DNS_server2]

$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.old                    (incomplete)                              eth1
192.168.0.router              ether   [rout_MAC_ADDRESS]   C                     eth1

$ ip neigh show
192.168.0.old dev eth1  FAILED
192.168.0.router dev eth1 lladdr [rout_MAC_ADDRESS] STALE

```
This  is completely screwed. I want to delete the 192.168.0.old address, and  also update the router MAC address, which differs by one character for  some reason...

So, to fix:-
Delete FAILED entries using either arp...
```

$ sudo arp -d 192.168.0.old

```
.. or using ip
```

$ sudo ip neigh del 192.168.0.old dev eth1

```
The above info  commands don't show the dead MAC address. However, it was in  /proc/net/arp, so it's possible to run this additionally specifying the  link-local (mac) address :-
```

$ sudo ip neigh del 192.168.0.old dev eth1 lladdr [MAC_ADDRESS]

```

# Update router MAC address.
```

$ sudo arp -s 192.168.0.router [CONFIRMED_MAC_ADDRESS]

```
I'm  not sure which is the recommended way of doing this. I ran the `ip`  command first, got some form of error, ran the `arp` commands, and now  the bad entries have gone.

Still, running /etc/init.d/networking resets back to an incorrect resolv.conf file.

I  figure all scripts should be running out of the /etc/network/ directory  tree, but I've searched for files that contain resolv.conf within /etc.

Looks like /etc/ppp/ip-up.d/0dns-up is creating the resolv.conf file. It says:-

> 
# DNS1 and DNS2 are variables exported by pppd when using 'usepeerdns'.
# Do we have them?  If so, we are using "dynamic dns".  Append a couple of
# nameserver lines to the temp file.


I've never done anything with pppd before. hmph. Better start reading some more man pages.

---

### Post by spleach on 2011-08-03
I believe I've found the solution, in perhaps the most obvious of places. The Ubuntu [Network Configuration documentation]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html").

```
ip addr flush eth1
```

Now when I run:-
```
$ sudo /etc/init.d/networking restart
$ cat /etc/resolv.conf
domain example.com
search example.com
nameserver 192.168.0.old
nameserver 192.168.0.router

```

darn.. Back to looking for alternatives then... Any suggestions would be greatly appreciated!

---

