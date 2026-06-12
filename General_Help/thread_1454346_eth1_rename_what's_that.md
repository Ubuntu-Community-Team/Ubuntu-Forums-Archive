---
title: "eth1_rename?? what's that?"
date: 2010-04-14
forum: General Help
---

### Post by HotForLinux on 2010-04-14
For the first time, after hibernating, I was unable to use the wifi card. I had to reboot again.

These are the ouputs of common commands after bringing networking down, up and down again:.

```
**$iwconfig **
lo        no wireless extensions.

eth0      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1_rename  no wireless extensions.
[B]
$ ifconfig -a[/B]
eth0      Link encap:Ethernet  HWaddr 00:0e:35:e4:21:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xc000 Memory:b800b000-b800bfff 

eth1_rename Link encap:Ethernet  HWaddr 00:a0:d1:bb:ae:17  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112821 (110.1 KB)  TX bytes:112821 (110.1 KB)
[B]
$ sudo ifup eth1[/B]
eth1: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

I couldn't configure eth1 because according to the system it was inexistent.
What should one do in a case like this one?

I saved dmeg, but I can't figure out if it is helpful

---

### Post by Iowan on 2010-04-14
You can see if that definition shows up in */etc/udev/rules.d/70-persistent-net.rules* If so, you might be able to edit it back...

---

### Post by llamabr on 2010-04-14
after hybernate, i always have to hang back about a minute or so, before the wireless reconnects.

unhibernate, or open the lid, and make yourself a nice cup of tea.  does the situation change?

---

### Post by HotForLinux on 2010-05-25
> **Iowan said:**
> You can see if that definition shows up in */etc/udev/rules.d/70-persistent-net.rules* If so, you might be able to edit it back...

Thanks, but I don't quite understand what you mean. The problem was temporal. After rebooting it disappeared.
Is the first time I hear about the  */etc/udev/rules.d/ * directory.
I've read the contents of that file and I guess that is where the system learns how to call the installed net cards (i.e. eth0, eth1,...).

I don't understand what are the names in parenthesis, how come it seems that  there's a third USB card (?) and why would I want to add my own entries.

**$cat /etc/udev/rules.d/70-persistent-net.rules**
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4351 (sky2)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:a0:d1:bb:[COLOR=DimGray]xx:yy[/COLOR]", ATTR{type}=="1", NAME="eth0"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0e:35:e4:[COLOR=DimGray]xx:yy[/COLOR]", ATTR{type}=="1", NAME="eth1"

# USB device 0x06b9:0x4062 (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:7f:62:[COLOR=DimGray]xx:yy[/COLOR]", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

```

---

### Post by HotForLinux on 2010-05-25
> **llamabr said:**
> after hybernate, i always have to hang back about a minute or so, before the wireless reconnects.

unhibernate, or open the lid, and make yourself a nice cup of tea.  does the situation change?

Thanks. I'll do that the next time. I don't hibernate often but, as I said, I think that was the first time this happened. The bad thing is I didn't have the slightest idea how to fix it without rebooting.

---

