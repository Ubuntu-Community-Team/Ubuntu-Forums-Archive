---
title: "Freezing Gnome"
date: 2006-06-07
forum: General Help
---

### Post by fdimmling on 2006-06-07
I have made a fresh install of Dapper on my Acer Travelmate 4652LMi - 1.73 Centrino, Intel 915 graphics, ipw2200 WLAN. 

From time to time Gnome freezes right after the desktop is complete. I cannot start any program though the mouse is moving. Ctrl-Alt-F2 gives me a console to restart the computer. I'm using network-manager. The freeze occurs after nm has successfully connected to the WPA AP.

Any ideas - just a bug to be reported?

Friedrich

---

### Post by PhoenixP3K on 2006-06-07
Had the same hard freeze problem with my DWL-G122 Wireless USB connector. You might have to try and set it using command lines. Here is [the thread]("http://www.ubuntuforums.org/showthread.php?t=187201&highlight=DWL-G122")

So instead of using the network manager open a terminal window and use this

sudo iwconfig rausb0 essid <my SSID>
sudo iwconfig rausb0 key <my WEP key>
sudo dhclient rausb0

If this works and you have no freeze you can then edit /etc/network/interfaces to make the wireless configuration automatic on startup:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# iface eth0 inet dhcp

auto rausb0

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid <my SSID>
pre-up iwconfig rausb0 key <my WEP key>
pre-up dhclient rausb0
```

This method worked for me, it might work for you as well.

---

### Post by fdimmling on 2006-06-07
Since I like the network manager very much because it allows smooth switching between ethernet and wireless networks I might prefer restarting the laptop from time to time. In Breezy I used wifi-radar which would be a possibility for Dapper too I guess if nm is really the culprit and I get tired of the restarting.

Friedrich

---

