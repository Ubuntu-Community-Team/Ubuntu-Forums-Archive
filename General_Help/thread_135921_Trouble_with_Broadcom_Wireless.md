---
title: "Trouble with Broadcom Wireless"
date: 2006-02-24
forum: General Help
---

### Post by jasper24 on 2006-02-24
I have been fighting for several days now to get my Broadcom 4318 wireless to work. I have read and re-read every how-to I can. I have made some progress, but still can't get it to connect.

I get this when I ifup eth0
----------------------------------------------
jasper@jasperhplaptop:~$ sudo ifup eth0
/etc/network/if-pre-up.d/wireless-tools: eval: line 58: syntax error near unexpected token `('
/etc/network/if-pre-up.d/wireless-tools: eval: line 58: `/sbin/iwconfig eth0 key 80211g.zip BCMWL564.SYS Desktop Setup.exe WL_T60H906(8.0.10.0,XP64_logo) bcm43xx.cat bcmwl5.inf logs'
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth0/00:14:a5:6a:48:d5
Sending on   LPF/eth0/00:14:a5:6a:48:d5
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
---------------------------------
iwconfig:
---------------------------------
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"jasper"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=54 Mb/s
          Tx-Power=off
          RTS thr:off   Fragment thr:off

eth1      no wireless extensions.

sit0      no wireless extensions.
-------------------------------------
ifconfig:
-------------------------------------
eth1      Link encap:Ethernet  HWaddr 00:0F:B0:C2:5E:02
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fec2:5e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7523090 (7.1 MiB)  TX bytes:1412288 (1.3 MiB)
          Interrupt:50 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:114552 (111.8 KiB)  TX bytes:114552 (111.8 KiB)
-------------------------------------------
/etc/network/interface
-------------------------------------------
# The primary network interface
iface eth1 inet dhcp
auto eth0
iface eth0 inet dhcp
wireless-essid jasper
ap 00:13:46:4D:0B:F8
channel 6
wireless-key **********
-------------------------------------------
I am trying to use WEP ( I have tried WAP and no encription as well)

Using KDE, it eth0 shows up in the network settings, but its disabled. When I try and enable it, it comes on for a second or two and then disables.

For some reason it's not getting the AP. I can't figure it out. Everything appears to be setup right.

I have setup ndiswrapper with the appropriate driver
----------------------------------------
ndiswrapper -l:
----------------------------------------
Installed ndis drivers:
bcmwl5          driver present, hardware present

I am out of ideas, and am hoping that someone here can help.

Thanks,
Jasper

---

### Post by jak on 2006-04-29
I have the **exact **same problem.. Any news?

---

### Post by gondilon on 2006-04-29
try sudo modprobe nsidprapper and then see if your card appears in the network connections dialog.

---

### Post by jak on 2006-04-30
It's there, it appears, it just doesnt connect.
Here's where the problem is visible.
```

eth0 IEEE 802.11b/g ESSID:"jasper" Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid Bit Rate=54 Mb/s

```
for some people, they say using
```

sudo iwconfig eth0 ap any

```
should fix that. But it doesnt, not for me.

---

### Post by Ramses on 2006-05-02
> /etc/network/if-pre-up.d/wireless-tools: eval: line 58: syntax error near unexpected token `('
/etc/network/if-pre-up.d/wireless-tools: eval: line 58: `/sbin/iwconfig eth0 key **80211g.zip BCMWL564.SYS Desktop Setup.exe WL_T60H906(8.0.10.0,XP64_logo) bcm43xx.cat bcmwl5.inf logs**'

That part looks suspicious. Looks like you copy-pasted wrong things to WEP-key or something. 

I just finished yesterday configuring my own laptop (with broadcom 4318) and noticed that it is better to edit /etc/network/interfaces file by hand than with some gui. Network configuration sucks in KDE.
I noticed too that Wifi-radar messes up KDE and broke my wifi initially. Uninstallation of Wifi-radar fixed things if you happen to have that installed.

Some Acer notebooks have software controlled antennas which you must activate with acer_acpi or acerhk before you can use wireless.

```
iface eth0 inet dhcp
wireless-essid jasper
ap 00:13:46:4D:0B:F8
channel 6
wireless-key **********
```
My wireless key is in ascii (s before the key is for that) form and is like this:
```
wireless-key s:mykey
```
I just removed stars and wrote key to file. I dont't know if that is the proper way, but it worked. I didn't need channel or ap line.

Maybe you should first try to get wireless working without WEP.

---

### Post by Goldenice on 2006-06-03
I had the same problem with my BCM4309.

I have solved the problem with this guide:

[http://www.ubuntuforums.org/showthread.php?t=186538](http://www.ubuntuforums.org/showthread.php?t=186538)

I've only did 1,3,5,7 and 8 steps.

Sorry for my bad english.

---

### Post by phaeton77 on 2006-06-04
I had this same problem with my Linksys WMP11 v2.7 card.  What was happening was the kernel was trying to load the broadcom chipset's firmware on boot, and it somehow conflicted with ndiswrapper enabling the card and allowing me to start it up.  

If you run dmesg you will most likely see the kernel giving an error that the firmware could not be located for the broadcom chipset.  To circumvent this, add the bcm43xx module (the bad default module ubuntu is trying to load on boot) to the blacklist-watchdog file:
/etc/modprobe.d/blacklist-watchdog

Here's what mine looks like:
# Watchdog drivers should not be loaded automatically, but only if a
# watchdog daemon is installed.
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist booke_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i6300esb
blacklist i8xx_tco
blacklist ib700wdt
blacklist ibmasr
blacklist indydog
blacklist ixp2000_wdt
blacklist ixp4xx_wdt
blacklist machzwd
blacklist mixcomwd
blacklist mpc8xx_wdt
blacklist mpcore_wdt
blacklist mv64x60_wdt
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist s3c2410_wdt
blacklist sa1100_wdt
blacklist sbc60xxwdt
blacklist sb8360
blacklist sc1200wdt
blacklist sc520_wdt
blacklist scx200_wdt
blacklist shwdt
blacklist softdog
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci
blacklist bcm43xx


Worked like a charm for me.  After I entered this and rebooted, the kernel ignored trying to load that module and ndiswrapper worked great.

---

### Post by GreatestGravity on 2006-06-04
Thanks Phaeton! It worked great for me!

---

### Post by lois on 2006-06-17
Thank's a lot Phaeton77. Worked fine. And it makes sense.

---

