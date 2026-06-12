---
title: "network connection problem"
date: 2010-06-01
forum: General Help
---

### Post by adimopoulos on 2010-06-01
Hi everybody

First time writing here. I have a small problem. Suddenly i have no Internet at all. My workstation has an intel core i5 650 3200 Ghz with a motherboard MB GIGABYTE GA-H55M-S2H(1156/H55/DDR3 my rooter is a TOMSON tg585 and i'm connected with Ethernet cable. I'm running 10.04 64bit and had no problem for the last 2 months. I'm now on a live cd xubuntu 9.10 32bit so i suppose the problem is not from my provider or from my rooter conection. Here is part of my syslog and ifconfig hope someone can help. thanks 

May 30 09:35:27 aris-pc kernel: [   12.723301] type=1505 audit(1275201327.276:7):  operation="profile_replace" pid=808 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 30 09:35:27 aris-pc kernel: [   12.723466] type=1505 audit(1275201327.276:8):  operation="profile_replace" pid=808 name="/usr/lib/connman/scripts/dhclient-script"
May 30 09:35:27 aris-pc kernel: [   12.772959] type=1505 audit(1275201327.326:9):  operation="profile_load" pid=809 name="/usr/bin/evince"
May 30 09:35:27 aris-pc kernel: [   12.776906] type=1505 audit(1275201327.326:10):  operation="profile_load" pid=809 name="/usr/bin/evince-previewer"
May 30 09:35:27 aris-pc kernel: [   12.779363] type=1505 audit(1275201327.326:11):  operation="profile_load" pid=809 name="/usr/bin/evince-thumbnailer"
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Sierra
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Option High-Speed
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Ericsson MBM
May 30 09:35:27 aris-pc NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
May 30 09:35:27 aris-pc NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
May 30 09:35:27 aris-pc NetworkManager:    SCPlugin-Ifupdown: (37827872) ... get_connections.
May 30 09:35:27 aris-pc NetworkManager:    SCPlugin-Ifupdown: (37827872) ... get_connections (managed=false): return empty list.
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Longcheer
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Huawei
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Novatel
May 30 09:35:27 aris-pc modem-manager: Loaded plugin Generic
May 30 09:35:27 aris-pc modem-manager: Loaded plugin AnyData
May 30 09:35:27 aris-pc NetworkManager:    Ifupdown: get unmanaged devices count: 0
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): carrier is OFF
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): now managed
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): bringing up device.
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): preparing device.
May 30 09:35:27 aris-pc NetworkManager: <info>  (eth0): deactivating device (reason: 2).
May 30 09:35:27 aris-pc NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0
May 30 09:35:27 aris-pc kernel: [   12.930738] r8169: eth0: link down
May 30 09:35:27 aris-pc kernel: [   12.930991] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 30 09:35:27 aris-pc NetworkManager: <info>  modem-manager is now available
May 30 09:35:27 aris-pc NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
May 30 09:35:27 aris-pc NetworkManager: <info>  Trying to start the supplicant...
May 30 09:35:27 aris-pc init: apport pre-start process (946) terminated with status 1
May 30 09:35:27 aris-pc gdm-binary[816]: WARNING: Unable to find users: no seat-id found
May 30 09:35:27 aris-pc cron[951]: (CRON) INFO (pidfile fd = 3)
May 30 09:35:27 aris-pc acpid: starting up with proc fs
May 30 09:35:27 aris-pc init: apport post-stop process (964) terminated with status 1
May 30 09:35:27 aris-pc acpid: 36 rules loaded
May 30 09:35:27 aris-pc acpid: waiting for events: event logging is off
May 30 09:35:27 aris-pc avahi-daemon[822]: Network interface enumeration completed.
May 30 09:35:27 aris-pc avahi-daemon[822]: Registering HINFO record with values 'X86_64'/'LINUX'.
May 30 09:35:27 aris-pc avahi-daemon[822]: Server startup complete. Host name is aris-pc.local. Local service cookie is 232314403.
May 30 09:35:27 aris-pc anacron[997]: Anacron 2.3 started on 2010-05-30
May 30 09:35:27 aris-pc cron[998]: (CRON) STARTUP (fork ok)
May 30 09:35:27 aris-pc cron[998]: (CRON) INFO (Running @reboot jobs)
May 30 09:35:27 aris-pc kernel: [   13.190410] ppdev: user-space parallel port driver
May 30 09:35:27 aris-pc anacron[997]: Will run job `cron.daily' in 5 min.
May 30 09:35:27 aris-pc anacron[997]: Jobs will be executed sequentially
May 30 09:35:27 aris-pc acpid: client connected from 1001[0:0]
May 30 09:35:27 aris-pc acpid: 1 client rule loaded
May 30 09:35:28 aris-pc gdm-session-worker[1139]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Sucessfully called chroot.
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Sucessfully dropped privileges.
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Sucessfully limited resources.
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Running.
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Watchdog thread running.
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Canary thread running.
May 30 09:35:29 aris-pc polkitd[1211]: started daemon version 0.96 using authority implementation `local' version `0.96'
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Sucessfully made thread 1205 of process 1205 (n/a) owned by '1000' high priority at nice level -11.
May 30 09:35:29 aris-pc rtkit-daemon[1207]: Supervising 1 threads of 1 processes of 1 users.
May 30 09:35:30 aris-pc acpid: client connected from 1390[108:114]
May 30 09:35:30 aris-pc acpid: 1 client rule loaded
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Sucessfully made thread 1396 of process 1205 (n/a) owned by '1000' RT at priority 5.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Supervising 2 threads of 1 processes of 1 users.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Sucessfully made thread 1397 of process 1205 (n/a) owned by '1000' RT at priority 5.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Supervising 3 threads of 1 processes of 1 users.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Sucessfully made thread 1399 of process 1399 (n/a) owned by '1000' high priority at nice level -11.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Supervising 4 threads of 2 processes of 1 users.
May 30 09:35:31 aris-pc pulseaudio[1399]: pid.c: Daemon already running.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Sucessfully made thread 1400 of process 1400 (n/a) owned by '1000' high priority at nice level -11.
May 30 09:35:31 aris-pc rtkit-daemon[1207]: Supervising 4 threads of 2 processes of 1 users.
May 30 09:35:31 aris-pc pulseaudio[1400]: pid.c: Daemon already running.
May 30 09:36:33 aris-pc AptDaemon: INFO: Initializing daemon
aris@aris-pc:~$ 

and here is my ifconfig

ris@aris-pc:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:74:92:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

