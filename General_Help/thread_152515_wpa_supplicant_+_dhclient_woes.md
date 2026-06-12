---
title: "wpa_supplicant + dhclient woes"
date: 2006-03-30
forum: General Help
---

### Post by bakaink on 2006-03-30
Okay after trying to get my wireless to work with wpa_supplicant for the last... 6 hours I feel like I'm slamming my face into a brick wall. ](*,) 

Here's the symptoms:

when the wpa_supplicant is running, I am able to assosciate with my AP perfectly fine.  In fact, I can assign an address manually to my wireless interface and from there browse the web, etc etc etc.  However, when the wpa_supplicant daemon is running, dhclient ceases to function.  It sends out DHCPREQUEST packets, but it is as if they are getting lost somewhere between dhclient and the interface. Here's what I found puzzling:  I can't even use dhcp to assign an address on my wired network interface when I have wpa_supplicant up and running.

I'm running Ubuntu 5.10 brezzy with:
wpa_supplicant 0.4.5
ieee80211 1.1.12
ipw2200 1-1-1
kernel 2.6.12-10-686
dhclient 3.0.2

/etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

#eapol_version=1
ap_scan=2
#fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="******"
        pairwise=TKIP
        proto=WPA
        key_mgmt=WPA-PSK
        psk=******
}

```

/etc/default/wpasupplicant
```
ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

#OPTIONS="-w"

# EXAMPLES

OPTIONS="-i eth1 -c /etc/wpa_supplicant.conf -D ipw -wB"

```

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        hostname yomiko

#iface eth1 inet static
iface eth1 inet dhcp
        hostname yomiko
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5

```

Any insight into this issue would be much appreciated

---

### Post by Saint Peter on 2006-04-29
I am having this EXACT same issue.

pc is a Dell Inspiron 1100 notebook
wirless card is a D-Link WNA2330

I can ping the gateway if I assign an ip address manually, but dhclient cannot obtain a lease.

---

### Post by kenny-x on 2006-05-10
the porblem with the iwp2200 card and wpa_supplicant is an option in the module
if u load your module with the option hwcrypto=0 it should work.
works with me.

it mea be that the other card has the same problem

---

