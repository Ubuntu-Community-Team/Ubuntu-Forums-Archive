---
title: "repair wired network connection"
date: 2011-06-04
forum: General Help
---

### Post by dragonfly41 on 2011-06-04
I've had ubuntu 10.10 running very smoothly in dual boot configuration with Vista.

Ubuntu is mounted in two separate partitions "/" and "/home".

I use only wired (cable) connection.

...

I could see several wireless connections (probably from nearby homes) and I thought I might try disabling wireless connections (even though not connected) leaving only my wired connection.

I remember installing connection manager through Synaptic Package Manager .. but I then saw a red icon in the top right of panel .. after rebooting there were no network connections seen (wired or wireless).

I tried adding a new wired connection from network connections but this shows blank in fields "Device MAC Address" and "Cloned MAC Address".

...

I tried the command:-

sudo /etc/init.d/networking restart

but that didn't restore network connections.

So unless there is a quick fix to restore network connections it seems that I must "repair" ubuntu.

...

If I do what is the recommended "repair" process?

Re-install ubuntu from LiveCD by mounting partitions "/" and "home" without formatting either?

Or do I format only the "/" partition but not the "/home" partition?

Or is there an easier option?

I'm posting this from my Vista boot.

---

### Post by wgarcia on 2011-06-04
When you say "connection manager" you mean "network-manager"? When you click on the icon in the upper panel for the network-manager, do you have "Wired" marked? 

To disable wireless connections you just have to unmarked "Wireless" in the network manager indicator menu. 

I don't think it is necessary to reinstall Ubuntu just because of this, but of course it is hard to fix if you don't have any connection at all and you have to move back and forth to another system. 

Some other thing that you can try, from a terminal:

sudo apt-get remove --purge network-manager
sudo apt-get install network-manager

This should remove the network-manager application and all its configuration files and reinstall it, maybe this fixes the missconfiguration that you introduced when you tried to disable the wireless network.

---

### Post by dragonfly41 on 2011-06-04
Thanks for the advice .. but when I came out of Vista and rebooted into ubuntu my network connections were restored .. I don't know what caused the glitch.

The symptoms were no connections shown at all in the panel icon.   There was no "wired" marked or "Auto eth0".

I think this glitch occurred after .. by mistake .. I installed "connman"   ... Intel Connection Manager daemon.

> Intel Connection Manager daemon

The Linux Connection Manager project provides a daemon for managing
Internet connections within embedded devices running the Linux
operating system. The Connection Manager is designed to be slim and to
use as few resources as possible, so it can be easily integrated in
other Moblin-based embedded systems. It is fully modular system that
can be extended through plug-ins, to support all kinds of wired or
wireless technologies. Also, configuration methods like DHCP and
domain name resolving are implemented using plug-ins. The plug-in
approach allows for easy adaption and modification for various use cases.

This package contains the connman daemon and its plugins.


I have now uninstalled this.   I was looking for a daemon to disable wireless connections.

I still don't know how to disable wireless connections.

---

### Post by jonbanjo on 2011-06-21
I've just found this page when trying to fix my own wired network problem and was wondering if anyone has any other ideas how to repair one.

Mine started what seems to have been a hardware problem.  The card did not appear on one boot but re-appeared the next time I started up. 

The settings in Network Manager were correct but I had no network and the LAN settings do not show using ifconfig.  I tried editing settings in the hope it would rewrite something but no joy.  

I tried changing the name of the connection from auto-eth0 to eth0 to match the name shown in ifconfig but the only thing that achieved was Network Manager then showed me with 2 wired connections instead of 1.  I deleted both to try to start from scratch and using the mac that ifconfig gave me, created a new connection but that did not work.

I then tried the apt-get remove/install method suggested above but all that achieved was to force me into getting a working network to re-install as it would not re-install (needed to download) without one.  I achieved this using the ifconfig and route commands and editing /etc/resolv.conf. These changes didn't hold through a reboot though.  

Any ideas how to get Network Manager to work properly, or alternatively, can I remove it completely and set things manually in a way that will hold?

---

### Post by jonbanjo on 2011-06-22
I'm running now.

I've edited /etc/network/interface as per the instructions at

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

I haven't a clue why Network Manager no longer seems to be part of the configuration but that's not a problem to me.

---

