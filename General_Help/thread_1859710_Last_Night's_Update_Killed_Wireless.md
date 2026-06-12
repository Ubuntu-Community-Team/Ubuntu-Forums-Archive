---
title: "Last Night's Update Killed Wireless"
date: 2011-10-14
forum: General Help
---

### Post by demonboy on 2011-10-14
My partner runs 10.10 on a Samsung NC10 and last night ran an update. Since then she has been unable to get online as the wireless card appears to have been disconnected. I've tried Fn+F9, which normally turns the wireless on but to no avail. At the grub screen I've tried running the previous kernel but that doesn't make any difference. I am unable to plug in a wired connection.

I've followed other threads on this subject but can't work out why this is so. Here are some Terminal outputs:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:13:77:d3:c6:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12354 (12.3 KB)  TX bytes:12354 (12.3 KB)

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```lshw -C network
```

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:d3:c6:ba
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 multicast=yes
       resources: irq:42 memory:f0100000-f0103fff ioport:2000(size=256)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```udevadm trigger
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```Any clues or pointers greatly appreciated.

---

### Post by demonboy on 2011-10-14
Thanks all for your replies. 

In the end I drove 2 hours to see my wife, took the computer into an internet cafe and hard-wired it via ethernet cable in order to force an update. This was after spending a morning trying to find a solution online on someone else's laptop, to no avail.

Not ideal, not a workable solution when we move back on to our boat in India (we're visiting relatives in the UK at the moment) and not exactly a selling point to my girlfriend. We still don't know why this happened, what caused it, what the solution was (the update was just a guess) and haven't a clue if this will happen again. 

If someone could explain to me why this happened and how we can avoid it happening again I would be very grateful.

---

