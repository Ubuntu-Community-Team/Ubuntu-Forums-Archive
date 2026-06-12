---
title: "random logout issue in ubuntu 9.10"
date: 2010-08-18
forum: General Help
---

### Post by mr clark25 on 2010-08-18
whenever i give my hard drive a heavy workload, my computer logs me out after about 10-30 seconds.

i have always worked around it untill now. i have a friend that needs some files off a hard drive that i pulled out of their broken laptop, and moved to a external (usb) drive. now, when i try to copy the files to the external drive, i get logged out after about 50 megs are copied. (about 10 seconds)

this happens when copying to/from my current hard drive, and the laptop hard drive.

here are the last couple lines of /var/log/auth.log, right after i got logged out twice.
```

ug 18 17:25:01 clark-desktop CRON[14706]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 17:25:01 clark-desktop CRON[14706]: pam_unix(cron:session): session closed for user root
Aug 18 17:35:01 clark-desktop CRON[14713]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 17:35:01 clark-desktop CRON[14713]: pam_unix(cron:session): session closed for user root
Aug 18 17:39:01 clark-desktop CRON[14716]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 17:39:01 clark-desktop CRON[14716]: pam_unix(cron:session): session closed for user root
Aug 18 17:45:01 clark-desktop CRON[14724]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 17:45:01 clark-desktop CRON[14724]: pam_unix(cron:session): session closed for user root
Aug 18 18:02:35 clark-desktop gdm-session-worker[1978]: pam_unix(gdm-autologin:session): session opened for user james by (uid=0)
Aug 18 18:02:35 clark-desktop gdm-session-worker[1978]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Aug 18 18:02:38 clark-desktop seahorse-daemon[2496]: init gpgme version 1.1.8
Aug 18 18:05:01 clark-desktop CRON[2894]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 18:05:01 clark-desktop CRON[2894]: pam_unix(cron:session): session closed for user root
Aug 18 18:06:45 clark-desktop gnome-keyring-daemon[2493]: GVFS-RemoteVolumeMonitor: Owner :1.53 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
Aug 18 18:06:45 clark-desktop gnome-keyring-daemon[2493]: GVFS-RemoteVolumeMonitor: Owner :1.54 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts
Aug 18 18:06:45 clark-desktop gdm-session-worker[1978]: pam_unix(gdm-autologin:session): session closed for user james
Aug 18 18:07:07 clark-desktop gdm-session-worker[3047]: pam_unix(gdm:session): session opened for user james by (uid=0)
Aug 18 18:07:07 clark-desktop gdm-session-worker[3047]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Aug 18 18:07:09 clark-desktop seahorse-daemon[3176]: init gpgme version 1.1.8
Aug 18 18:09:01 clark-desktop CRON[3520]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 18:09:01 clark-desktop CRON[3520]: pam_unix(cron:session): session closed for user root
Aug 18 18:09:21 clark-desktop gdm-session-worker[3506]: pam_unix(gdm:session): session opened for user james by (uid=0)
Aug 18 18:09:21 clark-desktop gdm-session-worker[3506]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Aug 18 18:09:24 clark-desktop seahorse-daemon[3644]: init gpgme version 1.1.8
Aug 18 18:15:02 clark-desktop CRON[3963]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 18 18:15:02 clark-desktop CRON[3963]: pam_unix(cron:session): session closed for user root

```

current user: james
computer name: clark-desktop.


here are the last couple lines of /var/log/syslog:
```

Aug 18 18:02:37 clark-desktop kernel: [   36.814393] CPU0 attaching NULL sched-domain.
Aug 18 18:02:37 clark-desktop kernel: [   36.814399] CPU1 attaching NULL sched-domain.
Aug 18 18:02:37 clark-desktop kernel: [   36.832075] CPU0 attaching sched-domain:
Aug 18 18:02:37 clark-desktop kernel: [   36.832080]  domain 0: span 0-1 level MC
Aug 18 18:02:37 clark-desktop kernel: [   36.832083]   groups: 0 1
Aug 18 18:02:37 clark-desktop kernel: [   36.832089] CPU1 attaching sched-domain:
Aug 18 18:02:37 clark-desktop kernel: [   36.832092]  domain 0: span 0-1 level MC
Aug 18 18:02:37 clark-desktop kernel: [   36.832094]   groups: 1 0
Aug 18 18:02:37 clark-desktop kernel: [   36.974434] usb 2-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Aug 18 18:02:37 clark-desktop kernel: [   36.974470] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Aug 18 18:02:38 clark-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Aug 18 18:02:38 clark-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Aug 18 18:02:38 clark-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
Aug 18 18:02:38 clark-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 18 18:02:38 clark-desktop ntpd[2059]: ntpd exiting on signal 15
Aug 18 18:02:39 clark-desktop ntpdate[2554]: adjust time server 91.189.94.4 offset 0.009603 sec
Aug 18 18:02:39 clark-desktop ntpd[2654]: ntpd 4.2.4p6@1.1549-o Fri Dec  4 18:08:42 UTC 2009 (1)
Aug 18 18:02:39 clark-desktop ntpd[2655]: precision = 1.000 usec
Aug 18 18:02:39 clark-desktop ntpd[2655]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 18 18:02:39 clark-desktop ntpd[2655]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 18 18:02:39 clark-desktop ntpd[2655]: Listening on interface #2 lo, ::1#123 Enabled
Aug 18 18:02:39 clark-desktop ntpd[2655]: Listening on interface #3 eth0, fe80::219:d1ff:fe30:e96#123 Enabled
Aug 18 18:02:39 clark-desktop ntpd[2655]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 18 18:02:39 clark-desktop ntpd[2655]: Listening on interface #5 eth0, 192.168.1.8#123 Enabled
Aug 18 18:02:39 clark-desktop ntpd[2655]: kernel time sync status 2040
Aug 18 18:02:39 clark-desktop ntpd[2655]: frequency initialized -148.709 PPM from /var/lib/ntp/ntp.drift
Aug 18 18:02:39 clark-desktop udev-configure-printer: SERN fields match
Aug 18 18:02:39 clark-desktop udev-configure-printer: URI match: hp:/usb/Deskjet_F4200_series?serial=CN8732N1KZ05BR
Aug 18 18:02:39 clark-desktop udev-configure-printer: SERN fields match
Aug 18 18:02:39 clark-desktop udev-configure-printer: URI match: usb://HP/Deskjet%20F4200%20series?serial=CN8732N1KZ05BR
Aug 18 18:02:39 clark-desktop udev-configure-printer: Failed to get parent
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-4
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 413C:5117
Aug 18 18:02:39 clark-desktop udev-configure-printer: failed to claim interface
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb5
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.3
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 046D:C517
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb6
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0002
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb6
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb6/6-1
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 0471:0815
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: Failed to get parent
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb7
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0001
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0002
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0002
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-4
Aug 18 18:02:39 clark-desktop udev-configure-printer: Device vendor/product is 413C:5117
Aug 18 18:02:39 clark-desktop udev-configure-printer: failed to claim interface
Aug 18 18:02:39 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:39 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-4
Aug 18 18:02:39 clark-desktop udev-configure-printer: MFG:Dell MDL: Photo AIO Printer 966 SERN:- serial:42PKG91
Aug 18 18:02:40 clark-desktop kernel: [   40.051718] usb 2-4: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Aug 18 18:02:40 clark-desktop kernel: [   40.051754] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Aug 18 18:02:41 clark-desktop pulseaudio[2144]: ratelimit.c: 1 events suppressed
Aug 18 18:02:42 clark-desktop udev-configure-printer: URI matches without serial number: usb://Dell/Photo%20AIO%20Printer%20966
Aug 18 18:02:42 clark-desktop udev-configure-printer: No serial number URI matches so using those without
Aug 18 18:02:42 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2
Aug 18 18:02:42 clark-desktop udev-configure-printer: Device vendor/product is 1D6B:0002
Aug 18 18:02:42 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:42 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.3
Aug 18 18:02:42 clark-desktop udev-configure-printer: Device vendor/product is 046D:C517
Aug 18 18:02:42 clark-desktop udev-configure-printer: About to add queue for usb://Dell/Photo%20AIO%20Printer%20966
Aug 18 18:02:42 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:42 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-4
Aug 18 18:02:42 clark-desktop udev-configure-printer: last message repeated 2 times
Aug 18 18:02:42 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-1
Aug 18 18:02:42 clark-desktop udev-configure-printer: Failed to get parent
Aug 18 18:02:42 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-2
Aug 18 18:02:42 clark-desktop udev-configure-printer: Device vendor/product is 0644:0200
Aug 18 18:02:42 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:42 clark-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-5
Aug 18 18:02:42 clark-desktop udev-configure-printer: Device vendor/product is 0424:2504
Aug 18 18:02:42 clark-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Aug 18 18:02:42 clark-desktop udev-add-printer: add_queue: URIs=['usb://Dell/Photo%20AIO%20Printer%20966']
Aug 18 18:02:42 clark-desktop udev-add-printer: D-Bus method call failed: org.freedesktop.DBus.Error.ServiceUnknown: The name com.redhat.NewPrinterNotification was not provided by any .service files
Aug 18 18:02:45 clark-desktop kernel: [   44.800093] eth0: no IPv6 routers present
Aug 18 18:03:13 clark-desktop udev-add-printer: PPD: lsb/usr/cups-included/textonly.ppd; Status: 3
Aug 18 18:03:34 clark-desktop postfix/sendmail[2843]: fatal: open /etc/postfix/main.cf: No such file or directory
Aug 18 18:03:35 clark-desktop postfix/sendmail[2847]: fatal: open /etc/postfix/main.cf: No such file or directory
Aug 18 18:03:35 clark-desktop ntfs-3g[2851]: Version 2009.4.4 external FUSE 27
Aug 18 18:03:35 clark-desktop ntfs-3g[2851]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1)
Aug 18 18:03:35 clark-desktop ntfs-3g[2851]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Aug 18 18:03:35 clark-desktop ntfs-3g[2851]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Aug 18 18:04:00 clark-desktop kernel: [  120.359561] __ratelimit: 6 callbacks suppressed
Aug 18 18:04:00 clark-desktop kernel: [  120.359565] type=1503 audit(1282172640.636:26): operation="open" pid=2891 parent=2889 profile="/usr/bin/evince-thumbnailer" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F304632423433454233334344463731452F4D7920446F63756D656E74732F50425320426F6F6B6D61726B
Aug 18 18:04:00 clark-desktop kernel: [  120.437997] type=1503 audit(1282172640.716:27): operation="open" pid=2891 parent=2889 profile="/usr/bin/evince-thumbnailer" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name=2F6D656469612F304632423433454233334344463731452F4D7920446F63756D656E74732F50425320426F6F6B6D61726B
Aug 18 18:05:01 clark-desktop CRON[2895]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Aug 18 18:05:04 clark-desktop kernel: [  184.056023] usb 1-3: new high speed USB device using ehci_hcd and address 3
Aug 18 18:05:04 clark-desktop kernel: [  184.193089] usb 1-3: configuration #1 chosen from 1 choice
Aug 18 18:05:04 clark-desktop kernel: [  184.197073] scsi8 : SCSI emulation for USB Mass Storage devices
Aug 18 18:05:04 clark-desktop kernel: [  184.198997] usb-storage: device found at 3
Aug 18 18:05:04 clark-desktop kernel: [  184.199001] usb-storage: waiting for device to settle before scanning
Aug 18 18:05:09 clark-desktop kernel: [  189.196248] usb-storage: device scan complete
Aug 18 18:05:09 clark-desktop kernel: [  189.196740] scsi 8:0:0:0: Direct-Access     ST925031 5AS                   PQ: 0 ANSI: 2 CCS
Aug 18 18:05:09 clark-desktop kernel: [  189.197352] sd 8:0:0:0: Attached scsi generic sg8 type 0
Aug 18 18:05:09 clark-desktop kernel: [  189.202842] sd 8:0:0:0: [sdh] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Aug 18 18:05:09 clark-desktop kernel: [  189.203582] sd 8:0:0:0: [sdh] Write Protect is off
Aug 18 18:05:09 clark-desktop kernel: [  189.203587] sd 8:0:0:0: [sdh] Mode Sense: 28 00 00 00
Aug 18 18:05:09 clark-desktop kernel: [  189.203591] sd 8:0:0:0: [sdh] Assuming drive cache: write through
Aug 18 18:05:09 clark-desktop kernel: [  189.206902] sd 8:0:0:0: [sdh] Assuming drive cache: write through
Aug 18 18:05:09 clark-desktop kernel: [  189.206909]  sdh: sdh1
Aug 18 18:05:09 clark-desktop kernel: [  189.275334] sd 8:0:0:0: [sdh] Assuming drive cache: write through
Aug 18 18:05:09 clark-desktop kernel: [  189.275342] sd 8:0:0:0: [sdh] Attached SCSI disk
Aug 18 18:05:11 clark-desktop ntfs-3g[2927]: Version 2009.4.4 external FUSE 27
Aug 18 18:05:11 clark-desktop ntfs-3g[2927]: Mounted /dev/sdh1 (Read-Write, label "Iomega_HDD", NTFS 3.1)
Aug 18 18:05:11 clark-desktop ntfs-3g[2927]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Aug 18 18:05:11 clark-desktop ntfs-3g[2927]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sdh1,blkdev,blksize=4096
Aug 18 18:06:45 clark-desktop kernel: [  285.414152] Xorg: page allocation failure. order:4, mode:0x40d0
Aug 18 18:06:45 clark-desktop kernel: [  285.414160] Pid: 1824, comm: Xorg Not tainted 2.6.31-22-generic #60-Ubuntu
Aug 18 18:06:45 clark-desktop kernel: [  285.414164] Call Trace:
Aug 18 18:06:45 clark-desktop kernel: [  285.414175]  [<c0572d1c>] ? printk+0x18/0x1c
Aug 18 18:06:45 clark-desktop kernel: [  285.414183]  [<c01b84cc>] __alloc_pages_slowpath+0x45c/0x490
Aug 18 18:06:45 clark-desktop kernel: [  285.414191]  [<c01b860f>] __alloc_pages_nodemask+0x10f/0x120
Aug 18 18:06:45 clark-desktop kernel: [  285.414197]  [<c01b8667>] __get_free_pages+0x17/0x30
Aug 18 18:06:45 clark-desktop kernel: [  285.414204]  [<c01e0d5f>] __kmalloc+0xdf/0x180
Aug 18 18:06:45 clark-desktop kernel: [  285.414211]  [<c0127b48>] ? default_spin_lock_flags+0x8/0x10
Aug 18 18:06:45 clark-desktop kernel: [  285.414240]  [<f86ace48>] radeon_cp_cmdbuf+0xa98/0xbf0 [radeon]
Aug 18 18:06:45 clark-desktop kernel: [  285.414266]  [<f82888e2>] ? drm_lock+0x252/0x350 [drm]
Aug 18 18:06:45 clark-desktop kernel: [  285.414289]  [<f82856c0>] drm_ioctl+0x180/0x360 [drm]
Aug 18 18:06:45 clark-desktop kernel: [  285.414315]  [<f86ac3b0>] ? radeon_cp_cmdbuf+0x0/0xbf0 [radeon]
Aug 18 18:06:45 clark-desktop kernel: [  285.414323]  [<c015c160>] ? autoremove_wake_function+0x0/0x40
Aug 18 18:06:45 clark-desktop kernel: [  285.414330]  [<c01603b2>] ? hrtimer_start+0x22/0x30
Aug 18 18:06:45 clark-desktop kernel: [  285.414336]  [<c02cc6af>] ? security_file_permission+0xf/0x20
Aug 18 18:06:45 clark-desktop kernel: [  285.414344]  [<c01f5e93>] vfs_ioctl+0x73/0x90
Aug 18 18:06:45 clark-desktop kernel: [  285.414349]  [<c01f6161>] do_vfs_ioctl+0x71/0x310
Aug 18 18:06:45 clark-desktop kernel: [  285.414355]  [<c01f645f>] sys_ioctl+0x5f/0x80
Aug 18 18:06:45 clark-desktop kernel: [  285.414360]  [<c01033ac>] syscall_call+0x7/0xb
Aug 18 18:06:45 clark-desktop kernel: [  285.414364] Mem-Info:
Aug 18 18:06:45 clark-desktop kernel: [  285.414367] DMA per-cpu:
Aug 18 18:06:45 clark-desktop kernel: [  285.414371] CPU    0: hi:    0, btch:   1 usd:   0
Aug 18 18:06:45 clark-desktop kernel: [  285.414375] CPU    1: hi:    0, btch:   1 usd:   0
Aug 18 18:06:45 clark-desktop kernel: [  285.414378] Normal per-cpu:
Aug 18 18:06:45 clark-desktop kernel: [  285.414381] CPU    0: hi:  186, btch:  31 usd:   0
Aug 18 18:06:45 clark-desktop kernel: [  285.414385] CPU    1: hi:  186, btch:  31 usd: 146
Aug 18 18:06:45 clark-desktop kernel: [  285.414388] HighMem per-cpu:
Aug 18 18:06:45 clark-desktop kernel: [  285.414391] CPU    0: hi:  186, btch:  31 usd:   0
Aug 18 18:06:45 clark-desktop kernel: [  285.414394] CPU    1: hi:  186, btch:  31 usd:   0
Aug 18 18:06:45 clark-desktop kernel: [  285.414401] Active_anon:55303 active_file:26352 inactive_anon:4593
Aug 18 18:06:45 clark-desktop kernel: [  285.414403]  inactive_file:396353 unevictable:0 dirty:19010 writeback:5 unstable:0
Aug 18 18:06:45 clark-desktop kernel: [  285.414405]  free:5819 slab:13720 mapped:18675 pagetables:1314 bounce:0
Aug 18 18:06:45 clark-desktop kernel: [  285.414412] DMA free:3536kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:4kB inactive_file:4932kB unevictable:0kB present:15836kB pages_scanned:0 all_unreclaimable? no
Aug 18 18:06:45 clark-desktop kernel: [  285.414417] lowmem_reserve[]: 0 865 2014 2014
Aug 18 18:06:45 clark-desktop kernel: [  285.414428] Normal free:9000kB min:3728kB low:4660kB high:5592kB active_anon:0kB inactive_anon:0kB active_file:53688kB inactive_file:705256kB unevictable:0kB present:885944kB pages_scanned:129 all_unreclaimable? no
Aug 18 18:06:45 clark-desktop kernel: [  285.414433] lowmem_reserve[]: 0 0 9194 9194
Aug 18 18:06:45 clark-desktop kernel: [  285.414445] HighMem free:10740kB min:512kB low:1748kB high:2988kB active_anon:221084kB inactive_anon:18500kB active_file:51716kB inactive_file:875224kB unevictable:0kB present:1176856kB pages_scanned:64 all_unreclaimable? no
Aug 18 18:06:45 clark-desktop kernel: [  285.414450] lowmem_reserve[]: 0 0 0 0
Aug 18 18:06:45 clark-desktop kernel: [  285.414458] DMA: 2*4kB 1*8kB 0*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3536kB
Aug 18 18:06:45 clark-desktop kernel: [  285.414477] Normal: 1076*4kB 323*8kB 68*16kB 24*32kB 4*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 9000kB
Aug 18 18:06:45 clark-desktop kernel: [  285.414495] HighMem: 19*4kB 11*8kB 2*16kB 2*32kB 1*64kB 0*128kB 1*256kB 0*512kB 2*1024kB 4*2048kB 0*4096kB = 10820kB
Aug 18 18:06:45 clark-desktop kernel: [  285.414514] 424009 total pagecache pages
Aug 18 18:06:45 clark-desktop kernel: [  285.414517] 0 pages in swap cache
Aug 18 18:06:45 clark-desktop kernel: [  285.414520] Swap cache stats: add 0, delete 0, find 0/0
Aug 18 18:06:45 clark-desktop kernel: [  285.414523] Free swap  = 1461872kB
Aug 18 18:06:45 clark-desktop kernel: [  285.414526] Total swap = 1461872kB
Aug 18 18:06:45 clark-desktop kernel: [  285.421358] 523857 pages RAM
Aug 18 18:06:45 clark-desktop kernel: [  285.421364] 296531 pages HighMem
Aug 18 18:06:45 clark-desktop kernel: [  285.421367] 17116 pages reserved
Aug 18 18:06:45 clark-desktop kernel: [  285.421371] 279805 pages shared
Aug 18 18:06:45 clark-desktop kernel: [  285.421373] 284920 pages non-shared
Aug 18 18:06:45 clark-desktop kernel: [  285.443351] [drm] Num pipes: 1
Aug 18 18:06:46 clark-desktop acpid: client 1824[0:0] has disconnected
Aug 18 18:06:46 clark-desktop acpid: client connected from 2993[0:0]
Aug 18 18:06:46 clark-desktop kernel: [  285.852120] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:06:46 clark-desktop kernel: [  285.852193] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:06:46 clark-desktop kernel: [  286.075388] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:06:46 clark-desktop kernel: [  286.075452] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:06:46 clark-desktop kernel: [  286.075507] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:06:46 clark-desktop kernel: [  286.104391] [drm] Setting GART location based on new memory map
Aug 18 18:06:46 clark-desktop kernel: [  286.105817] [drm] Loading R500 Microcode
Aug 18 18:06:46 clark-desktop kernel: [  286.105853] [drm] Num pipes: 1
Aug 18 18:06:46 clark-desktop kernel: [  286.105860] [drm] writeback test succeeded in 1 usecs
Aug 18 18:06:59 clark-desktop ntpd[2655]: synchronized to 91.189.94.4, stratum 2
Aug 18 18:06:59 clark-desktop ntpd[2655]: kernel time sync status change 2001
Aug 18 18:07:08 clark-desktop pulseaudio[3143]: pid.c: Stale PID file, overwriting.
Aug 18 18:07:14 clark-desktop pulseaudio[3143]: ratelimit.c: 7 events suppressed
Aug 18 18:08:50 clark-desktop kernel: [  410.234747] Xorg: page allocation failure. order:4, mode:0x40d0
Aug 18 18:08:50 clark-desktop kernel: [  410.234752] Pid: 2993, comm: Xorg Not tainted 2.6.31-22-generic #60-Ubuntu
Aug 18 18:08:50 clark-desktop kernel: [  410.234755] Call Trace:
Aug 18 18:08:50 clark-desktop kernel: [  410.234764]  [<c0572d1c>] ? printk+0x18/0x1c
Aug 18 18:08:50 clark-desktop kernel: [  410.234771]  [<c01b84cc>] __alloc_pages_slowpath+0x45c/0x490
Aug 18 18:08:50 clark-desktop kernel: [  410.234775]  [<c01b860f>] __alloc_pages_nodemask+0x10f/0x120
Aug 18 18:08:50 clark-desktop kernel: [  410.234780]  [<c01b8667>] __get_free_pages+0x17/0x30
Aug 18 18:08:50 clark-desktop kernel: [  410.234785]  [<c01e0d5f>] __kmalloc+0xdf/0x180
Aug 18 18:08:50 clark-desktop kernel: [  410.234791]  [<c0127b48>] ? default_spin_lock_flags+0x8/0x10
Aug 18 18:08:50 clark-desktop kernel: [  410.234816]  [<f86ace48>] radeon_cp_cmdbuf+0xa98/0xbf0 [radeon]
Aug 18 18:08:50 clark-desktop kernel: [  410.234837]  [<f82888e2>] ? drm_lock+0x252/0x350 [drm]
Aug 18 18:08:50 clark-desktop kernel: [  410.234879]  [<f82856c0>] drm_ioctl+0x180/0x360 [drm]
Aug 18 18:08:50 clark-desktop kernel: [  410.234897]  [<f86ac3b0>] ? radeon_cp_cmdbuf+0x0/0xbf0 [radeon]
Aug 18 18:08:50 clark-desktop kernel: [  410.234903]  [<c0429577>] ? ehci_work+0x57/0x70
Aug 18 18:08:50 clark-desktop kernel: [  410.234907]  [<c0429973>] ? ehci_irq+0x93/0x1f0
Aug 18 18:08:50 clark-desktop kernel: [  410.234912]  [<c018f9ac>] ? handle_IRQ_event+0x4c/0x140
Aug 18 18:08:50 clark-desktop kernel: [  410.234917]  [<c0121180>] ? ack_apic_level+0x60/0x230
Aug 18 18:08:50 clark-desktop kernel: [  410.234922]  [<c01f5e93>] vfs_ioctl+0x73/0x90
Aug 18 18:08:50 clark-desktop kernel: [  410.234926]  [<c01f6161>] do_vfs_ioctl+0x71/0x310
Aug 18 18:08:50 clark-desktop kernel: [  410.234931]  [<c014b4ef>] ? irq_exit+0x2f/0x70
Aug 18 18:08:50 clark-desktop kernel: [  410.234935]  [<c01f645f>] sys_ioctl+0x5f/0x80
Aug 18 18:08:50 clark-desktop kernel: [  410.234939]  [<c01033ac>] syscall_call+0x7/0xb
Aug 18 18:08:50 clark-desktop kernel: [  410.234941] Mem-Info:
Aug 18 18:08:50 clark-desktop kernel: [  410.234944] DMA per-cpu:
Aug 18 18:08:50 clark-desktop kernel: [  410.234946] CPU    0: hi:    0, btch:   1 usd:   0
Aug 18 18:08:50 clark-desktop kernel: [  410.234948] CPU    1: hi:    0, btch:   1 usd:   0
Aug 18 18:08:50 clark-desktop kernel: [  410.234950] Normal per-cpu:
Aug 18 18:08:50 clark-desktop kernel: [  410.234952] CPU    0: hi:  186, btch:  31 usd:   0
Aug 18 18:08:50 clark-desktop kernel: [  410.234955] CPU    1: hi:  186, btch:  31 usd:  30
Aug 18 18:08:50 clark-desktop kernel: [  410.234957] HighMem per-cpu:
Aug 18 18:08:50 clark-desktop kernel: [  410.234959] CPU    0: hi:  186, btch:  31 usd:   0
Aug 18 18:08:50 clark-desktop kernel: [  410.234961] CPU    1: hi:  186, btch:  31 usd:  30
Aug 18 18:08:50 clark-desktop kernel: [  410.234965] Active_anon:42366 active_file:32243 inactive_anon:14158
Aug 18 18:08:50 clark-desktop kernel: [  410.234967]  inactive_file:359126 unevictable:0 dirty:26520 writeback:3136 unstable:0
Aug 18 18:08:50 clark-desktop kernel: [  410.234968]  free:44746 slab:9585 mapped:18483 pagetables:1294 bounce:0
Aug 18 18:08:50 clark-desktop kernel: [  410.234973] DMA free:3516kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:4kB inactive_file:4952kB unevictable:0kB present:15836kB pages_scanned:0 all_unreclaimable? no
Aug 18 18:08:50 clark-desktop kernel: [  410.234976] lowmem_reserve[]: 0 865 2014 2014
Aug 18 18:08:50 clark-desktop kernel: [  410.234984] Normal free:5480kB min:3728kB low:4660kB high:5592kB active_anon:40kB inactive_anon:128kB active_file:54264kB inactive_file:724620kB unevictable:0kB present:885944kB pages_scanned:0 all_unreclaimable? no
Aug 18 18:08:50 clark-desktop kernel: [  410.234987] lowmem_reserve[]: 0 0 9194 9194
Aug 18 18:08:50 clark-desktop kernel: [  410.234995] HighMem free:169988kB min:512kB low:1748kB high:2988kB active_anon:169424kB inactive_anon:56504kB active_file:74704kB inactive_file:706932kB unevictable:0kB present:1176856kB pages_scanned:0 all_unreclaimable? no
Aug 18 18:08:50 clark-desktop kernel: [  410.234999] lowmem_reserve[]: 0 0 0 0
Aug 18 18:08:50 clark-desktop kernel: [  410.235004] DMA: 1*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3516kB
Aug 18 18:08:50 clark-desktop kernel: [  410.235017] Normal: 1190*4kB 4*8kB 5*16kB 5*32kB 5*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 5480kB
Aug 18 18:08:50 clark-desktop kernel: [  410.235029] HighMem: 149*4kB 66*8kB 30*16kB 12*32kB 641*64kB 126*128kB 43*256kB 23*512kB 10*1024kB 4*2048kB 17*4096kB = 169988kB
Aug 18 18:08:50 clark-desktop kernel: [  410.235043] 392682 total pagecache pages
Aug 18 18:08:50 clark-desktop kernel: [  410.235045] 0 pages in swap cache
Aug 18 18:08:50 clark-desktop kernel: [  410.235047] Swap cache stats: add 0, delete 0, find 0/0
Aug 18 18:08:50 clark-desktop kernel: [  410.235049] Free swap  = 1461872kB
Aug 18 18:08:50 clark-desktop kernel: [  410.235051] Total swap = 1461872kB
Aug 18 18:08:50 clark-desktop kernel: [  410.240234] 523857 pages RAM
Aug 18 18:08:50 clark-desktop kernel: [  410.240237] 296531 pages HighMem
Aug 18 18:08:50 clark-desktop kernel: [  410.240239] 17116 pages reserved
Aug 18 18:08:50 clark-desktop kernel: [  410.240241] 282880 pages shared
Aug 18 18:08:50 clark-desktop kernel: [  410.240242] 241235 pages non-shared
Aug 18 18:08:50 clark-desktop kernel: [  410.260605] [drm] Num pipes: 1
Aug 18 18:08:51 clark-desktop acpid: client 2993[0:0] has disconnected
Aug 18 18:08:51 clark-desktop acpid: client connected from 3451[0:0]
Aug 18 18:08:51 clark-desktop kernel: [  411.391824] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:08:51 clark-desktop kernel: [  411.391929] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:08:51 clark-desktop kernel: [  411.641248] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:08:51 clark-desktop kernel: [  411.641316] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:08:51 clark-desktop kernel: [  411.641370] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
Aug 18 18:08:51 clark-desktop kernel: [  411.670360] [drm] Setting GART location based on new memory map
Aug 18 18:08:51 clark-desktop kernel: [  411.671764] [drm] Loading R500 Microcode
Aug 18 18:08:51 clark-desktop kernel: [  411.671799] [drm] Num pipes: 1
Aug 18 18:08:51 clark-desktop kernel: [  411.671806] [drm] writeback test succeeded in 1 usecs
Aug 18 18:09:01 clark-desktop CRON[3521]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Aug 18 18:09:22 clark-desktop pulseaudio[3609]: pid.c: Stale PID file, overwriting.
Aug 18 18:09:28 clark-desktop pulseaudio[3609]: ratelimit.c: 1 events suppressed
Aug 18 18:09:28 clark-desktop pulseaudio[3609]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Aug 18 18:09:28 clark-desktop pulseaudio[3609]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Aug 18 18:09:28 clark-desktop pulseaudio[3609]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Aug 18 18:15:02 clark-desktop CRON[3964]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Aug 18 18:17:01 clark-desktop CRON[3982]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 18 18:25:01 clark-desktop CRON[3987]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)

```


this didnt look like it would help much, but the ALSA error mentioned might be worth mentioning, even if it is completely unrelated. (i havent had any sound issues...)

---

### Post by mr clark25 on 2010-08-18
i forgot to say that the laptop hard drive is currently installed as an internal drive, and everything is sata. (minus the external drive)

---

### Post by mr clark25 on 2010-08-19
well, it looks like its not the SATA controller on my motherboard- i can still burn cd's alright. (i have a sata cd drive)

does anyone know what would cause this?

---

### Post by silbak04 on 2010-08-19
I'm not really sure but I found this:

[https://bbs.archlinux.org/viewtopic.php?id=77427](https://bbs.archlinux.org/viewtopic.php?id=77427)

^ hope that helps

---

### Post by EpicEraser on 2010-08-23
I have a similar problem (same error) when copying large quantities of files to an external (USB) hard disk, and when unrarring files.
For me, this error is quite rare, but nonetheless annoying.
I don't believe the post silbak04 mentioned is related.

Oh and I'm using Ubuntu 10.04, Linux 2.6.32-24-generic, Xorg 7.5, and I'm using radeon (r300).

---

