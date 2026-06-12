---
title: "The IP addres change itself"
date: 2009-07-16
forum: General Help
---

### Post by mmbathan on 2009-07-16
Hi Guys,
 
I connect two computers using cross cable in Bridge mode
the two computers using Vmware to run ubuntu OS
I assign static IP address to the machines and they can ping each other 
 
the problem is one of the machines suddenly change its IP address to the network IP address that is connected via wireless. I tried to disconnect the wireless but the network does not work until I enable the wireless again.
 
how can I make the IP address unchangeable?
 
 
Regards,

---

### Post by lisati on 2009-07-16
Some routers can be set so that a particular machines are assigned a set IP address. My Netgear WGR614v7 has on its configuration page an option "LAN IP Setup" which I can use to do this.

---

### Post by komputes on 2009-07-16
NetworkManager should allow you to disable wireless only by right clicking on the nm-applet (two computer icon in your panel) and select "Enable Wireless".

If you do not want to automatically request an IP address from a DHCP server, rifht click nm-applet and select "Edit connections" editing the connection you want to set to a static IP instead of DHCP. Hope this helps. 

If you really cannot tuen off wireless without turning off networking, this may be a bug (depending on your hardware). Please provide the model number of you wireless and ethernet card by running the command:

$ lspci -vvnn > ~/lspci.txt

and then upload lspci.txt from your home dir to this thread.

Cheers

---

### Post by mmbathan on 2009-07-16
thank you guys,
 
I run a test between the two machines using the static IP address, so I do not to use the IP address from a DHCP server and I need to use the static IP address.
 
komputes find the file in the attachments
 
Regards,

---

### Post by iponeverything on 2009-07-16
configure your static interfaces from 

/etc/network/interfaces

Once you configure in that file, network manager will ignore it.

say the interface in eth0 add this stanza to the interfaces file:
(with the corrected ip and mask information)

```

iface eth0 inet static
      address 192.168.1.1
      netmask 255.255.255.0

auto eth0

```

---

### Post by mmbathan on 2009-07-16
thank you iponeverything
 
I'll try.
 
Regards,

---

### Post by mmbathan on 2009-07-16
assigning the IP address it is work 
 
but I can not ping the other machine while the two machines can ping their self.
 
```
bagside@bagvapp:~$ ping 192.168.137.129
PING 192.168.137.129 (192.168.137.129) 56(84) bytes of data.
64 bytes from 192.168.137.129: icmp_seq=1 ttl=64 time=0.293 ms
64 bytes from 192.168.137.129: icmp_seq=2 ttl=64 time=0.058 ms
 
--- 192.168.137.129 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.058/0.175/0.293/0.118 ms

[EMAIL="bagside@bagvapp:~$"]bagside@bagvapp:~$[/EMAIL] ping 192.168.137.111
PING 192.168.137.111 (192.168.137.111) 56(84) bytes of data.
From 192.168.137.129 icmp_seq=2 Destination Host Unreachable
From 192.168.137.129 icmp_seq=3 Destination Host Unreachable
From 192.168.137.129 icmp_seq=4 Destination Host Unreachable
 
--- 192.168.137.111 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3000ms
, pipe 3
[EMAIL="bagside@bagvapp:~$"]bagside@bagvapp:~$[/EMAIL] 

```

---

