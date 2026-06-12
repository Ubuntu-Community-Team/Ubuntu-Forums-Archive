---
title: "Network won't start at boot - I have to &quot;ifup eth0&quot; - why?"
date: 2006-05-11
forum: General Help
---

### Post by BrianK on 2006-05-11
Just installed Breezey.  During bootup, the network doesn't get started properly - I only get the loopback.  If I log on & run "ifup eth0" it comes up instantly.

What's going on here?

FYI: this is a basic server install - no X or anything like that.

---

### Post by apollyonis on 2006-05-12
Open Terminal and do the following:

```
sudo more /etc/network/interfaces > ~/Desktop/eth0.txt
```
-this will make a backup copy of the current network config.

Doing the following will show the output in Read-Only; show us what whole file reads on here so that we can see how the network interface is set up.

```
gedit /etc/network/interfaces
```

Also, copy the contents of the ifstate to see if it has been modified or set up correctly.

```
gedit /etc/network/run/ifstate
```

The following is just an example of what a normal bootup network config looks like off of a live CD.

```
# This file describes the network interfaces available on your system
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

```

---

### Post by BrianK on 2006-05-12
[QUOTE=apollyonis]Open Terminal and do the following:
[/QUOTE]

the only thing different in those two files between working and non-working computers is the order in ifstate - where lo is first here as opposed to eth0 being first elsewhere...  does order make a difference?

I would try it right now, but I'm out of the office & don't want to lose access to that computer if I reboot it & the network doesn't come back up...

```

root@element02:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
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
# iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.0.52
        netmask 255.255.255.0
        gateway 192.168.0.1

root@element02:~# cat /etc/network/run/ifstate
lo=lo
eth0=eth0

```

---

### Post by geetarista on 2006-05-12
This worked for me:

```
sudo ndiswrapper -m
```

---

### Post by BrianK on 2006-05-12
if I read the man page for ndiswrapper correctly, this will not help me as I'm not using wireless.

---

