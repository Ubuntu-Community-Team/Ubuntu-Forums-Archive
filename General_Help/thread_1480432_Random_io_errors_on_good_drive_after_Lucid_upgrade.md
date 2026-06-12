---
title: "Random i/o errors on good drive after Lucid upgrade"
date: 2010-05-11
forum: General Help
---

### Post by Castarmax on 2010-05-11
Hope these are the logs thats needed and that Ive posted them in the proper manner.
Problem is I'm having random i/o errors and the system freezes after I upgraded from 9.04 to Lucid
Here is part of my syslog and the others are large so I compressed them.

May 11 16:15:47 john-desktop polkitd[1279]: started daemon version 0.96 using authority implementation `local' version `0.96'
May 11 16:15:47 john-desktop anacron[1302]: Anacron 2.3 started on 2010-05-11
May 11 16:15:47 john-desktop anacron[1302]: Normal exit (0 jobs run)
May 11 16:15:48 john-desktop kernel: [   54.274220] 0000:01:06.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
May 11 16:15:48 john-desktop kernel: [   54.274230] eth2: Setting full-duplex based on MII#1 link partner capability of 45e1.
May 11 16:15:48 john-desktop gdm-simple-greeter[1245]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
May 11 16:15:48 john-desktop init: plymouth-stop pre-start process (1407) terminated with status 1
May 11 16:15:48 john-desktop acpid: client connected from 1421[111:122]
May 11 16:15:48 john-desktop acpid: 1 client rule loaded
May 11 16:15:49 john-desktop dhclient: DHCPREQUEST of 192.168.0.3 on eth2 to 255.255.255.255 port 67
May 11 16:15:49 john-desktop dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May 11 16:15:49 john-desktop dhclient: bound to 192.168.0.3 -- renewal in 35369 seconds.
May 11 16:15:49 john-desktop NetworkManager: <info>  DHCP: device eth2 state changed preinit -> reboot
May 11 16:15:49 john-desktop NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Get) scheduled...
May 11 16:15:49 john-desktop NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Get) started...
May 11 16:15:49 john-desktop NetworkManager: <info>    address 192.168.0.3
May 11 16:15:49 john-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
May 11 16:15:49 john-desktop NetworkManager: <info>    gateway 192.168.0.1
May 11 16:15:49 john-desktop NetworkManager: <info>    nameserver '192.168.2.1'
May 11 16:15:49 john-desktop NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) scheduled...
May 11 16:15:49 john-desktop NetworkManager: <info>  Activation (eth2) Stage 4 of 5 (IP4 Configure Get) complete.
May 11 16:15:49 john-desktop NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) started...
May 11 16:15:49 john-desktop avahi-daemon[869]: Joining mDNS multicast group on interface eth2.IPv4 with address 192.168.0.3.
May 11 16:15:49 john-desktop avahi-daemon[869]: New relevant interface eth2.IPv4 for mDNS.
May 11 16:15:49 john-desktop avahi-daemon[869]: Registering new address record for 192.168.0.3 on eth2.IPv4.
May 11 16:15:50 john-desktop NetworkManager: <info>  (eth2): device state change: 7 -> 8 (reason 0)
May 11 16:15:50 john-desktop NetworkManager: <info>  Policy set 'Auto eth2' (eth2) as default for routing and DNS.
May 11 16:15:50 john-desktop NetworkManager: <info>  Activation (eth2) successful, device activated.
May 11 16:15:50 john-desktop NetworkManager: <info>  Activation (eth2) Stage 5 of 5 (IP Configure Commit) complete.
May 11 16:15:50 john-desktop gdm-session-worker[1246]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
May 11 16:15:55 john-desktop ntpdate[1465]: step time server 91.189.94.4 offset 4.792863 sec
May 11 16:15:59 john-desktop gnome-session[1496]: EggSMClient-WARNING: Desktop file '/home/john/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
May 11 16:16:00 john-desktop gnome-session[1496]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory)
May 11 16:16:00 john-desktop kernel: [   61.492508] eth2: no IPv6 routers present
May 11 16:16:02 john-desktop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
May 11 16:16:02 john-desktop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
May 11 16:16:12 john-desktop kernel: [   73.852400] end_request: I/O error, dev fd0, sector 0
May 11 16:16:24 john-desktop kernel: [   86.020787] end_request: I/O error, dev fd0, sector 0
May 11 16:17:02 john-desktop CRON[1841]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 11 16:17:04 john-desktop AptDaemon: INFO: Initializing daemon
May 11 16:22:05 john-desktop AptDaemon: INFO: Quiting due to inactivity
May 11 16:22:05 john-desktop AptDaemon: INFO: Shutdown was requested

---

### Post by dcstar on 2010-05-11
> **Castarmax said:**
> Hope these are the logs thats needed and that Ive posted them in the proper manner.
Problem is I'm having random i/o errors and the system freezes after I upgraded from 9.04 to Lucid
Here is part of my syslog and the others are large so I compressed them.
........

[LIST=1]
[*]Upgrades are always problematical, save your data and do a fresh install.
[*]People are not goings to trawl through masses of log files to try and find your problem, you provide some specific things and then you might get some useful ideas.
[/LIST]

---

