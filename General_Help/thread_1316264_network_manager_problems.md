---
title: "network manager problems"
date: 2009-11-05
forum: General Help
---

### Post by -jay- on 2009-11-05
ok i get this all the time it works fine in windows vista/7 but i keep getting disconnected from network manager

connection wired , no router , cable 15mb/2mb roadrunner/timewarn
er

heres a log showing whatever is wrong if somebody can pinpoint whats going on thanks

```
jay@ubuntu:~$ pidof NetworkManager
2438
jay@ubuntu:~$ sudo grep -riC 2 networkmanager /var/log | tail -n 500
[sudo] password for jay: 
/var/log/dmesg-[   13.224460] type=1505 audit(1257470308.097:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1966
/var/log/dmesg-[   13.224567] type=1505 audit(1257470308.097:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1966
/var/log/dmesg:[   13.224602] type=1505 audit(1257470308.097:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1966
/var/log/dmesg-[   13.224636] type=1505 audit(1257470308.097:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1966
/var/log/dmesg-[   13.328127] type=1505 audit(1257470308.201:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1971
--
/var/log/apt/term.log-Setting up nautilus-share (0.7.2-4ubuntu1) ...
/var/log/apt/term.log-Setting up network-manager (0.7.1~rc4.1.cf199a964-0ubuntu2) ...
/var/log/apt/term.log: Adding system startup for /etc/init.d/NetworkManager ...
/var/log/apt/term.log:   /etc/rc2.d/S50NetworkManager -> ../init.d/NetworkManager
/var/log/apt/term.log:   /etc/rc3.d/S50NetworkManager -> ../init.d/NetworkManager
/var/log/apt/term.log:   /etc/rc4.d/S50NetworkManager -> ../init.d/NetworkManager
/var/log/apt/term.log:   /etc/rc5.d/S50NetworkManager -> ../init.d/NetworkManager
/var/log/apt/term.log-
/var/log/apt/term.log-Setting up network-manager-gnome (0.7.1~rc4.1-0ubuntu2) ...
--
/var/log/installer/syslog-Nov  3 00:17:06 ubuntu kernel: [   71.336513] Bridge firewalling registered
/var/log/installer/syslog-Nov  3 00:17:06 ubuntu bluetoothd[4163]: Registered interface org.bluez.Service on path /org/bluez/4163/any
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu NetworkManager: <info>  starting... 
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'forcedeth') 
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_16_e6_86_92_73 
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
/var/log/installer/syslog-Nov  3 00:17:07 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
/var/log/installer/syslog-Nov  3 00:17:07 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
--
/var/log/installer/syslog-Nov  3 00:17:07 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_16_e6_86_92_73, iface: eth0): not well known
/var/log/installer/syslog-Nov  3 00:17:07 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
/var/log/installer/syslog:Nov  3 00:17:07 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
/var/log/installer/syslog:Nov  3 00:17:08 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
/var/log/installer/syslog-Nov  3 00:17:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (22630752) ... get_connections.
/var/log/installer/syslog-Nov  3 00:17:08 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (22630752) ... get_connections (managed=false): return empty list.
/var/log/installer/syslog-Nov  3 00:17:08 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
/var/log/installer/syslog-Nov  3 00:17:10 ubuntu acpid: client connected from 4284[0:0] 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): device state change: 1 -> 2 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): bringing up device. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): preparing device. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): device state change: 2 -> 3 
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_16_e6_86_92_73
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): device state change: 3 -> 4 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): device state change: 4 -> 5 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  (eth0): device state change: 5 -> 7 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  dhclient started with pid 4288 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.1.1
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
--
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu dhclient: 
/var/log/installer/syslog:Nov  3 00:17:12 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu dhclient: Listening on LPF/eth0/00:16:e6:86:92:73
/var/log/installer/syslog-Nov  3 00:17:12 ubuntu dhclient: Sending on   LPF/eth0/00:16:e6:86:92:73
--
/var/log/installer/syslog-Nov  3 00:17:16 ubuntu dhclient: DHCPREQUEST of 75.82.153.149 on eth0 to 255.255.255.255 port 67
/var/log/installer/syslog-Nov  3 00:17:16 ubuntu dhclient: DHCPACK of 75.82.153.149 from 10.46.0.1
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
/var/log/installer/syslog-Nov  3 00:17:16 ubuntu dhclient: bound to 75.82.153.149 -- renewal in 35963 seconds.
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    address 75.82.153.149 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    prefix 21 (255.255.248.0) 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    gateway 75.82.152.1 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    hostname 'ubuntu' 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    nameserver '209.18.47.61' 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    nameserver '209.18.47.62' 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>    domain name 'socal.rr.com' 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
/var/log/installer/syslog:Nov  3 00:17:16 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
/var/log/installer/syslog:Nov  3 00:17:17 ubuntu NetworkManager: <info>  (eth0): device state change: 7 -> 8 
/var/log/installer/syslog:Nov  3 00:17:17 ubuntu NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
/var/log/installer/syslog:Nov  3 00:17:17 ubuntu NetworkManager: <info>  Activation (eth0) successful, device activated. 
/var/log/installer/syslog:Nov  3 00:17:17 ubuntu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
/var/log/installer/syslog-Nov  3 00:17:21 ubuntu ntpdate[4367]: adjust time server 91.189.94.4 offset -0.060533 sec
/var/log/installer/syslog-Nov  3 00:17:22 ubuntu kernel: [   87.468012] eth0: no IPv6 routers present
--
/var/log/installer/syslog-Nov  3 00:24:29 ubuntu python: Not copying usr/share/locale-langpack/de/LC_MESSAGES/Linux-PAM.mo
/var/log/installer/syslog-Nov  3 00:24:29 ubuntu python: Not copying usr/share/locale-langpack/de/LC_MESSAGES/MoinMoin.mo
/var/log/installer/syslog:Nov  3 00:24:29 ubuntu python: Not copying usr/share/locale-langpack/de/LC_MESSAGES/NetworkManager.mo
/var/log/installer/syslog-Nov  3 00:24:29 ubuntu python: Not copying usr/share/locale-langpack/de/LC_MESSAGES/PackageKit.mo
/var/log/installer/syslog-Nov  3 00:24:29 ubuntu python: Not copying usr/share/locale-langpack/de/LC_MESSAGES/PolicyKit-gnome.mo
--
/var/log/installer/syslog-Nov  3 00:24:30 ubuntu python: Not copying usr/share/locale-langpack/es/LC_MESSAGES/Linux-PAM.mo
/var/log/installer/syslog-Nov  3 00:24:30 ubuntu python: Not copying usr/share/locale-langpack/es/LC_MESSAGES/MoinMoin.mo
/var/log/installer/syslog:Nov  3 00:24:30 ubuntu python: Not copying usr/share/locale-langpack/es/LC_MESSAGES/NetworkManager.mo
/var/log/installer/syslog-Nov  3 00:24:30 ubuntu python: Not copying usr/share/locale-langpack/es/LC_MESSAGES/PackageKit.mo
/var/log/installer/syslog-Nov  3 00:24:30 ubuntu python: Not copying usr/share/locale-langpack/es/LC_MESSAGES/Parse-DebianChangelog-Pod.mo
--
/var/log/dmesg.0-[   13.538248] type=1505 audit(1257465403.405:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1993
/var/log/dmesg.0-[   13.538361] type=1505 audit(1257465403.405:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1993
/var/log/dmesg.0:[   13.538395] type=1505 audit(1257465403.405:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1993
/var/log/dmesg.0-[   13.538428] type=1505 audit(1257465403.405:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1993
/var/log/dmesg.0-[   13.641059] type=1505 audit(1257465403.509:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1998
--
/var/log/pm-suspend.log-not applicable.
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/var/log/pm-suspend.log:/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/90chvt suspend suspend: success.
--
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/90chvt resume suspend: success.
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/var/log/pm-suspend.log:/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/var/log/pm-suspend.log-/usr/lib/pm-utils/sleep.d/45iwlist resume suspend: /sbin/iwlist

```

---

### Post by ram2500 on 2009-11-05
What's the output of ifconfig?

---

### Post by -jay- on 2009-11-05
heres the output from ifconfig

```

jay@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:e6:86:92:73  
          inet addr:75.82.153.149  Bcast:75.82.159.255  Mask:255.255.248.0
          inet6 addr: fe80::216:e6ff:fe86:9273/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19597918 (19.5 MB)  TX bytes:3123246 (3.1 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jay@ubuntu:~$ 

```

---

### Post by -jay- on 2009-11-06
bump , anybody know ?

---

### Post by mo.reina on 2009-11-06
have you tried connecting through the terminal and seeing if you have the same problem? what happens if you run dhclient from the terminal?

---

### Post by -jay- on 2009-11-06
heres the output on that 

```

jay@ubuntu:~$ sudo dhclient
[sudo] password for jay: 
There is already a pid file /var/run/dhclient.pid with pid 20066
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:e6:86:92:73
Sending on   LPF/eth0/00:16:e6:86:92:73
Sending on   Socket/fallback
DHCPREQUEST of 75.82.153.149 on eth0 to 255.255.255.255 port 67
DHCPACK of 75.82.153.149 from 10.46.0.1
bound to 75.82.153.149 -- renewal in 30102 seconds.
jay@ubuntu:~$ 



```

---

### Post by mo.reina on 2009-11-06
so are you being disconnected or is the connection stable through the terminal?

---

### Post by -jay- on 2009-11-06
i been getting disconnected with  network manager saying the following

wired network
disconnected - you are now offline 

i get this ever 3 to 5 mins popping up & its annoying im trying to figure whats causing it

---

### Post by mo.reina on 2009-11-06
what i mean is, if you connect through the terminal using dhclient, do you have a stable connection?  ignore whatever the network manager GUI is telling you, if you use dhclient you are bypassing network manager.

use dhclient and surf for the next 10 minutes.  see if you are still being disconnected

---

### Post by -jay- on 2009-11-06
doing that made it not have a connection at all tried checking sites like cnn.com & nothing

---

### Post by mo.reina on 2009-11-06
ok let's do a step by step process to make sure that network manager isn't interfering:
right click on the network manager icon and unclick "enable networking"
now go to the terminal and enter this command
```
ifconfig
```
post the output of the command, but the only thing that should come out should look something like this:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24688 (24.6 KB)  TX bytes:24688 (24.6 KB)

```
now enter this command:
```
ifconfig eth0 up 
```
that will tell your computer to activate your ethernet interface
hit ifconfig again, something like this should come out:
```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:2f:85:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:248 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28849 (28.8 KB)  TX bytes:28849 (28.8 KB)

```
you'll notice that eth0 is now included in the output
now hit the dhclient command again
```
dhclient
```
now try to surf.  make sure that your browser isn't in offline mode.

---

### Post by -jay- on 2009-11-06
ifconfig


```
 jay@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:283532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52497849 (52.4 MB)  TX bytes:52497849 (52.4 MB)

jay@ubuntu:~$ 


```

ok im able to surf with it disabled so anyway to keep it enabled & not have it pop up every few minutes?

---

### Post by -jay- on 2009-11-06
so do i have keep it disabled always???

---

### Post by mo.reina on 2009-11-06
well if you can surf by connecting through the terminal it means that the problem is network-manager, not your connection or your hardware.

i'd suggest removing then re-installing network-manager.  if the problem re-appears you can try using wicd instead, just do 
apt-get install wicd

---

### Post by mo.reina on 2009-11-06
oh and please have the thread marked solved, it saves time for other searchers with the same problem

---

### Post by HiImTye on 2009-11-06
I would try disabling ipv6. your 'stable connection' is only lacking an ipv6 address and your log showed no ipv6

try that and see if it works

---

### Post by HiImTye on 2009-11-06
> **HiImTye said:**
> I would try disabling ipv6. your 'stable connection' is only lacking an ipv6 address and your log showed no ipv6

try that and see if it works
nevermind thats the loopback

---

### Post by -jay- on 2009-11-06
> **mo.reina said:**
> well if you can surf by connecting through the terminal it means that the problem is network-manager, not your connection or your hardware.

i'd suggest removing then re-installing network-manager.  if the problem re-appears you can try using wicd instead, just do 
apt-get install wicd

thanks looks like ill be using wicd instead thanks for the help

---

