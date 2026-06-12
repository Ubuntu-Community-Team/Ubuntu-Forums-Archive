---
title: "Marvell yukon gigabit ethernet strike again !"
date: 2012-10-04
forum: General Help
---

### Post by LaBanane on 2012-10-04
Hello everyone !

I have a problem with my PCI-E NIC Marvell yukon. I read a lot of stuff about this and try many things !

I managed to upgrade my Ubuntu server 10.04 to 12.04 and apply the solution of Foresto [here]("http://ubuntuforums.org/showthread.php?t=1330283&page=3") post #25. I now use sk98lin driver instead of  sky2.
(Thanks you Foresto by the way ;) )

But I still lost my PCI-E Ethernet card ! Yeah this is very weird. Sometime my eth0 disappear :-k ... 

Running on my server I have a script which pings every 3 minutes a monitoring server. When the issue comes my server can't ping my monitoring anymore, but when I try to connect with ssh I managed to connect to my server. Then I can't see my PCI-E Ethernet card (not in lspci, not in lshw).
When I'm reboot my server, the eth0 "wake up" again and work for some time.

I was thinking it's a driver issue but obviously it's more ? Sk89lin doesn't work better than sky2 at first look.

LAST NEWS: I can't see my yukon 88e8053 anymore, even after a reboot. I really don't know what to do :frown:

Seems I have the same problem describe [here]("http://ubuntuforums.org/showthread.php?t=1954229").

If someone has any idea ?


*sorry for the bad English this is not my main language.

Here some information:

# lsb_release -a
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```

# ifconfig
```

eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:43ff:fe01:184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353873 (353.8 KB)  TX bytes:23268 (23.2 KB)
          Interrupt:52 Memory:fe620000-0 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:10.98.1.2  Bcast:10.98.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de9c:52ff:fe07:cbf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:320766 (320.7 KB)  TX bytes:2456729 (2.4 MB)
          Interrupt:51 Memory:fe420000-0 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:336 (336.0 B)  TX bytes:336 (336.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.16.99.1  P-t-P:172.16.99.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING  MTU:1500  Metric:1
          RX packets:2212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:127499 (127.4 KB)  TX bytes:0 (0.0 B)

```
My tun0 interface is generate by chillispot.

# lspci
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
**01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)**
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
**04:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)**

```

# lshw -c network
```

  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 20
       serial: XX:XX:XX:XX:XX:XX
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sk98lin driverversion=10.92.1.3 (01) duplex=full firmware=N/A ip=192.168.2.1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:52 memory:fe620000-fe623fff ioport:e000(size=256) memory:fe600000-fe61ffff
  *-network
       description: Ethernet interface
       product: Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 11
       serial: XX:XX:XX:XX:XX:XX
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sk98lin driverversion=10.92.1.3 (01) duplex=full firmware=N/A ip=10.98.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:51 memory:fe420000-fe423fff ioport:d000(size=256) memory:fe400000-fe41ffff

```

# lsmod | grep sk
```

sk98lin               171780  2 

```

# modprobe -l | grep sk
```

kernel/crypto/algif_skcipher.ko
kernel/drivers/net/ethernet/marvell/skge.ko
kernel/drivers/net/ethernet/marvell/sky2.ko
kernel/drivers/net/fddi/skfp/skfp.ko
kernel/drivers/net/tokenring/skisa.ko
kernel/drivers/media/dvb/dvb-usb/dvb-usb-gp8psk.ko
kernel/drivers/staging/comedi/drivers/skel.ko
kernel/drivers/mtd/nand/diskonchip.ko
kernel/net/sched/act_skbedit.ko
updates/dkms/sk98lin.ko

```

# cat /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp

```

# cat /etc/modprobe.d/blacklist.conf 
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by LaBanane on 2012-10-04
Up, i really need help.

---

### Post by Mark Phelps on 2012-10-04
> **LaBanane said:**
> Up, i really need help.

We all understand that ... but you're bumping every two hours -- and courtesy around here is to bump no more often than  every 24 hours -- so back off on the bumping.

---

### Post by LaBanane on 2012-10-05
> **Mark Phelps said:**
> We all understand that ... but you're bumping every two hours -- and courtesy around here is to bump no more often than  every 24 hours -- so back off on the bumping.

Sorry I was not aware about that I'll be more careful and try to not flood.

I still need help by the way, i really don't understand what could make my eth0 disapear.

I bought the server about 5 months ago so the hardware is really recent.
The solution runs for 3 months without incident and start to crash about 1 month ago. I don't make any update.
I start to think to a hardware failure but it's still strange.

LaBanane

---

### Post by cbraxton on 2012-10-05
For a server you are really better of sticking with Intel NICs whenever possible. Even a workstation-grade Intel network card is going to work better than Broadcomm in a small server.

---

### Post by LaBanane on 2012-10-09
Hi everyone !

Thanks you cbraxton for the reply =)

Here's my last news:
I managed to take my faulty server on my desk to test it (3 hours of road). After several hours I notice :

  -When I do a cold boot (I mean "shutdown -h now" the server and next power on) my server loses the faulty NIC.

  -When I do a warm boot (I mean "reboot") my server detects the card ... some time :-k
I don't understand why ...


I take some time to see BIOS configuration too, I have to enable "PEG Force gen1" and "Detect Non-Compliance Device" in "North Bridge" part or my NIC is not detected properly.
I do some research but if someone can tell me more about those options ?

I buy another NIC with VIA controller, waiting for delivery !

Feel free to ask me for some question or log.

Regards,

LaBanane.

---

### Post by LaBanane on 2012-10-10
Hello there !

I don't have the feeling my topic is reading a lot but I'll continue to feed it with my last news.

Ok ! So I found a nice command "last reboot" and notice my server reboot a lot.

_Last reboot_ (just for today):
```

reboot   system boot  3.2.0-31-generic Wed Oct 10 08:58 - 09:03  (00:05)    
reboot   system boot  3.2.0-31-generic Wed Oct 10 05:19 - 08:58  (03:38)    
reboot   system boot  3.2.0-31-generic Wed Oct 10 04:29 - 08:58  (04:28)    
reboot   system boot  3.2.0-31-generic Wed Oct 10 02:06 - 08:58  (06:51)

```

Then I search in the log and found this :

_Syslog:_

02:06
```
Oct  9 16:33:45 ilitoo-montelimar dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct  9 16:33:45 ilitoo-montelimar dhclient: DHCPREQUEST of 10.0.0.110 on eth0 to 255.255.255.255 port 67
Oct  9 16:33:45 ilitoo-montelimar dhclient: DHCPOFFER of 10.0.0.110 from 10.0.0.1
Oct  9 16:33:45 ilitoo-montelimar dhclient: DHCPACK of 10.0.0.110 from 10.0.0.1
Oct  9 16:33:46 ilitoo-montelimar dhclient: bound to 10.0.0.110 -- renewal in 37923 seconds.
Oct  9 16:33:54 ilitoo-montelimar kernel: [  145.781201] eth0: no IPv6 routers present
Oct  9 16:33:54 ilitoo-montelimar ntpdate[1395]: adjust time server 91.189.94.4 offset 0.242955 sec
Oct  9 16:34:57 ilitoo-montelimar kernel: [  209.103296] init: tty1 main process ended, respawning
Oct  9 16:35:05 ilitoo-montelimar kernel: [  216.865609] usb 2-1.3: USB disconnect, device number 3
Oct  9 17:17:01 ilitoo-montelimar CRON[2501]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  9 18:17:01 ilitoo-montelimar CRON[4190]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  9 19:17:01 ilitoo-montelimar CRON[5642]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  9 20:17:01 ilitoo-montelimar CRON[7094]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  9 21:17:01 ilitoo-montelimar CRON[8609]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  9 22:17:01 ilitoo-montelimar CRON[10061]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  9 23:17:01 ilitoo-montelimar CRON[11513]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 00:17:01 ilitoo-montelimar CRON[12965]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 01:17:01 ilitoo-montelimar CRON[14417]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 02:06:41 ilitoo-montelimar kernel: imklog 5.8.6, log source = /proc/kmsg started.
Oct 10 02:06:41 ilitoo-montelimar rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="804" x-info="http://www.rsys$
Oct 10 02:06:41 ilitoo-montelimar rsyslogd: rsyslogd's groupid changed to 103
Oct 10 02:06:41 ilitoo-montelimar rsyslogd: rsyslogd's userid changed to 101
Oct 10 02:06:41 ilitoo-montelimar rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/203$
Oct 10 02:06:41 ilitoo-montelimar kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 10 02:06:41 ilitoo-montelimar kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 10 02:06:41 ilitoo-montelimar kernel: [    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4$
Oct 10 02:06:41 ilitoo-montelimar kernel: [    0.000000] KERNEL supported cpus:
Oct 10 02:06:41 ilitoo-montelimar kernel: [    0.000000]   Intel GenuineIntel

```

We can see here that the server doesn't have any activity, the cron. hourly past every hour and everything is normal ! And then PAM reboot :confused:

04:29
```

Oct 10 02:06:41 ilitoo-montelimar kernel: [   20.328248] type=1400 audit(1349827601.728:8): apparmor="STATUS" operation="prof$
Oct 10 02:06:41 ilitoo-montelimar acpid: starting up with proc fs
Oct 10 02:06:41 ilitoo-montelimar acpid: 1 rule loaded
Oct 10 02:06:41 ilitoo-montelimar acpid: waiting for events: event logging is off
Oct 10 02:06:41 ilitoo-montelimar cron[910]: (CRON) INFO (pidfile fd = 3)
Oct 10 02:06:41 ilitoo-montelimar cron[941]: (CRON) STARTUP (fork ok)
Oct 10 02:06:41 ilitoo-montelimar cron[941]: (CRON) INFO (Running @reboot jobs)
Oct 10 02:06:42 ilitoo-montelimar kernel: [   20.856198] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 10 02:06:42 ilitoo-montelimar kernel: [   20.861197] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 10 02:06:42 ilitoo-montelimar chillispot[1051]: chilli.c: 373: Could not resolve IP address of uamserver: http://proxy.il$
Oct 10 02:17:01 ilitoo-montelimar CRON[1176]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 03:17:01 ilitoo-montelimar CRON[1635]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 04:17:01 ilitoo-montelimar CRON[2094]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 04:29:20 ilitoo-montelimar kernel: imklog 5.8.6, log source = /proc/kmsg started.
Oct 10 04:29:20 ilitoo-montelimar rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="778" x-info="http://www.rsys$
Oct 10 04:29:20 ilitoo-montelimar rsyslogd: rsyslogd's groupid changed to 103
Oct 10 04:29:20 ilitoo-montelimar rsyslogd: rsyslogd's userid changed to 101
Oct 10 04:29:20 ilitoo-montelimar rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/203$
Oct 10 04:29:20 ilitoo-montelimar acpid: starting up with proc fs
Oct 10 04:29:20 ilitoo-montelimar acpid: 1 rule loaded
Oct 10 04:29:20 ilitoo-montelimar acpid: waiting for events: event logging is off
Oct 10 04:29:20 ilitoo-montelimar cron[863]: (CRON) INFO (pidfile fd = 3)
Oct 10 04:29:20 ilitoo-montelimar cron[919]: (CRON) STARTUP (fork ok)
Oct 10 04:29:20 ilitoo-montelimar cron[919]: (CRON) INFO (Running @reboot jobs)
Oct 10 04:29:20 ilitoo-montelimar kernel: [    0.000000] Initializing cgroup subsys cpuset

```

I put the last line of the boot "kernel: [ 20.861197]" and the first line of the next reboot. The error of the chillispot put has part nothing goes wrong but still reboot. :(

05:19 (I put the entire boot log kernel this time)
```

Oct 10 04:29:21 ilitoo-montelimar kernel: [   10.921371] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 10 04:29:21 ilitoo-montelimar chillispot[1027]: chilli.c: 373: Could not resolve IP address of uamserver: http://proxy.il$
Oct 10 05:17:01 ilitoo-montelimar CRON[1437]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 05:19:21 ilitoo-montelimar kernel: imklog 5.8.6, log source = /proc/kmsg started.
Oct 10 05:19:21 ilitoo-montelimar rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="800" x-info="http://www.rsys$
Oct 10 05:19:21 ilitoo-montelimar rsyslogd: rsyslogd's groupid changed to 103
Oct 10 05:19:21 ilitoo-montelimar rsyslogd: rsyslogd's userid changed to 101
Oct 10 05:19:21 ilitoo-montelimar rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/203$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Linux version 3.2.0-31-generic-pae (buildd@roseapple) (gcc version 4$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] KERNEL supported cpus:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Intel GenuineIntel
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   AMD AuthenticAMD
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   NSC Geode by NSC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Cyrix CyrixInstead
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Centaur CentaurHauls
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Transmeta GenuineTMx86
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Transmeta TransmetaCPU
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   UMC UMC UMC UMC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000040200000 - 000000006e47d000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e47d000 - 000000006e4c4000 (ACPI NVS)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e4c4000 - 000000006e4cb000 (ACPI data)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e4cb000 - 000000006e604000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e604000 - 000000006e606000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e606000 - 000000006e616000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e616000 - 000000006e620000 (ACPI NVS)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e620000 - 000000006e645000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e645000 - 000000006e688000 (ACPI NVS)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006e688000 - 000000006e800000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 000000006f000000 - 000000007f200000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000100600000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000100600000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] DMI 2.7 present.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] DMI:    /Pure Platinum H67, BIOS 4.6.4 06/28/2011
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> $
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] last_pfn = 0x100600 max_arch_pfn = 0x1000000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] MTRR default type: uncachable
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   00000-9FFFF write-back
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   D0000-E7FFF uncachable
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   E8000-FFFFF write-protect
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] MTRR variable ranges enabled:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   1 base 100000000 mask FFFC00000 write-back
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   2 base 100400000 mask FFFE00000 write-back
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   3 base 06F000000 mask FFF000000 uncachable
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   4 base 070000000 mask FF0000000 uncachable
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   5 base 080000000 mask F80000000 uncachable
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   6 disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   7 disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   8 disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   9 disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] original variable MTRRs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 1, base: 4GB, range: 4MB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 2, base: 4100MB, range: 2MB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 3, base: 1776MB, range: 16MB, type UC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 4, base: 1792MB, range: 256MB, type UC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 5, base: 2GB, range: 2GB, type UC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] total RAM covered: 1782M
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Found optimal setting for mtrr clean up
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  gran_size: 64K        chunk_size: 512M        num_reg: 5      lose $
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] New variable MTRRs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] New variable MTRRs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 1, base: 1776MB, range: 16MB, type UC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 2, base: 1792MB, range: 256MB, type UC
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 3, base: 4GB, range: 4MB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] reg 4, base: 4100MB, range: 2MB, type WB
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] e820 update range: 000000006f000000 - 0000000100000000 (usable) ==> $
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] found SMP MP-table at [c00fcda0] fcda0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] initial memory mapped : 0 - 02000000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] RAMDISK: 35fca000 - 36fdd000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: RSDP 000f0450 00024 (v02 ALASKA)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: XSDT 6e4c4070 0005C (v01 ALASKA    A M I 01072009 AMI  0001001$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: FACP 6e4c9dd0 000F4 (v04 ALASKA    A M I 01072009 AMI  0001001$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: DSDT 6e4c4158 05C77 (v02 ALASKA    A M I 00000081 INTL 2005111$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: FACS 6e617f80 00040
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: APIC 6e4c9ec8 00062 (v03 ALASKA    A M I 01072009 AMI  0001001$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: SSDT 6e4c9f30 00098 (v01 AMICPU     PROC 00000001 MSFT 0300000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: MCFG 6e4c9fc8 0003C (v01 ALASKA    A M I 01072009 MSFT 0000009$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: WDTT 6e4ca008 00584 (v02 ALASKA    A M I 01072009 AMI  0000000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: HPET 6e4ca590 00038 (v01 ALASKA    A M I 01072009 AMI. 0000000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: ASPT 6e4ca5c8 00034 (v07 ALASKA PerfTune 01072009 AMI  0000000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] 3210MB HIGHMEM available.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] 891MB LOWMEM available.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   low ram: 0 - 37bfe000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Zone PFN ranges:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   HighMem  0x00037bfe -> 0x00100600
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Movable zone start PFN for each node
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] early_node_map[7] active PFN ranges
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Movable zone start PFN for each node
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] early_node_map[7] active PFN ranges
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x00020200 -> 0x00040000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x00040200 -> 0x0006e47d
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x0006e604 -> 0x0006e606
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x0006e688 -> 0x0006e800
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     0: 0x00100000 -> 0x00100600
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] On node 0 totalpages: 452484
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] free_area_init_node: node 0, pgdat c1868a80, node_mem_map f3fba200
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   DMA zone: 3949 pages, LIFO batch:0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   Normal zone: 221990 pages, LIFO batch:31
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   HighMem zone: 6421 pages used for memmap
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]   HighMem zone: 218340 pages, LIFO batch:31
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Using APIC driver default
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] nr_irqs_gsi: 40
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Allocating PCI resources starting at 7f200000 (gap: 7f200000:7fb1c00$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages:$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-31-generic-pae r$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Initializing CPU#0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] allocated 16801536 bytes of page_cgroup
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory c$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:00100600)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Memory: 1732872k/4200448k available (5818k kernel code, 77064k reser$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] virtual kernel memory layout:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]       .init : 0xc1877000 - 0xc1930000   ( 740 kB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]       .data : 0xc15ae8bc - 0xc1876280   (2846 kB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]       .text : 0xc1000000 - 0xc15ae8bc   (5818 kB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mod$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Node$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Hierarchical RCU implementation.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000]        RCU dyntick-idle grace-period acceleration is enabled.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Extended CMOS year: 2000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Console: colour dummy device 80x25
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] console [tty0] enabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Console: colour dummy device 80x25
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] console [tty0] enabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] hpet clockevent registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000000] Fast TSC calibration using PIT
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.004000] Detected 2494.423 MHz processor.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000001] Calibrating delay loop (skipped), value calculated using timer frequ$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000020] Security Framework initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000033] AppArmor: AppArmor initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000034] Yama: becoming mindful.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000073] Mount-cache hash table entries: 512
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000161] Initializing cgroup subsys cpuacct
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000165] Initializing cgroup subsys memory
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000171] Initializing cgroup subsys devices
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000172] Initializing cgroup subsys freezer
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000174] Initializing cgroup subsys blkio
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000179] Initializing cgroup subsys perf_event
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000200] CPU: Physical Processor ID: 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000201] CPU: Processor Core ID: 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000206] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000207] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000210] mce: CPU supports 7 MCE banks
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000220] CPU0: Thermal monitoring enabled (TM1)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.000227] using mwait in idle threads.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.002327] ACPI: Core revision 20110623
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.239288] ftrace: allocating 26555 entries in 52 pages
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.248397] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.248931] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.288565] CPU0: Intel(R) Celeron(R) CPU G540 @ 2.50GHz stepping 07
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393682] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393687] PEBS disabled due to CPU errata.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393690] ... version:                3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393691] ... bit width:              48
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393692] ... generic registers:      8
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393693] ... value mask:             0000ffffffffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393694] ... max period:             000000007fffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393696] ... fixed-purpose events:   3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393697] ... event mask:             00000007000000ff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393696] ... fixed-purpose events:   3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393697] ... event mask:             00000007000000ff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393795] NMI watchdog enabled, takes one hw-pmu counter.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393862] CPU 1 irqstacks, hard=f74ea000 soft=f74ec000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393864] Booting Node   0, Processors  #1 Ok.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.393866] smpboot cpu 1: start_ip = 99000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.404027] Initializing CPU#1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.501633] NMI watchdog enabled, takes one hw-pmu counter.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.501662] Brought up 2 CPUs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.501664] Total of 2 processors activated (9977.48 BogoMIPS).
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503087] devtmpfs: initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503187] EVM: security.selinux
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503188] EVM: security.SMACK64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503189] EVM: security.capability
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503210] PM: Registering ACPI NVS region at 6e47d000 (290816 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503217] PM: Registering ACPI NVS region at 6e616000 (40960 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.503220] PM: Registering ACPI NVS region at 6e645000 (274432 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504012] print_constraints: dummy:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504059] RTC time:  3:19:12, date: 10/10/12
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504089] NET: Registered protocol family 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504148] Trying to unpack rootfs image as initramfs...
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504176] EISA bus registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504189] ACPI: bus type pci registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504250] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xeffff$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.504252] PCI: not using MMCONFIG
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.518721] PCI: Using configuration type 1 for base access
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.520090] bio: create slab <bio-0> at 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.520349] ACPI: Added _OSI(Module Device)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.520350] ACPI: Added _OSI(Processor Device)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.520352] ACPI: Added _OSI(3.0 _SCP Extensions)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.520354] ACPI: Added _OSI(Processor Aggregator Device)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.521267] ACPI: EC: Look up EC in DSDT
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.522196] ACPI: Executed 1 blocks of module-level executable AML code
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524403] ACPI: SSDT 6e618e18 001D8 (v01    AMI      IST 00000001 MSFT 0300000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524637] ACPI: Dynamic OEM Table Load:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524639] ACPI: SSDT   (null) 001D8 (v01    AMI      IST 00000001 MSFT 0300000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524663] ACPI: SSDT 6e61ed98 00054 (v01    AMI      CST 00000001 MSFT 0300000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524868] ACPI: Dynamic OEM Table Load:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524663] ACPI: SSDT 6e61ed98 00054 (v01    AMI      CST 00000001 MSFT 0300000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524868] ACPI: Dynamic OEM Table Load:
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.524870] ACPI: SSDT   (null) 00054 (v01    AMI      CST 00000001 MSFT 0300000$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525103] ACPI: Interpreter enabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525107] ACPI: (supports S0 S5)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525117] ACPI: Using IOAPIC for interrupt routing
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525138] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xeffff$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525194] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI mother$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525195] PCI: Using MMCONFIG for extended config space
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.525364] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.529796] ACPI: No dock devices found.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.529798] HEST: Table not found.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.529801] PCI: Using host bridge windows from ACPI; if necessary, use "pci=noc$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530005] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530210] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530213] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530214] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530216] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530218] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530220] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530222] pci_root PNP0A08:00: host bridge window [mem 0x7f200000-0xffffffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530234] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530273] pci 0000:00:02.0: [8086:0102] type 0 class 0x000300
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530283] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530290] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530294] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530369] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530404] pci 0000:00:16.0: reg 10: [mem 0xfe608000-0xfe60800f 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530520] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530525] pci 0000:00:16.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530575] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530606] pci 0000:00:1a.0: reg 10: [mem 0xfe607000-0xfe6073ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530746] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530751] pci 0000:00:1a.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530789] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530815] pci 0000:00:1b.0: reg 10: [mem 0xfe600000-0xfe603fff 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530939] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530944] pci 0000:00:1b.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530939] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530944] pci 0000:00:1b.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.530980] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531116] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531122] pci 0000:00:1c.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531163] pci 0000:00:1c.4: [8086:1c18] type 1 class 0x000604
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531294] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531299] pci 0000:00:1c.4: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531334] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531466] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531471] pci 0000:00:1c.5: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531514] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531546] pci 0000:00:1d.0: reg 10: [mem 0xfe606000-0xfe6063ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531686] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531691] pci 0000:00:1d.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531724] pci 0000:00:1f.0: [8086:1c4a] type 0 class 0x000601
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531929] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531964] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531977] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.531991] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532005] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532018] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532032] pci 0000:00:1f.2: reg 24: [mem 0xfe605000-0xfe6057ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532121] pci 0000:00:1f.2: PME# supported from D3hot
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532125] pci 0000:00:1f.2: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532152] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532178] pci 0000:00:1f.3: reg 10: [mem 0xfe604000-0xfe6040ff 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532216] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532335] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532462] pci 0000:02:00.0: [1b21:1042] type 0 class 0x000c03
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532506] pci 0000:02:00.0: reg 10: [mem 0xfe500000-0xfe507fff 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532735] pci 0000:02:00.0: PME# supported from D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.532742] pci 0000:02:00.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537607] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537616] pci 0000:00:1c.4:   bridge window [mem 0xfe500000-0xfe5fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537733] pci 0000:03:00.0: [11ab:4381] type 0 class 0x000200
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537776] pci 0000:03:00.0: reg 10: [mem 0xfe420000-0xfe423fff 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537798] pci 0000:03:00.0: reg 18: [io  0xe000-0xe0ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537776] pci 0000:03:00.0: reg 10: [mem 0xfe420000-0xfe423fff 64bit]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537798] pci 0000:03:00.0: reg 18: [io  0xe000-0xe0ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537881] pci 0000:03:00.0: reg 30: [mem 0xfe400000-0xfe41ffff pref]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537988] pci 0000:03:00.0: supports D1 D2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537989] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.537996] pci 0000:03:00.0: PME# disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545600] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545607] pci 0000:00:1c.5:   bridge window [io  0xe000-0xefff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545612] pci 0000:00:1c.5:   bridge window [mem 0xfe400000-0xfe4fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545647] pci_bus 0000:00: on NUMA node 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545773] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545828] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.545932]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.546046]  pci0000:00: ACPI _OSC control (0x1d) granted
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548670] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548711] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548750] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548788] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548826] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548863] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548901] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.548943] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549042] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,lo$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549048] vgaarb: loaded
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549049] vgaarb: bridge control possible 0000:00:02.0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549136] i2c-core: driver [aat2870] using legacy suspend method
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549138] i2c-core: driver [aat2870] using legacy resume method
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549202] SCSI subsystem initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549245] libata version 3.00 loaded.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549280] usbcore: registered new interface driver usbfs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549289] usbcore: registered new interface driver hub
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549308] usbcore: registered new device driver usb
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.549372] PCI: Using ACPI for IRQ routing
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562560] PCI: pci_cache_line_size set to 64 bytes
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562636] reserve RAM buffer: 000000000009d800 - 000000000009ffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562638] reserve RAM buffer: 000000006e47d000 - 000000006fffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562636] reserve RAM buffer: 000000000009d800 - 000000000009ffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562638] reserve RAM buffer: 000000006e47d000 - 000000006fffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562642] reserve RAM buffer: 000000006e606000 - 000000006fffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562645] reserve RAM buffer: 000000006e800000 - 000000006fffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562647] reserve RAM buffer: 0000000100600000 - 0000000103ffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562748] NetLabel: Initializing
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562749] NetLabel:  domain hash size = 128
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562750] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562760] NetLabel:  unlabeled traffic allowed by default
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562815] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.562820] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.564834] Switching to clocksource hpet
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571043] AppArmor: AppArmor Filesystem Enabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571066] pnp: PnP ACPI init
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571083] ACPI: bus type pnp registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571219] pnp 00:00: [bus 00-ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571221] pnp 00:00: [io  0x0cf8-0x0cff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571223] pnp 00:00: [io  0x0000-0x03af window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571225] pnp 00:00: [io  0x03e0-0x0cf7 window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571226] pnp 00:00: [io  0x03b0-0x03df window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571228] pnp 00:00: [io  0x0d00-0xffff window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571230] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571232] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571234] pnp 00:00: [mem 0x7f200000-0xffffffff window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571235] pnp 00:00: [mem 0x00000000 window]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571283] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571332] pnp 00:01: [mem 0xfed10000-0xfed19fff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571334] pnp 00:01: [mem 0xe0000000-0xefffffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571336] pnp 00:01: [mem 0xfed90000-0xfed93fff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571337] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571339] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571375] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571377] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571379] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571381] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571383] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571386] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571451] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571386] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571451] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571453] pnp 00:02: [io  0x0295-0x0296]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571454] pnp 00:02: [io  0x0a00-0x0a01]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571481] system 00:02: [io  0x0295-0x0296] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571483] system 00:02: [io  0x0a00-0x0a01] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571486] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571504] pnp 00:03: [io  0x0060]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571506] pnp 00:03: [io  0x0064]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571516] pnp 00:03: [irq 1]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571539] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571568] pnp 00:04: [irq 12]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571590] pnp 00:04: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571610] pnp 00:05: [dma 4]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571611] pnp 00:05: [io  0x0000-0x000f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571613] pnp 00:05: [io  0x0081-0x0083]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571614] pnp 00:05: [io  0x0087]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571616] pnp 00:05: [io  0x0089-0x008b]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571617] pnp 00:05: [io  0x008f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571619] pnp 00:05: [io  0x00c0-0x00df]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571637] pnp 00:05: Plug and Play ACPI device, IDs PNP0200 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571645] pnp 00:06: [io  0x0070-0x0071]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571651] pnp 00:06: [irq 8]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571669] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571675] pnp 00:07: [io  0x0061]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571694] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571711] pnp 00:08: [io  0x0010-0x001f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571712] pnp 00:08: [io  0x0022-0x003f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571714] pnp 00:08: [io  0x0044-0x005f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571715] pnp 00:08: [io  0x0062-0x0063]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571717] pnp 00:08: [io  0x0065-0x006f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571718] pnp 00:08: [io  0x0072-0x007f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571720] pnp 00:08: [io  0x0080]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571721] pnp 00:08: [io  0x0084-0x0086]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571722] pnp 00:08: [io  0x0088]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571724] pnp 00:08: [io  0x008c-0x008e]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571725] pnp 00:08: [io  0x0090-0x009f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571727] pnp 00:08: [io  0x00a2-0x00bf]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571725] pnp 00:08: [io  0x0090-0x009f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571727] pnp 00:08: [io  0x00a2-0x00bf]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571728] pnp 00:08: [io  0x00e0-0x00ef]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571730] pnp 00:08: [io  0x04d0-0x04d1]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571760] system 00:08: [io  0x04d0-0x04d1] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571763] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571769] pnp 00:09: [io  0x00f0-0x00ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571775] pnp 00:09: [irq 13]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571793] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571930] pnp 00:0a: [io  0x0400-0x0453]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571932] pnp 00:0a: [io  0x0458-0x047f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571934] pnp 00:0a: [io  0x1180-0x119f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571935] pnp 00:0a: [io  0x0500-0x057f]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571937] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571939] pnp 00:0a: [mem 0xfec00000-0xfecfffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571941] pnp 00:0a: [mem 0xfed08000-0xfed08fff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571943] pnp 00:0a: [mem 0xff000000-0xffffffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571973] system 00:0a: [io  0x0400-0x0453] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571975] system 00:0a: [io  0x0458-0x047f] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571977] system 00:0a: [io  0x1180-0x119f] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571979] system 00:0a: [io  0x0500-0x057f] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571981] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571983] system 00:0a: [mem 0xfec00000-0xfecfffff] could not be reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571985] system 00:0a: [mem 0xfed08000-0xfed08fff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571988] system 00:0a: [mem 0xff000000-0xffffffff] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.571990] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572019] pnp 00:0b: [io  0x0454-0x0457]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572047] system 00:0b: [io  0x0454-0x0457] has been reserved
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572050] system 00:0b: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572142] pnp 00:0c: [mem 0xfed00000-0xfed003ff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572173] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572287] pnp: PnP ACPI: found 13 devices
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572289] ACPI: ACPI bus type pnp unregistered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.572292] PnPBIOS: Disabled by ACPI PNP
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608030] PCI: max bus depth: 1 pci_try_num: 2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608073] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608091] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608099] pci 0000:00:1c.4:   bridge window [mem 0xfe500000-0xfe5fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608091] pci 0000:00:1c.4: PCI bridge to [bus 02-02]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608099] pci 0000:00:1c.4:   bridge window [mem 0xfe500000-0xfe5fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608111] pci 0000:00:1c.5: PCI bridge to [bus 03-03]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608114] pci 0000:00:1c.5:   bridge window [io  0xe000-0xefff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608121] pci 0000:00:1c.5:   bridge window [mem 0xfe400000-0xfe4fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608151] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608158] pci 0000:00:1c.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608166] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608171] pci 0000:00:1c.4: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608181] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608186] pci 0000:00:1c.5: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608191] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608192] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608194] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608196] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608197] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608199] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608201] pci_bus 0000:00: resource 10 [mem 0x7f200000-0xffffffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608203] pci_bus 0000:02: resource 1 [mem 0xfe500000-0xfe5fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608205] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608207] pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608236] NET: Registered protocol family 2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608283] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608409] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608612] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608704] TCP: Hash tables configured (established 131072 bind 65536)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608706] TCP reno registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608708] UDP hash table entries: 512 (order: 2, 16384 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608712] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.608767] NET: Registered protocol family 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609261] pci 0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609502] pci 0000:00:02.0: Boot video device
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609516] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609535] pci 0000:00:1a.0: PCI INT A disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609560] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609577] pci 0000:00:1d.0: PCI INT A disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609597] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609630] pci 0000:02:00.0: PCI INT A disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609597] pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609630] pci 0000:02:00.0: PCI INT A disabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609639] PCI: CLS 64 bytes, default 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609946] audit: initializing netlink socket (disabled)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.609953] type=2000 audit(1349839151.248:1): initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.629387] highmem bounce pool size: 64 pages
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.629391] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631100] VFS: Disk quotas dquot_6.5.2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631145] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631540] fuse init (API version 7.17)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631607] msgmni has been set to 1628
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631825] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631843] io scheduler noop registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631845] io scheduler deadline registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631850] io scheduler cfq registered (default)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.631940] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632010] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632111] pcieport 0000:00:1c.4: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632174] pcieport 0000:00:1c.4: irq 41 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632271] pcieport 0000:00:1c.5: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632333] pcieport 0000:00:1c.5: irq 42 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632448] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632455] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632476] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632478] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632483] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632504] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632505] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632510] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632523] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632542] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632602] intel_idle: MWAIT substates: 0x1120
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632604] intel_idle: v0.4 model 0x2A
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632605] intel_idle: lapic_timer_reliable_states 0xffffffff
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632681] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/inp$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632686] ACPI: Power Button [PWRB]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632721] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632724] ACPI: Power Button [PWRF]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632721] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.632724] ACPI: Power Button [PWRF]
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.633912] ERST: Table is not found!
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.633914] GHES: HEST is not enabled!
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.633983] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.634148] isapnp: Scanning for PnP cards...
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.810343] Freeing initrd memory: 16460k freed
Oct 10 05:19:21 ilitoo-montelimar kernel: [    0.987864] isapnp: No Plug & Play device found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.028792] Linux agpgart interface v0.103
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.028864] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.028927] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 26214$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.029448] agpgart-intel 0000:00:00.0: detected 262144K stolen memory
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.029553] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.030751] brd: module loaded
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031368] loop: module loaded
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031471] ahci 0000:00:1f.2: version 3.0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031489] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031539] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031601] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl S$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031604] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part em$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.031609] ahci 0000:00:1f.2: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.036816] scsi0 : ahci
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.036895] scsi1 : ahci
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.036961] scsi2 : ahci
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037024] scsi3 : ahci
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037088] scsi4 : ahci
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037149] scsi5 : ahci
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037276] ata1: SATA max UDMA/133 abar m2048@0xfe605000 port 0xfe605100 irq 43
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037279] ata2: SATA max UDMA/133 abar m2048@0xfe605000 port 0xfe605180 irq 43
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037281] ata3: DUMMY
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037282] ata4: DUMMY
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037283] ata5: DUMMY
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037284] ata6: DUMMY
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037606] Fixed MDIO Bus: probed
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037621] tun: Universal TUN/TAP device driver, 1.6
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037623] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037670] PPP generic driver version 2.4.2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037756] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037670] PPP generic driver version 2.4.2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037756] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037770] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037784] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037787] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037825] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.037852] ehci_hcd 0000:00:1a.0: debug port 2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.041733] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.041748] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe607000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056377] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056490] hub 1-0:1.0: USB hub found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056493] hub 1-0:1.0: 2 ports detected
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056541] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056554] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056557] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056595] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.056618] ehci_hcd 0000:00:1d.0: debug port 2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.060510] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.060523] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe606000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076351] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076448] hub 2-0:1.0: USB hub found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076451] hub 2-0:1.0: 2 ports detected
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076497] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076506] uhci_hcd: USB Universal Host Controller Interface driver
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076534] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076553] xhci_hcd 0000:02:00.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076558] xhci_hcd 0000:02:00.0: xHCI Host Controller
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.076595] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081034] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfe500000
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081105] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081110] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081114] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081256] xHCI xhci_add_endpoint called for root hub
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081257] xHCI xhci_check_bandwidth called for root hub
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081278] hub 3-0:1.0: USB hub found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081286] hub 3-0:1.0: 2 ports detected
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081332] xhci_hcd 0000:02:00.0: xHCI Host Controller
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081368] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081332] xhci_hcd 0000:02:00.0: xHCI Host Controller
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081368] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081443] xHCI xhci_add_endpoint called for root hub
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081444] xHCI xhci_check_bandwidth called for root hub
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081464] hub 4-0:1.0: USB hub found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.081471] hub 4-0:1.0: 2 ports detected
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.100343] usbcore: registered new interface driver libusual
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.100386] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.100824] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.100829] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.100940] mousedev: PS/2 mouse device common for all mice
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101072] rtc_cmos 00:06: RTC can wake from S4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101217] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101258] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101301] device-mapper: uevent: version 1.0.3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101362] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-deve$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101386] EISA: Probing bus 0 at eisa.0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101387] EISA: Cannot allocate resource for mainboard
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101389] Cannot allocate resource for EISA slot 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101391] Cannot allocate resource for EISA slot 2
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101392] Cannot allocate resource for EISA slot 3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101393] Cannot allocate resource for EISA slot 4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101395] Cannot allocate resource for EISA slot 5
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101396] Cannot allocate resource for EISA slot 6
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101397] Cannot allocate resource for EISA slot 7
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101398] Cannot allocate resource for EISA slot 8
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101400] EISA: Detected 0 cards.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101407] cpufreq-nforce2: No nForce2 chipset.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101452] cpuidle: using governor ladder
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101523] cpuidle: using governor menu
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101525] EFI Variables Facility v0.08 2004-May-17
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101678] TCP cubic registered
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.101768] NET: Registered protocol family 10
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102111] NET: Registered protocol family 17
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102114] Registering the dns_resolver key type
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102132] Using IPI No-Shortcut mode
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102301] PM: Hibernation image not present or could not be loaded.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102312] registered taskstats version 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102301] PM: Hibernation image not present or could not be loaded.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.102312] registered taskstats version 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.107516]   Magic number: 0:362:310
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.107545] tty tty39: hash matches
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.107621] rtc_cmos 00:06: setting system clock to 2012-10-10 03:19:12 UTC (134$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.107994] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.107995] EDD information not available.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.356049] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.356080] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.358498] ata2.00: ATA-8: WDC WD5000BEVT-00A0RT0, 01.01A01, max UDMA/133
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.358502] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.358747] ata1.00: ATA-8: WDC WD5000BEVT-00A0RT0, 01.01A01, max UDMA/133
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.358751] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.360996] ata2.00: configured for UDMA/133
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.361684] ata1.00: configured for UDMA/133
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.361897] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-0 01.0 PQ: 0$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362029] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362043] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362090] sd 0:0:0:0: [sda] Write Protect is off
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362092] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362107] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362133] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-0 01.0 PQ: 0$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362229] sd 1:0:0:0: Attached scsi generic sg1 type 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362281] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362315] sd 1:0:0:0: [sdb] Write Protect is off
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362317] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.362332] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.368000] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.413925]  sda: sda1 sda2 < sda5 >
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.414611] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.424328]  sdb: sdb1 sdb2 < sdb5 >
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.425196] sd 1:0:0:0: [sdb] Attached SCSI disk
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.425287] Freeing unused kernel memory: 740k freed
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.425456] Write protecting the kernel text: 5820k
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.425471] Write protecting the kernel read-only data: 2376k
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.425473] NX-protecting the kernel data: 4420k
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.476567] [drm] Initialized drm 1.1.0 20060810
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.485061] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.476567] [drm] Initialized drm 1.1.0 20060810
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.485061] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.485066] i915 0000:00:02.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.502872] hub 1-1:1.0: USB hub found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.502947] hub 1-1:1.0: 6 ports detected
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.503741] i915 0000:00:02.0: irq 47 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.503746] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.503748] [drm] Driver supports precise vblank timestamp query.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.503807] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,d$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.601154] md: bind<sdb1>
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.615685] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.627643] Refined TSC clocksource calibration: 2494.332 MHz.
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.627647] Switching to clocksource tsc
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.661204] md: bind<sda1>
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.662739] md: raid1 personality registered for level 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.662827] bio: create slab <bio-1> at 1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.662875] md/raid1:md0: active with 2 out of 2 mirrors
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.662892] md0: detected capacity change from 0 to 494789394432
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.677830]  md0: unknown partition table
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.748158] hub 2-1:1.0: USB hub found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.748251] hub 2-1:1.0: 8 ports detected
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.775459] No connectors reported connected with modes
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.775466] [drm] Cannot find any crtc or sizes - going 1024x768
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.778672] fbcon: inteldrmfb (fb0) is primary device
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.778784] Console: switching to colour frame buffer device 128x48
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.781064] fb0: inteldrmfb frame buffer device
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.781065] drm: registered panic notifier
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.781078] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.885983] md: linear personality registered for level -1
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.887179] md: multipath personality registered for level -4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.888352] md: raid0 personality registered for level 0
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.890418] async_tx: api initialized (async)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.890674] xor: automatically using best checksumming function: pIII_sse
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.907264]    pIII_sse  : 11224.000 MB/sec
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.907266] xor: using function: pIII_sse (11224.000 MB/sec)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    1.975185] raid6: int32x1   1068 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.043095] raid6: int32x2   1032 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.111027] raid6: int32x4    967 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.043095] raid6: int32x2   1032 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.111027] raid6: int32x4    967 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.178937] raid6: int32x8   1090 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.246830] raid6: mmxx1     4078 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.314739] raid6: mmxx2     4386 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.382656] raid6: sse1x1    3442 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.450562] raid6: sse1x2    4236 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.518470] raid6: sse2x1    6887 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.586388] raid6: sse2x2    8490 MB/s
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.586389] raid6: using algorithm sse2x2 (8490 MB/s)
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.587057] md: raid6 personality registered for level 6
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.587060] md: raid5 personality registered for level 5
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.587062] md: raid4 personality registered for level 4
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.590841] md: raid10 personality registered for level 10
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.658496] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.719342] EXT4-fs (md0): INFO: recovery required on readonly filesystem
Oct 10 05:19:21 ilitoo-montelimar kernel: [    2.719346] EXT4-fs (md0): write access will be enabled during recovery
Oct 10 05:19:21 ilitoo-montelimar kernel: [    3.274696] EXT4-fs (md0): recovery complete
Oct 10 05:19:21 ilitoo-montelimar kernel: [    3.445963] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (nul$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.486384] Adding 5191676k swap on /dev/sda5.  Priority:-1 extents:1 across:519$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.506328] Adding 5191676k swap on /dev/sdb5.  Priority:-2 extents:1 across:519$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.530997] lp: driver loaded but no devices found
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.533365] f71882fg: Found f71808a chip at 0x290, revision 33
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.533483] f71882fg f71882fg.656: Fan: 1 is in duty-cycle mode
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.533490] f71882fg f71882fg.656: Auto pwm controlled by raw digital data, disa$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.533496] f71882fg f71882fg.656: Fan: 2 is in duty-cycle mode
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.556120] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ $
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.556187] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.556220] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.577457] sk98lin 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.577467] sk98lin: Network Device Driver v10.92.1.3
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.577468] (C)Copyright 1999-2012 Marvell(R).
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.577482] sk98lin 0000:03:00.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582162] Bluetooth: Core ver 2.16
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582397] NET: Registered protocol family 31
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582399] Bluetooth: HCI device and connection manager initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582402] Bluetooth: HCI socket layer initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582403] Bluetooth: L2CAP socket layer initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582402] Bluetooth: HCI socket layer initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582403] Bluetooth: L2CAP socket layer initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.582409] Bluetooth: SCO socket layer initialized
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.585876] Bluetooth: Generic Bluetooth USB driver ver 0.6
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.591970] usbcore: registered new interface driver btusb
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.594757] mei: module is from the staging directory, the quality is unknown, y$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.595754] eth0: Generic Marvell Yukon chipset Ethernet device
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.714545] type=1400 audit(1349839161.115:2): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.714554] type=1400 audit(1349839161.115:3): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.714925] type=1400 audit(1349839161.115:4): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.714938] type=1400 audit(1349839161.115:5): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.715138] type=1400 audit(1349839161.115:6): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [    9.715154] type=1400 audit(1349839161.115:7): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116076] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116138] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116243] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116308] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116359] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116407] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/s$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116455] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/so$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116502] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116549] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116598] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:0$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116649] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116903] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116909] mei 0000:00:16.0: setting latency timer to 64
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.116980] mei 0000:00:16.0: irq 49 for MSI/MSI-X
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.163277] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.206983] init: failsafe main process (757) killed by TERM signal
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.321703] type=1400 audit(1349839161.723:8): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.322098] type=1400 audit(1349839161.723:9): apparmor="STATUS" operation="prof$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.322314] type=1400 audit(1349839161.723:10): apparmor="STATUS" operation="pro$
Oct 10 05:19:21 ilitoo-montelimar kernel: [   10.324164] type=1400 audit(1349839161.723:11): apparmor="STATUS" operation="pro$
Oct 10 05:19:22 ilitoo-montelimar kernel: [   11.037057] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 10 05:19:22 ilitoo-montelimar kernel: [   11.042378] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct 10 05:19:22 ilitoo-montelimar chillispot[1046]: chilli.c: 373: Could not resolve IP address of uamserver: http://proxy.il$
Oct 10 05:19:22 ilitoo-montelimar kernel: [   11.161181] init: plymouth-upstart-bridge main process (786) killed by TERM sign$
Oct 10 06:17:01 ilitoo-montelimar CRON[1532]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 07:17:02 ilitoo-montelimar CRON[1991]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 08:17:01 ilitoo-montelimar CRON[2450]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 10 08:57:13 ilitoo-montelimar kernel: [13065.612054] usb 2-1.3: new low-speed USB device number 4 using ehci_hcd
Oct 10 08:57:14 ilitoo-montelimar kernel: [13065.798635] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.0/us$
Oct 10 08:57:14 ilitoo-montelimar kernel: [13065.798722] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboa$
Oct 10 08:57:14 ilitoo-montelimar kernel: [13065.798734] usbcore: registered new interface driver usbhid
Oct 10 08:57:14 ilitoo-montelimar kernel: [13065.798736] usbhid: USB HID core driver

```

My server reboots another time with no error, at 08:57:13 I plug a USB keyboard and reboot manually at 08:58.

I think my NIC is lost when my server take a reboot from the space ! I don't have any cron which have reboot instruction, that's why I don't understand the issue.

Is there any log where I can search to understand why my server reboot ?

I'll perform some hardware test to see if the RAM or any-hardware materials are making my server reboot.


Regards,

LaBanane.

---

