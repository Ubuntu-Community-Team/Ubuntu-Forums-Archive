---
title: "Freezing: No service file found in /etc/avahi/services"
date: 2010-01-28
forum: General Help
---

### Post by Jiminy Cricket on 2010-01-28
So I recently install Kubuntu 9.10. The installation went smoothly, but when I boot up, the whole system freezes a few seconds after the loading screen finishes (at this point, one can see the two dots chasing each other in a circle, I assume the Kubuntu 'progress' mouse.) I also tried installing Ubuntu 9.10 and Xubuntu 9.10 and the same thing happens. I looked through the logs, and the only "error" like thing I could find was in syslog, the last 40 lines of which are pasted below. I marked the lines I was noticing with big arrows. Could someone please tell me if this is possibly the cause of my freezing, and if so, how I should go about fixing it?
```

Jan 27 12:44:50 ubuntu bluetoothd[2545]: Starting SDP server
Jan 27 12:44:50 ubuntu kernel: [   22.051935] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 27 12:44:50 ubuntu kernel: [   22.051941] Bluetooth: BNEP filters: protocol multicast
Jan 27 12:44:50 ubuntu kernel: [   22.083835] Bridge firewalling registered
Jan 27 12:44:50 ubuntu bluetoothd[2545]: bridge pan0 created
Jan 27 12:44:50 ubuntu bluetoothd[2545]: Registered interface org.bluez.Service on path /org/bluez/2545/any
Jan 27 12:44:50 ubuntu bluetoothd[2545]: Starting experimental netlink support
Jan 27 12:44:50 ubuntu bluetoothd[2545]: Failed to find Bluetooth netlink family
Jan 27 12:44:51 ubuntu NetworkManager: <info>  starting... 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'NULL(info.linux.driver)') 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_12_3f_d4_b1_a4 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rtl8180') 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_17_3f_31_26_e6 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  Trying to start the supplicant... 
Jan 27 12:44:51 ubuntu NetworkManager: <info>  Trying to start the system settings daemon... 
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Successfully dropped root privileges.
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: avahi-daemon 0.6.23 starting up.
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: init!
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Successfully called chroot().
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Successfully dropped remaining capabilities.
Jan 27 12:44:51 ubuntu avahi-daemon[2623]: chroot.c: open() failed: No such file or directory
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_12_3f_d4_b1_a4, iface: eth0): not well known
---------->**Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Failed to open /etc/resolv.conf: Invalid argument**
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_17_3f_31_26_e6, iface: wlan0): not well known
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: end _init.
Jan 27 12:44:51 ubuntu nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 27 12:44:51 ubuntu nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
---------->**Jan 27 12:44:51 ubuntu avahi-daemon[2622]: No service file found in /etc/avahi/services.**
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Network interface enumeration completed.
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 27 12:44:51 ubuntu avahi-daemon[2622]: Server startup complete. Host name is ubuntu.local. Local service cookie is 4198073178.
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (165762872) ... get_connections.
Jan 27 12:44:51 ubuntu nm-system-settings:    SCPlugin-Ifupdown: (165762872) ... get_connections (managed=false): return empty list.
Jan 27 12:44:51 ubuntu nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Jan 27 12:44:51 ubuntu NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
```

---

### Post by DoubleDown on 2010-01-28
This looks to be an issue with compiz.  Please disable it upon startup.  Also please post your output in [code] tags.

---

### Post by Jiminy Cricket on 2010-01-28
I edited and added [code] tags.

Thank you for the response. Would you mind telling me exactly how to disable compiz at startup?

---

### Post by DoubleDown on 2010-01-28
> **Jiminy Cricket said:**
> I edited and added [code] tags.
 
Thank you for the response. Would you mind telling me exactly how to disable compiz at startup?
 
Try: man compiz

---

