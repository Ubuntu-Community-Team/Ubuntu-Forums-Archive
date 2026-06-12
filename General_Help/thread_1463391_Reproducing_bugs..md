---
title: "Reproducing bugs."
date: 2010-04-26
forum: General Help
---

### Post by jwbrase on 2010-04-26
I've been getting a segfault bug in Opera (apparently the plugin wrapper from the log surrounding the latest crash) that's been corrupting my display and necessitating an X restart when it happens (I'll get a pause, all my windows and my desktop will go scrambled, often showing images from sites I had visited previously, and the system will bog down. Ctrl-Alt-Backspace generally fixes things). However, I've not been able to really figure out a good way of reproducing the bug. It just happens randomly from time to time so that I have to be careful about how long I let Opera run. Does anyone know of a good way to flush bugs out that generally occur once in a few hundred hours of run time? (Other than just waiting a long time for them to happen). For example, some way to exacerbate the instability that's at the root of a bug so that it shows itself?

System logs from the latest crash:


daemon.log
```
Apr 27 02:36:29 system76-pc NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Apr 27 02:36:29 system76-pc NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Apr 27 02:36:29 system76-pc gdm[3861]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr 27 02:36:29 system76-pc NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 14541 
Apr 27 02:36:29 system76-pc NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Apr 27 02:36:29 system76-pc avahi-daemon[3905]: Withdrawing address record for 10.0.0.212 on wlan0.
Apr 27 02:36:29 system76-pc avahi-daemon[3905]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.212.
Apr 27 02:36:29 system76-pc avahi-daemon[3905]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 27 02:36:29 system76-pc nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Apr 27 02:36:31 system76-pc console-kit-daemon[3664]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
Apr 27 02:36:31 system76-pc console-kit-daemon[3664]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Apr 27 02:36:31 system76-pc console-kit-daemon[3664]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Apr 27 02:36:32 system76-pc acpid: client 3866[0:0] has disconnected 
Apr 27 02:36:32 system76-pc acpid: client 3866[0:0] has disconnected 
```

kern.log (I'm not sure that the NVRM stuff is relevant, but I'm including it just in case as it was within 20 seconds of the crash).
```

Apr 27 02:36:10 system76-pc kernel: [44152.777045] NVRM: Xid (0001:00): 8, Channel 00000001
Apr 27 02:36:11 system76-pc kernel: [44152.814169] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 000002e8 00000002 00000100
Apr 27 02:36:11 system76-pc kernel: [44152.842971] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 0000024c 00000026 00000140
Apr 27 02:36:11 system76-pc kernel: [44152.877467] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 0000024c 00000026 00000140
Apr 27 02:36:11 system76-pc kernel: [44152.909486] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 0000024c 00000026 00000140
Apr 27 02:36:11 system76-pc kernel: [44152.943819] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 0000024c 00000026 00000140
Apr 27 02:36:11 system76-pc kernel: [44152.978352] NVRM: Xid (0001:00): 13, 0001 00000000 0000502d 0000024c 00000026 00000100
Apr 27 02:36:29 system76-pc kernel: [44171.365571] operapluginwrap[8262]: segfault at f50fe030 ip 00000000f730a9e0 sp 00000000ffcd4214 error 4 in libpthread-2.9.so[f7303000+15000]

```

messages:
```

Apr 27 02:36:29 system76-pc kernel: [44171.365571] operapluginwrap[8262]: segfault at f50fe030 ip 00000000f730a9e0 sp 00000000ffcd4214 error 4 in libpthread-2.9.so[f7303000+15000]
Apr 27 02:36:29 system76-pc bonobo-activation-server (jon-21464): could not associate with desktop session: Failed to connect to socket /tmp/dbus-UcFKlnmGGC: Connection refused

```

---

