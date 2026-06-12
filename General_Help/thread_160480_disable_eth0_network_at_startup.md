---
title: "disable eth0 network at startup"
date: 2006-04-15
forum: General Help
---

### Post by marcwenger on 2006-04-15
I want to be able to disable Ubuntu to search for a network connection at startup on my laptop.  I've consulted other threads and resources and none of them work for me.

I used the BootUp Manager (BUM), but when I try to deselect startup services, it says "Editing in runlevel S is not allowed!...".

This is what my /etc/network/interfaces file currently has:

```
#This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp

#auto eth0
```

What should it say?

eth0 is my ethernet, eth1 is my wifi.  I want neither to startup.  Of course I will start them on a need-by-need basis, which I know how to do with Network Manager.


Thanks!  Any help is much appreciated

---

### Post by joft on 2006-04-15
Hi,

I'm not 100% sure, but did you try to disable the following lines of your /etc/network/interfaces file (by writing a # in front of them)?

[QUOTE=marcwenger]
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
[/QUOTE]

I guess that only eth0 is activate during the boot process at the moment? And eth1 is left alone, right?

---

### Post by hw-tph on 2006-04-15
Comment out The "script grep" and "map eth0" lines in the interfaces configuration file like joft said above. Then install ifplugd. ifplugd will bring up a network interface when there is a cable plugged in, and bring it down properly when the network cable is removed. It is great to have on both laptops and desktops.

Here is my simple config (/etc/default/ifplugd):
```
INTERFACES="eth0"
HOTPLUG_INTERFACES=""
ARGS="-q -f -u0 -d10 -w -I"
SUSPEND_ACTION="stop"
```

Håkan

---

### Post by marcwenger on 2006-04-15
Thanks a lot!  It worked

---

