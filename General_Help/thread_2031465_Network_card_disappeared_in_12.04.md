---
title: "Network card disappeared in 12.04"
date: 2012-07-22
forum: General Help
---

### Post by DisappearingOak on 2012-07-22
Hi, I bought a new network card (D-Link 520TX) which says it's compatible with Linux. When I put it in, it worked brilliantly with plug and play and I used it fine for two days, but when I booted up today, the internet is not working. I checked ifconfig -a, and the ethernet card does not show up, only thing that shows up is a loopback. In lspci, the device shows up as:

02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)

but the device has disappeared from ifconfig and netwrok settings. Please help me get back my internet.

---

### Post by sanderj on 2012-07-23
I'm not an expert, so I won't be able to help you much, but here are some tips:

```
lshw -C network
```
will show drivers in use

And on recent Ubuntu:
```
nm-tool
```
will show everything about networks

```
dmesg | grep eth
```
will show things about eth during boot. If boot was too long ago, use
```
grep eth /var/log/syslog
```

Oh, you have tried rebooting, haven't you?



PS: a bit more technical lspci command which is probably NOT needed if you do the above

```
lspci -v | grep -i -e ethernet -e network -A12 | grep -i "Kernel modules" -B12

```

---

### Post by DisappearingOak on 2012-07-23
Hi, I wanted to say the same thing happened with an older card (worked fine before and one day upon boot disappeared from ifconfig -a. I thought it was dead so I bought a new one and now it's happened with this one also). I'm posting the outputs of some relevant commands.

(Note: I'm using a usb adsl modem temporarily which shows up as eth0).
ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:e0:a6:66:41:e1  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:a6ff:fe66:41e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:792281 (792.2 KB)  TX bytes:256507 (256.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84130 (84.1 KB)  TX bytes:84130 (84.1 KB)

```

70-persistent-net.rules
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# USB device 0x0451:0x6060 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:a6:66:41:e1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1106:/sys/devices/pci0000:00/0000:00:14.4/0000:02:06.0 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="cc:b2:55:06:29:f0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

```
lspci -v | grep -i -e ethernet -e network -A12 | grep -i "Kernel modules" -B12
02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
	Subsystem: D-Link System Inc Device 1405
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 20
	I/O ports at de00 [size=256]
	Memory at fdf00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: via-rhine

```

lspci
```
02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)

```

lsmod
```
via_rhine              32192  0 

```

```
dmesg | grep -e via -e eth
[    2.673349] i2c-core: driver [aat2870] using legacy suspend method
[    2.673349] i2c-core: driver [aat2870] using legacy resume method
[    4.089819] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    4.090633] via-rhine 0000:02:06.0: enabling device (0085 -> 0087)
[    4.090651] via-rhine 0000:02:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.090681] via-rhine 0000:02:06.0: MMIO do not match PIO [06] (00 != 80)
[    4.090697] via-rhine: probe of 0000:02:06.0 failed with error -5
[   11.007286] cdc_ether 6-3:2.0: eth0: register 'cdc_ether' at usb-0000:00:13.1-3, CDC Ethernet Device, 00:e0:a6:66:41:e1
[   11.007307] usbcore: registered new interface driver cdc_ether
[   22.376027] eth0: no IPv6 routers present
[  308.670360] cdc_ether 6-3:2.0: eth0: unregister 'cdc_ether' usb-0000:00:13.1-3, CDC Ethernet Device
[  339.075946] cdc_ether 6-3:2.0: eth0: register 'cdc_ether' at usb-0000:00:13.1-3, CDC Ethernet Device, 00:e0:a6:66:41:e1
[  349.680086] eth0: no IPv6 routers present
[  611.351667] cdc_ether 6-3:2.0: eth0: unregister 'cdc_ether' usb-0000:00:13.1-3, CDC Ethernet Device
[  635.780289] cdc_ether 6-3:2.0: eth0: register 'cdc_ether' at usb-0000:00:13.1-3, CDC Ethernet Device, 00:e0:a6:66:41:e1
[  645.960071] eth0: no IPv6 routers present

```

lshw command says that lshw is not installed.

It was suggested on IRC support channel to remove last two lines from persisten rules.net file and reboot but on rebooting, the file did not update anything and ifconfig remained the same. So the card shows up in lspci but not in ifconfig or network manageer. Also could someone tell me what the error message means in above output? Please help!

---

