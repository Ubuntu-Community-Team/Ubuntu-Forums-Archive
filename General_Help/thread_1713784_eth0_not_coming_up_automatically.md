---
title: "eth0 not coming up automatically?"
date: 2011-03-24
forum: General Help
---

### Post by Roasted on 2011-03-24
I have a server with two NICs. I tried to bond their network interfaces together, but it bombed out and didn't work, despite the fact I copied the example 100% except for my own numbers for addresses, etc. I decided to go back to a single NIC and let the other unused for now, since I need to get this server running. uh. yesterday.

My network interface file:


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.52.1.35
netmask 255.255.240.0
gateway 10.52.0.1
nameserver 10.52.1.2


When I boot up, often times eth0 isn't listed in ifconfig. I'll see eth1, which is just an unused interface at the moment, but eth0 is no where to be found. If I restart the network service, bam. I'm good.

Why is it not auto coming up?

---

### Post by Cheesehead on 2011-03-24
1) udev rules determine which interface gets which name.
2) /etc/network/interfaces determines how each named interface gets configured. 

Take a look at the udev naming rules.

```
$ ls -l /etc/udev/rules.d/
total 20
-rw-r--r-- 1 root root  613 2011-01-01 11:21 10-vboxdrv.rules
-rw-r--r-- 1 root root   99 2010-07-16 03:16 45-libsane.rules
-rw-r--r-- 1 root root 2266 2010-11-15 19:57 70-persistent-cd.rules
-rw-r--r-- 1 root root  561 2009-10-17 16:33 70-persistent-net.rules    #<-- Aha! That looks promising!
-rw-r--r-- 1 root root 1157 2009-11-03 04:26 README

```

udev will happily assign an interface name based on a mac address you choose. Simply edit the rule.
```
$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x168c:0x001c (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:3a:94:09:b3", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:3a:94:a0:30", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

So now, at every reboot, your interfaces will be named consistently.

---

### Post by Roasted on 2011-03-25
Could this have been caused by my attempted fail at bonding my interfaces? Due to time restraints I just decided I should save it for summer and retrace my steps to get it back to "normal" so I could have a running setup.

---

### Post by Cheesehead on 2011-03-25
If you have two nics, the kernel will load them in the order they get detected - which may be effectively random for you. The next boot may load hardware in a completely different order, and may assign eth0 to a different nic. You have **no** control over which gets loaded first and assigned eth0. That has nothing to do with bonding - that's just how Linux loads hardware.

You **do** have control over whether udev accepts the original assignments, or renames them. (That's what udev is for.)

Your attempt to bond interfaces, or to undo the bonding, might have had some effect...or not. I don't know what you did or which weird online instruction set you followed, or how well you followed those instructions, or why bonding didn't work for you. **Try editing the udev rule(s) first.** If editing the udev rule doesn't work, then we can look more into that as a possible cause.

---

### Post by Roasted on 2011-03-26
Appreciate the response. I ended up commenting the two lines out and rebooting, just to see what happened. Right away when it came back online, eth0 was up. Good sign.

I ended up having to cut out of work earlier than I expected, but the fact eth0 came up was solid. I'll reboot it a few times on Monday and see if it comes up each time.

Oddly, when I booted up and the OS loaded the two additional lines for eth0 and eth1, there didn't seem to be a difference with the commented out lines vs the new lines. At least nothing I took notice of. But I'll check it out Monday and we'll see...

---

