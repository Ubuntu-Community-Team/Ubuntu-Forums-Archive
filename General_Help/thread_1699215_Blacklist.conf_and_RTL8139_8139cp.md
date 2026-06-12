---
title: "Blacklist.conf and RTL8139 8139cp"
date: 2011-03-03
forum: General Help
---

### Post by kuifje09 on 2011-03-03
Using the rtl8139 card gives some trouble immediate after the boot or a while later.
Removing the 8139cp driver in time, will save a lot trouble / reboot.

I placed the 8139cp driver in the /etc/modprobe.d/blacklist.conf but after the boot driver 8139cp
is loaded. Why?

Even syslog tells not to use 8139cp but 8139too.  so I remove 8139cp by hand.

What is wrong with the ubuntu 10.10 kernel ? it loads the 8139cp while it is not needed.
But also, it should not harm I think, altough it does.

If you leave the 8139cp alone, your network will stop working.

So I placed  "rmmod 8139cp"  in my rc.local. Hopefully it will help at least.

/var/log/syslog:Mar  3 16:05:08 grey kernel: [    2.425382] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
/var/log/syslog:Mar  3 16:05:08 grey kernel: [    2.993065] 8139too: 8139too Fast Ethernet driver 0.9.28

blacklist.conf:
# This driver crashes my RTL8139too.
# only one of both should be active at a time ?
# I need the 8139too
blacklist 8139cp

So here are two questions,
1   why are those 2 drivers coliding .
2  why does the blacklist.conf not work .

Also posible, I dont understand the working of blacklist.conf

---

### Post by kuifje09 on 2011-03-04
Even this did not fix the problem. The driver 8139cp  was unloaded after the boot /  rc.local
but the network stopped working after a few minutes.

So , maybe the heading needs another content.

but,   Driver cannot be unloaded with the blacklist.conf,
         My network even stops working even driver is unloaded.

Any ideas to solve this are welcome.  I never had this problem, until now, running ubuntu 10.10
I install all the updates which are given by ubuntu...

Does this mean anything in relation :

/var/log/jockey.log:2011-03-03 14:40:40,826 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': '8139too', 'jockey_handler': 'KernelModuleHandler'}

/var/log/kern.log:Mar  4 13:51:20 grey kernel: [    2.431593] 8139too 0000:00:08.0: eth0: RealTek RTL8139 at 0xe800, 00:02:44:90:2c:b3, IRQ 19
/var/log/kern.log:Mar  4 13:52:26 grey kernel: [  111.824064] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out

Now I reboot the system and network remains online...
/var/log/syslog:Mar  4 13:55:56 grey kernel: [  322.250002] 8139too 0000:00:08.0: PCI INT A disabled
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649378] 8139too: 8139too Fast Ethernet driver 0.9.28
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649447] 8139too 0000:00:08.0: enabling device (0000 -> 0003)
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649460] 8139too 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649479] 8139too 0000:00:08.0: setting latency timer to 64
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649489] 8139too 0000:00:08.0: Chip not responding, ignoring board
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649505] 8139too 0000:00:08.0: PCI INT A disabled
/var/log/syslog:Mar  4 13:56:11 grey kernel: [  336.649515] 8139too: probe of 0000:00:08.0 failed with error -5
/var/log/syslog:Mar  4 13:57:58 grey kernel: [    2.379350] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
/var/log/syslog:Mar  4 13:57:58 grey kernel: [    2.379385] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
/var/log/syslog:Mar  4 13:57:58 grey kernel: [    2.426201] 8139too: 8139too Fast Ethernet driver 0.9.28
/var/log/syslog:Mar  4 13:57:58 grey kernel: [    2.434875] 8139too 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
/var/log/syslog:Mar  4 13:57:58 grey kernel: [    2.435923] 8139too 0000:00:08.0: eth0: RealTek RTL8139 at 0xe800, 00:02:44:90:2c:b3, IRQ 19
/var/log/syslog:Mar  4 13:57:58 grey NetworkManager[856]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)

---

### Post by kuifje09 on 2011-03-09
Still the network blocks, at boot, but how strange it is, the second boot it usualy starts and keeps up.
Because I get no response to what to do and have no clue myself, I decided to exchange the network card.
This card uses the 3c59x driver and I will see if this one will do better.
The first boot was successfull, and is running now for over 30 min's Looks good.

Second strange behavior, when removing the driver 8139too mii,  and then modprobe them.
The keyboard and mouse ( ps2 ) looses contact. Assert an USB keybaord enables me to type again.
But the network cannot be brought up? no idea why. ( No media or such error message )

This is all hapening with the ubuntu version 10.10. !  that's for shure.

---

