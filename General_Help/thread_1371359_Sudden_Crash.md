---
title: "Sudden Crash"
date: 2010-01-03
forum: General Help
---

### Post by riversoto on 2010-01-03
I've been using ubuntu for a couple of years, but lately my system has suddenly crashed, unexpectedly the session with all the open applications was closed and the system started from scratch, anyone can please indicate me which log to examine to determine what it's going wrong. 
This is a typical problem for windows users, but cannot be happening with Ubuntu!!! 
Thanx in advance.-

---

### Post by Bobulous on 2010-01-03
Poke around in /var/log and examine files such as /var/log/messages (and archived logs such as messages.1 etc).

Note that it's normal to get a lot of stuff generated into logfiles, even if the machine doesn't crash, so you'll have to look for the exact time range when the problem occurred. (I can see two "segfault" errors listed in messages for the last ten minutes, both caused by Gnote crashing.)

If the crash is very sudden, and not caused by Ubuntu, you may have hardware faults (such as power supply failure, RAM faults, etc), as these can bring a machine down suddenly and often.

---

### Post by riversoto on 2010-01-10
Thanks for your reply Bobulous, I've checked several logs, because I had the problem again but this time I could register the minute.
This is the Crash (22:29) any idea? i don't have such an expert eye:

var/log/daemon.log
Jan 10 22:28:18 laptop console-kit-daemon[1144]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Jan 10 22:28:18 laptop console-kit-daemon[1144]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan 10 22:28:18 laptop console-kit-daemon[1144]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Jan 10 22:28:21 laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 10 22:28:23 laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jan 10 22:28:23 laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Jan 10 22:28:34 laptop NetworkManager: <debug> [1263133714.000781] ensure_killed(): waiting for vpn service pid 1992 to exit
Jan 10 22:28:34 laptop NetworkManager: <debug> [1263133714.000881] ensure_killed(): vpn service pid 1992 cleaned up
Jan 10 22:28:45 laptop wpa_supplicant[1222]: CTRL-EVENT-SCAN-RESULTS 
Jan 10 22:29:32 laptop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Jan 10 22:29:32 laptop NetworkManager: <info>  (eth1): taking down device.
Jan 10 22:29:33 laptop avahi-daemon[1210]: Got SIGTERM, quitting.


var/log/syslog
Jan 10 22:28:18 laptop console-kit-daemon[1144]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Jan 10 22:28:18 laptop console-kit-daemon[1144]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan 10 22:28:18 laptop console-kit-daemon[1144]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Jan 10 22:28:21 laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 10 22:28:23 laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jan 10 22:28:23 laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Jan 10 22:28:28 laptop bonobo-activation-server (yerco-6428): could not associate with desktop session: Failed to connect to socket /tmp/dbus-IKB9dLdoCy: Conexión rechazada
Jan 10 22:28:34 laptop NetworkManager: <debug> [1263133714.000781] ensure_killed(): waiting for vpn service pid 1992 to exit
Jan 10 22:28:34 laptop NetworkManager: <debug> [1263133714.000881] ensure_killed(): vpn service pid 1992 cleaned up
Jan 10 22:28:45 laptop wpa_supplicant[1222]: CTRL-EVENT-SCAN-RESULTS 
Jan 10 22:29:32 laptop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Jan 10 22:29:32 laptop NetworkManager: <info>  (eth1): taking down device.
Jan 10 22:29:33 laptop avahi-daemon[1210]: Got SIGTERM, quitting.
Jan 10 22:29:33 laptop kernel: Kernel logging (proc) stopped.

var/log/messages
Jan 10 22:28:28 laptop bonobo-activation-server (yerco-6428): could not associate with desktop session: Failed to connect to socket /tmp/dbus-IKB9dLdoCy: Conexión rechazada
Jan 10 22:29:33 laptop kernel: Kernel logging (proc) stopped.

---

