---
title: "Problem with dbus or wicd"
date: 2009-08-21
forum: General Help
---

### Post by p110011 on 2009-08-21
Hello, I have a problem of which I'm not sure how to classify, so I'll ask here.
I have Hardy Heron on a desktop pc that has worked great since 8.04.

The other day I got this message on booting up that says, wicd needs to access your network cars, so I type my password and wicd does nothing.

I get this when starting in the CLI:wicd-client

```
$ wicd-client
Has notifications support True
Loading...
Connecting to daemon...
Can't connect to the daemon, trying to start it automatically...
Connected.
ERROR:dbus.proxies:Introspect error on :1.51:/org/wicd/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
warning: ignoring exception org.freedesktop.DBus.Error.ServiceUnknown: The name :1.51 was not provided by any .service files
warning: ignoring exception org.freedesktop.DBus.Error.ServiceUnknown: The name :1.51 was not provided by any .service files
```I have tried searching this, (no luck) completely removing wicd, and reloading it from synaptic, reinstalling dbus and installing network manager. in NM I could see networks, but the connect button is grayed out.

Here is my lshw -c network

```
~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:6a:33:f9:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2870 driverversion=1.52+Ralink Technology, Corp.,11 link=no multicast=yes wireless=IEEE 802.11g

```When I enable the adapter the DISABLED goes away.

So I'm not sure if this a network fault, or system (dbus) and is there someway to fix this easily, or can I fix it by upgrading to 8.10? 

I really like the way it has going, till now:) so I hope the first way is possible.

p.s. I posted in networking a few days ago, but it seems I may be out of luck

Thanks, 

Gill

Not really solved, but I wiped 7.04 out and started with a clean install.

---

### Post by P4man on 2009-08-21
have you tried uninstalling and reinstalling ndiswrapper and your windows driver? BTW, isnt that card supported natively?

---

### Post by p110011 on 2009-08-21
I did download the latest driver and installed it. 

As far as I can tell, the wiki for supported hardware lists my dongle (AirLink101 Model AWLL6070) as needing Ndiswrapper.

I have a feeling this may be a dbus problem, and if so, I have no idea how to fix it.

---

