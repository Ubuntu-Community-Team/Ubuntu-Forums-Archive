---
title: "Very slow gnome login"
date: 2012-10-08
forum: General Help
---

### Post by Yehonal on 2012-10-08
Hello guys!
i've a problem during the login in ubuntu 11.10 ( with gnomeshell). It's very very slow, it takes about 2 minutes before the gnome-shell appears.
here you are some logs ( only the latest important part ):

kern.log
> Oct  8 09:17:18 hw2-ubuntu-work kernel: [   36.101363] vboxdrv: Successfully loaded version 4.1.22 (interface 0x00190000).
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.307206] vboxpci: IOMMU not found (not registered)
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.544640] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.572669] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618093] Bluetooth: Core ver 2.16
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618111] NET: Registered protocol family 31
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618112] Bluetooth: HCI device and connection manager initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618114] Bluetooth: HCI socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618115] Bluetooth: L2CAP socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618152] Bluetooth: SCO socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.619313] Bluetooth: RFCOMM TTY layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.619316] Bluetooth: RFCOMM socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.619317] Bluetooth: RFCOMM ver 1.11
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.621874] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.621876] Bluetooth: BNEP filters: protocol multicast
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.939629] eth9: Link up
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.940082] eth9: Link changed: 100Mbps, full duplex
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.940482] ADDRCONF(NETDEV_CHANGE): eth9: link becomes ready
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.990294] r8169 0000:02:00.0: eth19: link up
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.990449] ADDRCONF(NETDEV_CHANGE): eth19: link becomes ready
Oct  8 09:17:26 hw2-ubuntu-work kernel: [   44.112008] ham0: no IPv6 routers present
Oct  8 09:17:28 hw2-ubuntu-work kernel: [   45.552464] init: plymouth-stop pre-start process (1970) terminated with status 1
Oct  8 09:17:30 hw2-ubuntu-work kernel: [   47.200016] eth19: no IPv6 routers present
Oct  8 09:17:30 hw2-ubuntu-work kernel: [   47.552007] eth9: no IPv6 routers present
Oct  8 09:18:02 hw2-ubuntu-work kernel: [   80.386825] show_signal_msg: 51 callbacks suppressed
Oct  8 09:18:02 hw2-ubuntu-work kernel: [   80.386829] pulseaudio[2100]: segfault at 34 ip b0ed445a sp bff39d30 error 4 in module-loopback.so[b0ed2000+7000]
Oct  8 09:18:31 hw2-ubuntu-work kernel: [  109.741695] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
Oct  8 09:20:04 hw2-ubuntu-work kernel: [  203.084622] eth9: Link down
Oct  8 09:20:08 hw2-ubuntu-work kernel: [  206.380425] eth9: Link up
Oct  8 09:20:08 hw2-ubuntu-work kernel: [  206.380910] eth9: Link changed: 100Mbps, full duplex

syslog:
> Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618093] Bluetooth: Core ver 2.16
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618111] NET: Registered protocol family 31
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618112] Bluetooth: HCI device and connection manager initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618114] Bluetooth: HCI socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618115] Bluetooth: L2CAP socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.618152] Bluetooth: SCO socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.619313] Bluetooth: RFCOMM TTY layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.619316] Bluetooth: RFCOMM socket layer initialized
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.619317] Bluetooth: RFCOMM ver 1.11
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.621874] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.621876] Bluetooth: BNEP filters: protocol multicast
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.939629] eth9: Link up
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.940082] eth9: Link changed: 100Mbps, full duplex
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.940482] ADDRCONF(NETDEV_CHANGE): eth9: link becomes ready
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.990294] r8169 0000:02:00.0: eth19: link up
Oct  8 09:17:19 hw2-ubuntu-work kernel: [   36.990449] ADDRCONF(NETDEV_CHANGE): eth19: link becomes ready
Oct  8 09:17:19 hw2-ubuntu-work /etc/mysql/debian-start[1686]: Upgrading MySQL tables if necessary.
Oct  8 09:17:19 hw2-ubuntu-work gnome-session[1581]: WARNING: Failed to start app: Unable to start application: Esecuzione del processo figlio "/usr/lib/at-spi/at-spi-registryd" non riuscita (File o directory non esistente)
Oct  8 09:17:20 hw2-ubuntu-work /etc/mysql/debian-start[1689]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Oct  8 09:17:20 hw2-ubuntu-work /etc/mysql/debian-start[1689]: Looking for 'mysql' as: /usr/bin/mysql
Oct  8 09:17:20 hw2-ubuntu-work /etc/mysql/debian-start[1689]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Oct  8 09:17:20 hw2-ubuntu-work /etc/mysql/debian-start[1689]: This installation of MySQL is already upgraded to 5.1.63, use --force if you still need to run mysql_upgrade
Oct  8 09:17:20 hw2-ubuntu-work /etc/mysql/debian-start[1717]: Checking for insecure root accounts.
Oct  8 09:17:20 hw2-ubuntu-work /etc/mysql/debian-start[1730]: Triggering myisam-recover for all MyISAM tables
Oct  8 09:17:20 hw2-ubuntu-work dbus[1105]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Oct  8 09:17:20 hw2-ubuntu-work dbus[1105]: [system] Successfully activated service 'org.freedesktop.UPower'
Oct  8 09:17:20 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth9 --protocol tcp --destination-port 53 --jump ACCEPT
Oct  8 09:17:20 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth9 --protocol udp --destination-port 53 --jump ACCEPT
Oct  8 09:17:20 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth9 --protocol tcp --destination-port 67 --jump ACCEPT
Oct  8 09:17:20 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface eth9 --protocol udp --destination-port 67 --jump ACCEPT
Oct  8 09:17:20 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth9 --jump REJECT
Oct  8 09:17:21 hw2-ubuntu-work avahi-daemon[1118]: Joining mDNS multicast group on interface eth19.IPv6 with address fe80::beae:c5ff:fedb:b04.
Oct  8 09:17:21 hw2-ubuntu-work avahi-daemon[1118]: New relevant interface eth19.IPv6 for mDNS.
Oct  8 09:17:21 hw2-ubuntu-work avahi-daemon[1118]: Registering new address record for fe80::beae:c5ff:fedb:b04 on eth19.*.
Oct  8 09:17:21 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface eth9 --jump REJECT
Oct  8 09:17:21 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface eth9 --out-interface eth9 --jump ACCEPT
Oct  8 09:17:21 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface eth9 --jump ACCEPT
Oct  8 09:17:21 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface eth9 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Oct  8 09:17:21 hw2-ubuntu-work avahi-daemon[1118]: Joining mDNS multicast group on interface eth9.IPv6 with address fe80::206:4fff:fe4e:8586.
Oct  8 09:17:21 hw2-ubuntu-work avahi-daemon[1118]: New relevant interface eth9.IPv6 for mDNS.
Oct  8 09:17:21 hw2-ubuntu-work avahi-daemon[1118]: Registering new address record for fe80::206:4fff:fe4e:8586 on eth9.*.
Oct  8 09:17:21 hw2-ubuntu-work NetworkManager[1117]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 ! --destination 10.42.43.0/255.255.255.0 --jump MASQUERADE
Oct  8 09:17:21 hw2-ubuntu-work NetworkManager[1117]: <info> Starting dnsmasq...
Oct  8 09:17:22 hw2-ubuntu-work NetworkManager[1117]: <info> (eth9): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct  8 09:17:22 hw2-ubuntu-work dnsmasq[1942]: started, version 2.57 cachesize 150
Oct  8 09:17:22 hw2-ubuntu-work dnsmasq[1942]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP IDN
Oct  8 09:17:22 hw2-ubuntu-work dnsmasq-dhcp[1942]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Oct  8 09:17:22 hw2-ubuntu-work dnsmasq[1942]: no servers found in /etc/resolv.conf, will retry
Oct  8 09:17:22 hw2-ubuntu-work dnsmasq[1942]: cleared cache
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth9) successful, device activated.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth9) Stage 5 of 5 (IP Configure Commit) complete.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth9) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> (eth19): carrier now ON (device state 20)
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> (eth19): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Oct  8 09:17:24 hw2-ubuntu-work dbus[1105]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Auto-activating connection 'connessione_scrivania'.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) starting connection 'connessione_scrivania'
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> (eth19): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 1 of 5 (Device Prepare) scheduled...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <warn> bluez error getting default adapter: No such adapter
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 1 of 5 (Device Prepare) started...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 2 of 5 (Device Configure) scheduled...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 1 of 5 (Device Prepare) complete.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 2 of 5 (Device Configure) starting...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> (eth19): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 2 of 5 (Device Configure) successful.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 2 of 5 (Device Configure) complete.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 3 of 5 (IP Configure Start) started...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> (eth19): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 3 of 5 (IP Configure Start) complete.
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 4 of 5 (IP4 Configure Get) started...
Oct  8 09:17:24 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 5 of 5 (IP Configure Commit) started...
Oct  8 09:17:24 hw2-ubuntu-work avahi-daemon[1118]: Joining mDNS multicast group on interface eth19.IPv4 with address 192.168.1.2.
Oct  8 09:17:24 hw2-ubuntu-work avahi-daemon[1118]: New relevant interface eth19.IPv4 for mDNS.
Oct  8 09:17:24 hw2-ubuntu-work avahi-daemon[1118]: Registering new address record for 192.168.1.2 on eth19.IPv4.
Oct  8 09:17:24 hw2-ubuntu-work dbus[1105]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  8 09:17:26 hw2-ubuntu-work kernel: [   44.112008] ham0: no IPv6 routers present
Oct  8 09:17:28 hw2-ubuntu-work NetworkManager[1117]: <info> (eth19): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct  8 09:17:28 hw2-ubuntu-work kernel: [   45.552464] init: plymouth-stop pre-start process (1970) terminated with status 1
Oct  8 09:17:28 hw2-ubuntu-work dnsmasq[1942]: reading /etc/resolv.conf
Oct  8 09:17:28 hw2-ubuntu-work dnsmasq[1942]: using nameserver 192.168.1.1#53
Oct  8 09:17:28 hw2-ubuntu-work dnsmasq[1942]: cleared cache
Oct  8 09:17:29 hw2-ubuntu-work NetworkManager[1117]: <info> Policy set 'connessione_scrivania' (eth19) as default for IPv4 routing and DNS.
Oct  8 09:17:29 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) successful, device activated.
Oct  8 09:17:29 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 5 of 5 (IP Configure Commit) complete.
Oct  8 09:17:29 hw2-ubuntu-work NetworkManager[1117]: <info> Activation (eth19) Stage 4 of 5 (IP4 Configure Get) complete.
Oct  8 09:17:30 hw2-ubuntu-work kernel: [   47.200016] eth19: no IPv6 routers present
Oct  8 09:17:30 hw2-ubuntu-work kernel: [   47.552007] eth9: no IPv6 routers present
Oct  8 09:17:33 hw2-ubuntu-work gnome-session[1581]: WARNING: Failed to start app: Unable to start application: Esecuzione del processo figlio "gnome-power-manager" non riuscita (File o directory non esistente)
Oct  8 09:17:33 hw2-ubuntu-work dbus[1105]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Oct  8 09:17:33 hw2-ubuntu-work dbus[1105]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Successfully called chroot.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Successfully dropped privileges.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Successfully limited resources.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Running.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Watchdog thread running.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Canary thread running.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2100 of process 2100 (n/a) owned by '106' high priority at nice level -11.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 1 threads of 1 processes of 1 users.
Oct  8 09:17:33 hw2-ubuntu-work gdm-session-worker[2106]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Oct  8 09:17:33 hw2-ubuntu-work dbus[1105]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Oct  8 09:17:33 hw2-ubuntu-work dbus[1105]: [system] Successfully activated service 'org.freedesktop.Accounts'
Oct  8 09:17:33 hw2-ubuntu-work accounts-daemon[2108]: started daemon version 0.6.14
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2110 of process 2100 (n/a) owned by '106' RT at priority 5.
Oct  8 07:17:33 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 2 threads of 1 processes of 1 users.
Oct  8 07:17:34 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2128 of process 2100 (n/a) owned by '106' RT at priority 5.
Oct  8 07:17:34 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 3 threads of 1 processes of 1 users.
Oct  8 07:17:34 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2129 of process 2100 (n/a) owned by '106' RT at priority 5.
Oct  8 07:17:34 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 4 threads of 1 processes of 1 users.
Oct  8 07:17:35 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2132 of process 2132 (n/a) owned by '106' high priority at nice level -11.
Oct  8 07:17:35 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 5 threads of 2 processes of 1 users.
Oct  8 09:17:35 hw2-ubuntu-work pulseaudio[2132]: [pulseaudio] pid.c: Daemon already running.
Oct  8 09:17:35 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-WARNING: Overriding tab label for notebook
Oct  8 09:17:36  gdm-simple-greeter[2088]: last message repeated 4 times
Oct  8 09:17:35 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-WARNING: /build/buildd/gtk+3.0-3.2.0/./gtk/gtkwidget.c:6857: widget not within a GtkWindow
Oct  8 09:17:36 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  8 09:17:36 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height -3
Oct  8 09:17:36 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  8 09:17:36 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-CRITICAL: gtk_widget_get_preferred_height_for_width: assertion `width >= 0' failed
Oct  8 09:17:36 hw2-ubuntu-work gdm-simple-greeter[2088]: Gtk-WARNING: gtk_widget_size_allocate(): attempt to allocate widget with width -47 and height -47
Oct  8 09:17:39 hw2-ubuntu-work ntpdate[1967]: step time server 91.189.94.4 offset -1.133025 sec
Oct  8 09:17:40 hw2-ubuntu-work gdm-simple-greeter[2088]: Gdk-CRITICAL: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed
Oct  8 07:17:44 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2309 of process 2309 (n/a) owned by '1000' high priority at nice level -11.
Oct  8 07:17:44 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 5 threads of 2 processes of 2 users.
Oct  8 07:17:44 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2312 of process 2309 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:17:44 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 6 threads of 2 processes of 2 users.
Oct  8 07:17:45 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2313 of process 2309 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:17:45 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 7 threads of 2 processes of 2 users.
Oct  8 07:17:45 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2314 of process 2309 (n/a) owned by '1000' RT at priority 5.
Oct  8 07:17:45 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 8 threads of 2 processes of 2 users.
Oct  8 07:17:45 hw2-ubuntu-work rtkit-daemon[2103]: Successfully made thread 2317 of process 2317 (n/a) owned by '1000' high priority at nice level -11.
Oct  8 07:17:45 hw2-ubuntu-work rtkit-daemon[2103]: Supervising 9 threads of 3 processes of 2 users.
Oct  8 09:17:45 hw2-ubuntu-work pulseaudio[2317]: [pulseaudio] pid.c: Daemon already running.
Oct  8 09:17:48 hw2-ubuntu-work gnome-session[2183]: WARNING: Failed to start app: Unable to start application: Esecuzione del processo figlio "dropbox" non riuscita (File o directory non esistente)
Oct  8 09:17:48 hw2-ubuntu-work nautilus: [N-A] Nautilus-Actions Tracker 3.2.2 initializing...
Oct  8 09:17:53 hw2-ubuntu-work nautilus: [N-A] Nautilus-Actions Menu Extender 3.2.2 initializing...
Oct  8 09:17:53 hw2-ubuntu-work ntpdate[2327]: adjust time server 91.189.94.4 offset -0.000747 sec
Oct  8 09:17:59 hw2-ubuntu-work dbus[1105]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Oct  8 09:18:00 hw2-ubuntu-work dbus[1105]: [system] Successfully activated service 'org.freedesktop.UDisks'
Oct  8 09:18:02 hw2-ubuntu-work kernel: [   80.386825] show_signal_msg: 51 callbacks suppressed
Oct  8 09:18:02 hw2-ubuntu-work kernel: [   80.386829] pulseaudio[2100]: segfault at 34 ip b0ed445a sp bff39d30 error 4 in module-loopback.so[b0ed2000+7000]
Oct  8 09:18:31 hw2-ubuntu-work kernel: [  109.741695] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
Oct  8 09:19:16 hw2-ubuntu-work dnsmasq[1942]: reading /etc/resolv.conf
Oct  8 09:19:16 hw2-ubuntu-work dnsmasq[1942]: using nameserver 192.168.1.1#53
Oct  8 09:19:16 hw2-ubuntu-work dnsmasq[1942]: cleared cache
Oct  8 09:19:23 hw2-ubuntu-work goa[2648]: goa-daemon version 3.2.1 starting [main.c:112, main()]
Oct  8 09:19:32 hw2-ubuntu-work dbus[1105]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Oct  8 09:19:32 hw2-ubuntu-work dbus[1105]: [system] Successfully activated service 'com.ubuntu.SystemService'
Oct  8 09:20:04 hw2-ubuntu-work kernel: [  203.084622] eth9: Link down
Oct  8 09:20:08 hw2-ubuntu-work kernel: [  206.380425] eth9: Link up
Oct  8 09:20:08 hw2-ubuntu-work kernel: [  206.380910] eth9: Link changed: 100Mbps, full duplex

you can see that the time jumps from 80" to 200" ...it's impressive slow :(

> Oct  8 09:17:30 hw2-ubuntu-work kernel: [   47.552007] eth9: no IPv6 routers present
Oct  8 09:18:02 hw2-ubuntu-work kernel: [   80.386825] show_signal_msg: 51 callbacks suppressed
Oct  8 09:18:02 hw2-ubuntu-work kernel: [   80.386829] pulseaudio[2100]: segfault at 34 ip b0ed445a sp bff39d30 error 4 in module-loopback.so[b0ed2000+7000]
Oct  8 09:18:31 hw2-ubuntu-work kernel: [  109.741695] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro,commit=0
Oct  8 09:20:04 hw2-ubuntu-work kernel: [  203.084622] eth9: Link down
Oct  8 09:20:08 hw2-ubuntu-work kernel: [  206.380425] eth9: Link up
Oct  8 09:20:08 hw2-ubuntu-work kernel: [  206.380910] eth9: Link changed: 100Mbps, full duplex

can someone help me? 

thanks in advance

---

