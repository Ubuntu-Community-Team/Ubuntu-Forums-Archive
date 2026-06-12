---
title: "Script Gnome network configuration"
date: 2006-05-17
forum: General Help
---

### Post by mority on 2006-05-17
Hi,

cay anyone tell me where Gnome stores the network configuration one enters at System -> Administration -> Networking? Or give me a hint where I might find a little introduction on how the whole Gnome configuration concept works?

I should describe my problem a little bit: I use Breezy Badger on my primary notebook which I use at home and at office. Of course the network configuration in my home network differs from the one in office. Now, I could just use DHCP. But I don't want to use DHCP at office because I want to get the same IP address everytime I connect to the office network. So I wrote an ugly script which looks something like this:
```

#!/bin/sh
#

# this script does the network configuration for my office network

echo "configuring eth1"
ifconfig eth1 192.168.x.y
echo "waiting 3 seconds for interface to come up"
sleep 3
echo "adding default gateway"
route add default gw 192.168.x.z
echo "creating /etc/resolv.conf"
echo "search domain.com" > /etc/resolv.conf
echo "nameserver 192.168.x.z" >> /etc/resolv.conf
echo "connection should be up and running. enjoy work..."

exit 0

```

I have a similar script for my home network. So everytime I come to office I start the script above and when I come home I start the other script.

The scripts work very well so far. The problem is: In System -> Administration -> Networking I may choose from only 2 options for the ethernet interface: DHCP or manual IP. If I enter a manual IP I would have to change it everytime I come to office or home. But I wrote the scripts to avoid just that in the first place. If I choose DHCP, Ubuntu is sending DHCP requests every 10 seconds even though the interface is already up and configured by the script! And those 10-second-interval DHCP requests are annoying the sysadmin at office.
Okay, I could suppress the DHCP requests by configuring some random static IP in the Gnome config and then leave it alone and use my scripts. But that would not be very consistent and I would never know what side effects this could have (for example Gnome periodically reconfiguring my network interface with the random IP address I entered there...).

My solution would be to rewrite the script in a way that it does not configure the interface directly through ifconfig but by modifying Gnome config files or something like that.

Any suggestions?

Thanks for your attention.

---

### Post by Ramses de Norre on 2006-05-17
The configuration is in /etc/network/interfaces.

---

### Post by mority on 2006-05-17
[QUOTE=Ramses de Norre]The configuration is in /etc/network/interfaces.[/QUOTE]

Hmm, that's kinda obvious. For some reason I thought there would be an extra Gnome layer between it, so that the config is written first in some Gnome config file before it goes to the system config files. Anyhow, thanks for reply.

---

### Post by it.henrik on 2006-05-17
> german kezboards suck! hahe .. so true

---

### Post by mority on 2006-05-17
[QUOTE=it.henrik]hahe .. so true[/QUOTE]

u r off top1c ;)

---

### Post by dave_m on 2006-05-17
wouldn't it be simpler to just add a new location?

---

### Post by mority on 2006-05-17
[QUOTE=dave_m]wouldn't it be simpler to just add a new location?[/QUOTE]

Yeah, I just discovered that location feature after posting here. But it does not really fit my needs because in my home network I set up a PPTP tunnel to connect to the gateway over wifi. And that does the script I wrote to configure my network setup at home. But I can't set up this PPTP tunnel via the Gnome network configuration interface.
But maybe I can use a combination of both. I'll have to think about sometime...

---

