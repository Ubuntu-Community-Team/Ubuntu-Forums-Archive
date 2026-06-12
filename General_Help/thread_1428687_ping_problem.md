---
title: "ping problem"
date: 2010-03-13
forum: General Help
---

### Post by weishigoname on 2010-03-13
I am using redhat9 host and ARM board for embedded development.I want them to share files with NFS.but did not succeed.return "unable to touch host error".when I ping each other ,did not response.but when I traceroute each other,succeeded,but take about 3000ms.
I configure ARM board : ip 192.168.0.50
                                   netmask 255.255.255.0
                                   gateway 192.168.0.1
                          default route :192.168.0.1
                          namesever 192.168.0.1
and for redhat9 host :ip 192.168.0.56
                                netmask 255.255.255.0
                               gateway 192.168.0.1
                             default route 192.168.0.1
                                nameserver 192.168.0.1
I use RJ45 line ,and connect them directly

---

### Post by Iowan on 2010-03-13
Is there a router in there, somewhere? Otherwise, what is 192.168.0.1?

---

### Post by efflandt on 2010-03-13
It is possible that something is trying to resolve a hostname for an IP and that times out unsuccessfully before it proceeds, or arp issues.  Have you tried **ping -n** or **/usr/sbin/traceroute -n**?

I once had an older SMC wireless router that when dumbed down to just wireless AP/switch (DHCP disabled and nothing connected to WAN), occasionally experienced 5 second arp delays (maybe trying to connect its unconnected WAN).

Some routers may have issues depending upon whether a static IP is within or outside of DHCP range.  For most, a static IP should NOT be within DHCP range.  But I heard that some routers are just the opposite, where a static IP has to be within DHCP range of the router.

---

### Post by weishigoname on 2010-03-13
no route ,no wireless ,host and arm board connect directly with RJ45 .I tried other host ,and ping is ok,NFS is fine ,and the OS is redhat 9 too.I used tftp .it is fine,and I used ping in bootloader ,it is fine .I can send data to ARM board via tftp

---

