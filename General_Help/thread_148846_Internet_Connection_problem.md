---
title: "Internet Connection problem"
date: 2006-03-22
forum: General Help
---

### Post by Fedcer on 2006-03-22
Hi, I have my pc with Ubuntu connected to router and I'm trying to configure the internet access but I havn't had any luck.
When I run the pppoeconf it gives me an error. With ping [ip of a pc in the local network] it connects succesfully. However if I try to connect with ping to a server in the internet, it fails.

This is the result of the command ifconfig eth0:

eth0   Link encap:Ethernet  HWaddr 00:07:E9:9E:96:C1
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17384 (16.9 KiB)  TX bytes:2434 (2.3 KiB)


This what /etc/network/interfaces contains:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

iface dsl-provider inet ppp
provider dsl-provider


This is the result of the command route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   Metric   Ref    Use    Iface
192.168.0.0     0.0.0.0            255.255.255.0   U         0          0        0      eth0
0.0.0.0            192.168.0.1     0.0.0.0             UG       0          0        0      eth0


This is what /etc/resolv.conf contains:

nameserver 192.168.0.1


Oh, and the router ip is 192.168.0.1


Thank you for the help!!

---

### Post by neoroses on 2006-03-22
just a thought...im not pro but might help - just check that system-->adminstration-->networking--><your adapter>--->properties is set to dhcp not static ip it may not be correct but just a idea

---

### Post by jamesr on 2006-03-22
Also the nameserver should not be your router, it needs to be the server as provided by ISP. 

Also why are you not using DHCP because depending the way your is setup this can automatically find the nameservers from ISP

---

### Post by Fedcer on 2006-03-23
Hi! Thank You both for the help! I am now using dhcp and added in the resolv.conf my ISP's IP. Now internet is working (in fact, I'm posting from ubuntu :) )

However, I have a new problem. DHCP automatiically asigns an IP to the pc and that ip is the same one another pc in my network has. So, they cannot be connected simultaneously. Any idea ?

Thank you,

Fedcer

---

### Post by dmizer on 2006-03-23
what is your ip address according to ifconfig?

edit to add: if you are using a router, what model and manufacture is it?

---

### Post by Fedcer on 2006-03-23
According to ifconfig my IP is 192.168.0.11, the same my other pc is using.

The router is a CNet CNIG-914

---

### Post by dmizer on 2006-03-23
check your router config to see how many ip's it allows to have leased.

how many computers do you have connected to your router? is your router wireless?

---

### Post by Fedcer on 2006-03-23
I have 4 (counting the ubuntu one) pc connected to the router and it is not wireless.

The IP pool is set to begin at 192.168.0.2 and end at 192.168.99, if that is what you're asking.

---

### Post by dmizer on 2006-03-23
yes.

have you tried rebooting your router?  strange that your router is handing you an 11 ip when you only have four computers attached to it.

---

### Post by jamesr on 2006-03-23
It is not usual to get non sequential addresses from a router. Are there any static addresses because the dhcp server can be confused by a static  address unless you define the addresses by MAC number.

---

### Post by dmizer on 2006-03-24
did a little research about your router. and there's a couple things i noticed.

the default ip for this router is 192.168.1.1 which means changes have been done to the router.  were you the one who performed the changes, or is this a used router, or did someone else configure it for you?  if it's used, you might be well off to simply reset the router to factory defaults by performing the following:

1- Unplug the router from power.
2- Press and hold the reset key for 8 seconds while you plug the router back to power.
3- Reboot (power off then power on) the ADSL/Cable modem.

default un and pass for this router is Username: admin and password: 0000 <-- zeros.

however ... simply power cycling the router (unplug power and reconnect power) will often times clear up these odd problems.  i don't think that this is a problem with ubuntu, but rather with your router, or with how your network is configured.

also, as jamesr suggests, do check the other 3 computers connected to your network and see how their network settings are configured.  this also may lead you to the root of your problem.

---

### Post by Fedcer on 2006-03-24
Hi guys, thank you for your replies.

Power cycling the reouter didn't change anything.

About the other pcs, they are all set with static IPs and I've just changed the one with the .11 ip to .4 so right now there aren't problems.

About the MAC number, I apologize for my ignorance but I've no idea what that is. :(

EDIT: Oh, and about the router IP, you read it from [http://www.cnetusa.com/support/faq/CNIG914%20Router%20FAQ.pdf](http://www.cnetusa.com/support/faq/CNIG914%20Router%20FAQ.pdf) right? 'Couse that must be a newer revision of the model or something like that because my manual says, as it in fact is, that the default ip of the router is 192.168.0.1

---

### Post by jamesr on 2006-03-25
MAC Address
Short for Media Access Control address, a hardware address that uniquely identifies each node of a network

Ie somewhere on the board there is a chip with a hardware address which is unique or so I believe.

---

