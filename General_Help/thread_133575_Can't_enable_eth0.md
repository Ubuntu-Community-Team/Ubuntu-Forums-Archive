---
title: "Can't enable eth0"
date: 2006-02-20
forum: General Help
---

### Post by FlakJacket on 2006-02-20
For some reason I have to fight with the network module in kcontrol to enable my eth0 internal wireless card.  The little meter in my taskbar shows great reception and the network is unencrypted, but for some reason every time i hit enable interface it disables it seconds later. Sometimes it works but then when I shutdown the whole process starts over.

Please help,
 Flak

---

### Post by invalid on 2006-02-20
Why don't you try it via a terminal, and see exactly what output you get. It may help debug the problem. If you can't see what is going on, paste it here and we may be able to help.
```
sudo ifup eth0
```

---

### Post by FlakJacket on 2006-02-20
It tells me

```

There is already a pid file /var/run/dhclient.eth0.pid with pid 0
...Copyright info...

Listening on LPF/eth0/00:02:8a:92:f7:f6
Sending on LPF/eth0/00:02:8a:92:f7:f6
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
NO DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

```

Any help would be most appreciated.

Thanks,
  Flak

---

### Post by Vetto on 2006-02-20
1. what card chip is it? (dmesg |grep eth0) and look for the chip
2. post the text from your /etc/network/interfaces file.

---

### Post by FlakJacket on 2006-02-20
1.
```
 
[4294677.432000] natsemi eth0: NatSemi DP8381[56] at 0xd0008000 (0000:00:12.0), 00:0b:cd:8b:2c:1c, IRQ 10, port TP.
[4294709.561000] eth0: New link status: Connected (0001)

```

2.

I will post later when I have more time to type.

Thanks,
 Flak

---

### Post by Vetto on 2006-02-20
Is that a wireless card?  The National Semiconductor DP8381(56) cards are supposed to have drivers in the kernel, but it looks like a wired card, not a wireless card.  Does your laptop have two cards, wireless and ethernet?

---

### Post by FlakJacket on 2006-02-20
Yes my laptop has both wireless and ethernet cards.

Flak

EDIT: I just did dmesg on eth1 and it is my wireless card how would they get switched like that?

---

### Post by Vetto on 2006-02-21
Not sure about them getting "switched"...but suffice it to say that eth1 is your wireless card, not eth0.  Lets see your interfaces file, almost all issues can be fixed there if the card is working.

BTW, I am NOT an expert in this I can help with the basics...but you are in the right place to get this addressed and fixed. :)

---

### Post by FlakJacket on 2006-02-21
By switched I mean eth0 used to work as my wireless card and i've enable eth1 on an ethernet cable right now so i don't know why dmesg says that eth1 is wireless and eth0 is ethernet.

Here's my network file now that i have internet.

```

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
iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any

iface eth1 inet dhcp

auto eth0

```

Thanks for any help but I won't be able to test wireless for a couple days so I'll have to wait.

Flak

---

### Post by Vetto on 2006-02-25
From a term, type:
sudo iwconfig

That should list all interfaces and show you which is the wireless one.
Now, try to up the interface and then try to get an address:
sudo ifconfig eth0 up  (assuming eth0 is the wireless)
sudo dhclient eth0

you should get an address.

If not, ensure that the AP is not MAC filtering, check that it is not encrypted (no WEP or WPA), see what channel it is on and note the SSID for later troubleshooting.

---

### Post by FlakJacket on 2006-02-25
I'm home and it now works i'm not sure how but maybe it was the network I was on while away.  Thanks for all your help.

Flak

---

