---
title: "network issue on bootup"
date: 2006-03-26
forum: General Help
---

### Post by shawnzyoo on 2006-03-26
when i boot up my ethernet device isn't working correctly
but when i deactivate it and then reactivate it (through SYSTEM>>ADMINISTRATION>>NETWORKING) it works just fine for everything
web/ftp/ssh/ect
is there a way to make it correctly connect in the first place?
that way i can remotely reboot it
thanks

---

### Post by barfos on 2006-03-26
this may have something to do with /etc/network/interfaces

i think the line

auto eth0

should be in there somewhere.

---

### Post by shawnzyoo on 2006-03-26
this is my file after i deactivated/activated it

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
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1


auto eth0

iface ath0 inet dhcp

---

### Post by Ramses de Norre on 2006-03-26
Is the problem with eth0 or ath0?

---

### Post by mld4165 on 2006-03-26
[QUOTE=Ramses de Norre]Is the problem with eth0 or ath0?[/QUOTE]

Greetings

I have the same issue with ath0, and I hope nobody is offended if I join in this thread.

It worked fine after the original install but after updating the pc it stopped. not sure which update it was as there were many to do. I thought it might be with dhcp but setting ip and dns made no difference.

I also notice that I have long periods of no activity and then all of a sudden it takes off. Not a network issue as this is the only pc with that problem.

output og ifconfig ath0. notice errors on RX
===========================
 Link encap:Ethernet  HWaddr 00:90:96:72:36:6B
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fe72:366b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18286 errors:55806 dropped:0 overruns:0 frame:55806
          TX packets:11361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:14818202 (14.1 MiB)  TX bytes:1775802 (1.6 MiB)
          Interrupt:18 Memory:e0c20000-e0c30000
===========================
mld4165

---

### Post by shawnzyoo on 2006-03-26
my problem is with eth0
i have a wireless ath0 driver which works fine but i don't use it
thanks

---

### Post by shawnzyoo on 2006-03-30
<bump>

---

