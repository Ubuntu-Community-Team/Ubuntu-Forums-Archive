---
title: "No internet in Kubuntu (Router and DHCP off)"
date: 2006-02-23
forum: General Help
---

### Post by pioSko on 2006-02-23
I have a Linksys router configured for optimum P2P. IP's are given to both of the PC's and Windows is setup and net is working.

On to Kubuntu. I've manually edited /etc/network/interfaces a number of times... currently it looks like this:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# the loopback network interface
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
address 192.168.1.100
netmask 255.255.255.0
gateway 85.128.[xx].[xxx]

auto eth0

... the [xx] are numbers. gateway is the Default Gateway setup in my router.

... and I do have DNS servers in /etc/resolv.conf

I'm positive that I have correct address and netmask entered because if I enter anything else, I can't even connect to the router.

When I do ifconfig i see that all the things configured are shown, except for gateway (not sure if it's supposed to show up). There is also a bcast value shown that is very similar to the gateway in terms of numbers. But i don't know what broadcast is or where to change it... nor to what.

The gui allows me to enter all those values, but there is a bug in kubuntu where it does NOT save the gateway, and when saving new config it overwrites the interfaces file without entering a gateway value... so I have to do it manually. I use the gui to reset the eth0 to check new configs.

Any help will be appreciated.

PS: When I had DCHP in router and Kubuntu turned on, internet worked fine.

---

### Post by jamesr on 2006-02-23
I would expect to see a the router address as the gateway.

Also you said> PS: When I had DCHP in router and Kubuntu turned on, internet worked fine.
 

What did the files show as gateway etc.

---

### Post by pioSko on 2006-02-23
Bingo!

Changed it to 192.168.1.1 (direct to router) and it's working. Writing from Kubuntu.

Of course, in Windows it's set like this aswell... didn't notice :/



Thank you!

---

