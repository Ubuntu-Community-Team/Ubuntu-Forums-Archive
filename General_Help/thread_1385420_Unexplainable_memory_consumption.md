---
title: "Unexplainable memory consumption"
date: 2010-01-19
forum: General Help
---

### Post by mondalaci on 2010-01-19
Please somebody help me, I am on the verge of becoming mad!

I have 4G RAM in my laptop and according to ps_mem.py which uses smaps which is the most accurate measurement currently 2.8G is used out of 4G.

----8<----

 Private  +   Shared  =  RAM used	Program 

 92.0 KiB +   9.0 KiB = 101.0 KiB	sh
100.0 KiB +   9.0 KiB = 109.0 KiB	sidic
108.0 KiB +   9.0 KiB = 117.0 KiB	icecat
116.0 KiB +  13.0 KiB = 129.0 KiB	dd
120.0 KiB +   9.0 KiB = 129.0 KiB	run-icecat.sh
140.0 KiB +   9.0 KiB = 149.0 KiB	compiz
152.0 KiB +  23.0 KiB = 175.0 KiB	gnome-pty-helper
156.0 KiB +  21.0 KiB = 177.0 KiB	atd
176.0 KiB +  20.0 KiB = 196.0 KiB	upstart-udev-bridge
180.0 KiB +  16.0 KiB = 196.0 KiB	dhclient3
184.0 KiB +  26.0 KiB = 210.0 KiB	hald-addon-generic-backlight
192.0 KiB +  26.0 KiB = 218.0 KiB	hald-addon-cpufreq
196.0 KiB +  26.0 KiB = 222.0 KiB	hald-addon-rfkill-killswitch
212.0 KiB +  30.0 KiB = 242.0 KiB	hald-addon-acpi
216.0 KiB +  29.0 KiB = 245.0 KiB	hald-addon-storage
220.0 KiB +  28.0 KiB = 248.0 KiB	hald-addon-input
240.0 KiB +  25.0 KiB = 265.0 KiB	syndaemon
248.0 KiB +  26.0 KiB = 274.0 KiB	cron
288.0 KiB +  27.0 KiB = 315.0 KiB	hald-runner
420.0 KiB +  52.5 KiB = 472.5 KiB	gvfsd-burn
452.0 KiB +  39.5 KiB = 491.5 KiB	ssh-agent
440.0 KiB +  55.5 KiB = 495.5 KiB	indicator-users-service
484.0 KiB +  30.0 KiB = 514.0 KiB	wpa_supplicant
476.0 KiB +  52.0 KiB = 528.0 KiB	gvfsd-metadata
540.0 KiB +  61.0 KiB = 601.0 KiB	modem-manager
596.0 KiB +   9.0 KiB = 605.0 KiB	acpid
560.0 KiB +  66.0 KiB = 626.0 KiB	gvfs-gphoto2-volume-monitor
572.0 KiB +  63.5 KiB = 635.5 KiB	indicator-session-service
592.0 KiB +  58.0 KiB = 650.0 KiB	dbus-launch (2)
464.0 KiB + 206.0 KiB = 670.0 KiB	avahi-daemon (2)
604.0 KiB +  69.0 KiB = 673.0 KiB	getty (6)
616.0 KiB +  70.5 KiB = 686.5 KiB	gvfsd-trash
668.0 KiB +  25.5 KiB = 693.5 KiB	init
248.0 KiB + 584.0 KiB = 832.0 KiB	udevd (3)
740.0 KiB +  95.0 KiB = 835.0 KiB	gdm-session-worker
756.0 KiB +  89.5 KiB = 845.5 KiB	gconf-helper (deleted)
780.0 KiB +  65.5 KiB = 845.5 KiB	gvfs-fuse-daemon
780.0 KiB +  87.0 KiB = 867.0 KiB	gdm-binary
832.0 KiB +  75.0 KiB = 907.0 KiB	cupsd
824.0 KiB +  84.0 KiB = 908.0 KiB	gdm-simple-slave
828.0 KiB +  82.5 KiB = 910.5 KiB	gvfs-gdu-volume-monitor
860.0 KiB +  62.5 KiB = 922.5 KiB	gvfsd
888.0 KiB +  86.5 KiB = 974.5 KiB	NetworkManager
892.0 KiB + 115.5 KiB =   1.0 MiB	indicator-status-service
792.0 KiB + 268.5 KiB =   1.0 MiB	devkit-disks-daemon (2)
  1.0 MiB +  95.0 KiB =   1.1 MiB	VBoxXPCOMIPCD
  1.0 MiB + 118.5 KiB =   1.1 MiB	console-kit-daemon
  1.1 MiB +  66.0 KiB =   1.2 MiB	bonobo-activation-server
  1.1 MiB +  74.5 KiB =   1.2 MiB	polkitd
  1.2 MiB +  57.0 KiB =   1.2 MiB	devkit-power-daemon
  1.3 MiB +  51.5 KiB =   1.3 MiB	hald
  1.2 MiB + 103.5 KiB =   1.3 MiB	gvfsd-http
  1.5 MiB +  45.5 KiB =   1.5 MiB	rsyslogd
  1.5 MiB +  36.5 KiB =   1.6 MiB	tnslsnr
  1.7 MiB + 170.0 KiB =   1.8 MiB	gdu-notification-daemon
  1.8 MiB + 175.5 KiB =   2.0 MiB	gnome-session
  1.8 MiB + 230.5 KiB =   2.1 MiB	gnome-screensaver
  2.4 MiB + 288.0 KiB =   2.7 MiB	dbus-daemon (2)
  2.5 MiB + 242.5 KiB =   2.7 MiB	multiload-applet-2
  2.9 MiB + 224.5 KiB =   3.1 MiB	seahorse-daemon
  3.0 MiB + 330.5 KiB =   3.3 MiB	evolution-alarm-notify
  3.2 MiB + 215.5 KiB =   3.4 MiB	VBoxSVC
  3.2 MiB + 315.0 KiB =   3.5 MiB	gnome-settings-daemon
  3.7 MiB + 283.0 KiB =   3.9 MiB	bluetooth-applet
  4.2 MiB +  83.5 KiB =   4.3 MiB	gconfd-2
  4.1 MiB + 203.5 KiB =   4.3 MiB	update-notifier
  4.0 MiB + 354.0 KiB =   4.4 MiB	polkit-gnome-authentication-agent-1
  4.1 MiB + 347.5 KiB =   4.4 MiB	gnome-volume-control-applet
816.0 KiB +   4.1 MiB =   4.8 MiB	apache2 (6)
  4.5 MiB + 416.5 KiB =   4.9 MiB	indicator-applet-session
  4.8 MiB + 157.5 KiB =   4.9 MiB	mc (3)
  5.1 MiB + 314.5 KiB =   5.4 MiB	notify-osd
  5.2 MiB + 297.0 KiB =   5.5 MiB	gnome-keyboard-applet
  5.5 MiB +  67.5 KiB =   5.6 MiB	system-service-
  5.4 MiB + 362.5 KiB =   5.7 MiB	nm-applet
  5.6 MiB + 218.0 KiB =   5.8 MiB	ssh (2)
  5.3 MiB + 535.0 KiB =   5.8 MiB	gtk-window-decorator
  7.5 MiB +  96.0 KiB =   7.6 MiB	gnome-keyring-daemon
  9.4 MiB + 667.0 KiB =  10.1 MiB	gnome-terminal
 10.0 MiB + 380.5 KiB =  10.4 MiB	python2.6
 12.6 MiB + 324.0 KiB =  12.9 MiB	tomboy
 12.4 MiB + 805.5 KiB =  13.1 MiB	nautilus
 12.9 MiB + 915.0 KiB =  13.8 MiB	gnome-panel
 14.7 MiB + 653.5 KiB =  15.3 MiB	xchat
 14.6 MiB + 773.0 KiB =  15.3 MiB	ekiga
 18.9 MiB +   1.3 MiB =  20.1 MiB	pidgin (deleted)
 21.9 MiB + 265.5 KiB =  22.1 MiB	bash (8)
 26.3 MiB +   1.6 MiB =  27.8 MiB	npviewer.bin (2)
 31.3 MiB +   1.0 MiB =  32.3 MiB	rhythmbox (deleted)
 34.0 MiB + 211.0 KiB =  34.2 MiB	pulseaudio (deleted)
 35.6 MiB + 687.0 KiB =  36.2 MiB	soffice.bin
 40.1 MiB + 280.5 KiB =  40.4 MiB	skype
 52.2 MiB +   5.6 MiB =  57.8 MiB	Xorg
 60.0 MiB + 393.0 KiB =  60.4 MiB	compiz.real
133.2 MiB + 738.5 KiB = 133.9 MiB	icecat-bin
157.1 MiB + 816.5 KiB = 157.9 MiB	firefox
170.5 MiB +  61.7 MiB = 232.2 MiB	oracle (27)
530.8 MiB +   1.6 MiB = 532.4 MiB	VirtualBox (2)
  1.1 GiB + 264.5 KiB =   1.1 GiB	jsvc (3)
---------------------------------
                          2.7 GiB
=================================

 Private  +   Shared  =  RAM used	Program 

----8<----

But according to free the situation looks different:

             total       used       free     shared    buffers     cached
Mem:       3959464    3924556      34908          0        908    1198968
-/+ buffers/cache:    2724680    1234784
Swap:            0          0          0


/proc/meminfo also confirms free:

MemTotal:        3959464 kB
MemFree:           36044 kB
Buffers:             476 kB
Cached:          1197828 kB
SwapCached:            0 kB
Active:          2714500 kB
Inactive:         818020 kB
Active(anon):    2678648 kB
Inactive(anon):   791308 kB
Active(file):      35852 kB
Inactive(file):    26712 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:               180 kB
Writeback:             0 kB
AnonPages:       2334216 kB
Mapped:           432768 kB
Slab:              77360 kB
SReclaimable:      31020 kB
SUnreclaim:        46340 kB
PageTables:        47076 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1979732 kB
Committed_AS:    5570448 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      566828 kB
VmallocChunk:   34359093263 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       10240 kB
DirectMap2M:     4085760 kB


ps -ef

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jan18 ?        00:00:00 /sbin/init
root         2     0  0 Jan18 ?        00:00:00 [kthreadd]
root         3     2  0 Jan18 ?        00:00:00 [migration/0]
root         4     2  0 Jan18 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 Jan18 ?        00:00:00 [watchdog/0]
root         6     2  0 Jan18 ?        00:00:00 [migration/1]
root         7     2  0 Jan18 ?        00:00:08 [ksoftirqd/1]
root         8     2  0 Jan18 ?        00:00:00 [watchdog/1]
root         9     2  0 Jan18 ?        00:00:51 [events/0]
root        10     2  0 Jan18 ?        00:00:01 [events/1]
root        11     2  0 Jan18 ?        00:00:00 [cpuset]
root        12     2  0 Jan18 ?        00:00:00 [khelper]
root        13     2  0 Jan18 ?        00:00:00 [netns]
root        14     2  0 Jan18 ?        00:00:00 [async/mgr]
root        15     2  0 Jan18 ?        00:00:00 [kintegrityd/0]
root        16     2  0 Jan18 ?        00:00:00 [kintegrityd/1]
root        17     2  0 Jan18 ?        00:00:00 [kblockd/0]
root        18     2  0 Jan18 ?        00:00:00 [kblockd/1]
root        19     2  0 Jan18 ?        00:00:00 [kacpid]
root        20     2  0 Jan18 ?        00:00:00 [kacpi_notify]
root        21     2  0 Jan18 ?        00:00:00 [kacpi_hotplug]
root        22     2  0 Jan18 ?        00:00:00 [ata/0]
root        23     2  0 Jan18 ?        00:00:00 [ata/1]
root        24     2  0 Jan18 ?        00:00:00 [ata_aux]
root        25     2  0 Jan18 ?        00:00:00 [ksuspend_usbd]
root        26     2  0 Jan18 ?        00:00:00 [khubd]
root        27     2  0 Jan18 ?        00:00:00 [kseriod]
root        28     2  0 Jan18 ?        00:00:00 [kmmcd]
root        29     2  0 Jan18 ?        00:00:00 [bluetooth]
root        30     2  0 Jan18 ?        00:00:00 [khungtaskd]
root        31     2  0 Jan18 ?        00:00:01 [pdflush]
root        32     2  0 Jan18 ?        00:00:02 [pdflush]
root        33     2  0 Jan18 ?        00:00:04 [kswapd0]
root        34     2  0 Jan18 ?        00:00:00 [aio/0]
root        35     2  0 Jan18 ?        00:00:00 [aio/1]
root        36     2  0 Jan18 ?        00:00:00 [ecryptfs-kthrea]
root        37     2  0 Jan18 ?        00:00:00 [crypto/0]
root        38     2  0 Jan18 ?        00:00:00 [crypto/1]
root        54     2  0 Jan18 ?        00:00:00 [scsi_eh_0]
root        55     2  0 Jan18 ?        00:00:12 [scsi_eh_1]
root        56     2  0 Jan18 ?        00:00:00 [scsi_eh_2]
root        57     2  0 Jan18 ?        00:00:00 [scsi_eh_3]
root        58     2  0 Jan18 ?        00:00:00 [scsi_eh_4]
root        59     2  0 Jan18 ?        00:00:00 [scsi_eh_5]
root        74     2  0 Jan18 ?        00:00:00 [kstriped]
root        75     2  0 Jan18 ?        00:00:00 [kmpathd/0]
root        76     2  0 Jan18 ?        00:00:00 [kmpathd/1]
root        77     2  0 Jan18 ?        00:00:00 [kmpath_handlerd]
root        78     2  0 Jan18 ?        00:00:00 [ksnapd]
root        79     2  0 Jan18 ?        00:00:03 [kondemand/0]
root        80     2  0 Jan18 ?        00:00:17 [kondemand/1]
root        81     2  0 Jan18 ?        00:00:00 [kconservative/0]
root        82     2  0 Jan18 ?        00:00:00 [kconservative/1]
root        83     2  0 Jan18 ?        00:00:00 [krfcommd]
root       333     2  0 15:13 ?        00:00:00 [scsi_eh_8]
root       371     2  0 Jan18 ?        00:00:00 [khpsbpkt]
root       378     2  0 Jan18 ?        00:00:00 [i915/0]
root       379     2  0 Jan18 ?        00:00:00 [i915/1]
root       384     2  0 Jan18 ?        00:00:00 [knodemgrd_0]
root       387     2  0 Jan18 ?        00:00:00 [usbhid_resumer]
root       475     2  0 Jan18 ?        00:00:09 [kjournald2]
root       476     2  0 Jan18 ?        00:00:00 [ext4-dio-unwrit]
root       477     2  0 Jan18 ?        00:00:00 [ext4-dio-unwrit]
root       540     1  0 Jan18 ?        00:00:00 udevd --daemon
root       630     2  0 Jan18 ?        00:00:00 [kpsmoused]
laci       752  2760  0 15:20 pts/5    00:00:00 bash
laci       771   752  0 15:21 pts/5    00:00:01 mc
laci       773   771  0 15:21 pts/6    00:00:00 bash -rcfile .bashrc
root       837     2  0 Jan18 ?        00:00:00 [iwlagn]
root       838     2  0 Jan18 ?        00:00:00 [phy0]
root       868     2  0 Jan18 ?        00:00:00 [hd-audio0]
102        915     1  0 Jan18 ?        00:00:01 dbus-daemon --system --fork
root       918     1  0 Jan18 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
syslog     927     1  0 Jan18 ?        00:00:00 rsyslogd -c4
avahi      928     1  0 Jan18 ?        00:00:00 avahi-daemon: running [nitehawk.local]
avahi      929   928  0 Jan18 ?        00:00:00 avahi-daemon: chroot helper
root       933     1  0 Jan18 ?        00:00:01 NetworkManager
107        934     1  0 Jan18 ?        00:00:02 hald --daemon=yes
root       936     1  0 Jan18 ?        00:00:00 /usr/sbin/modem-manager
root       942     1  0 Jan18 ?        00:00:00 gdm-binary
root       948     2  0 Jan18 ?        00:00:00 [hd-audio1]
root       951     1  0 Jan18 ?        00:00:00 /usr/sbin/console-kit-daemon
root      1016   934  0 Jan18 ?        00:00:00 hald-runner
laci      1037 32527 29 15:23 ?        01:33:31 /usr/lib/virtualbox/VirtualBox --comment whisper-winxp1 --startvm 5c4adce5-b1d2-493c-a5b9-9b72bae494a8
root      1166     1  0 Jan18 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1169     1  0 Jan18 ?        00:00:00 /sbin/wpa_supplicant -u -s
root      1177     1  0 Jan18 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1184     1  0 Jan18 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1185     1  0 Jan18 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1187     1  0 Jan18 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1193     1  0 Jan18 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1203     1  0 Jan18 ?        00:00:00 atd
root      1204     1  0 Jan18 ?        00:00:00 cron
root      1210  1016  0 Jan18 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      1229  1016  0 Jan18 ?        00:00:00 /usr/lib/hal/hald-addon-generic-backlight
root      1230   942  0 Jan18 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1233  1230  6 Jan18 tty7     02:10:27 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-UkS544/database -nolisten tcp vt7
root      1273  1016  0 Jan18 ?        00:00:08 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1296  1016  0 Jan18 ?        00:00:04 hald-addon-input: Listening on /dev/input/event9 /dev/input/event11 /dev/input/event0 /dev/input/event8 /dev/input/event3 /dev/input/event7 /dev/input/event2 /dev/input/event10 /dev/input/event5 /dev/input/event1
root      1388  1016  0 Jan18 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
107       1389  1016  0 Jan18 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
oracle    1555     1  0 Jan18 ?        00:00:00 /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/tnslsnr LISTENER -inherit
root      1571   540  0 15:36 ?        00:00:00 udevd --daemon
root      1572   540  0 15:36 ?        00:00:00 udevd --daemon
root      1577   933  0 Jan18 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-713fefc5-95f3-41a4-9d7c-2d83dba331a8-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
oracle    1583     1  0 Jan18 ?        00:00:17 xe_pmon_XE
oracle    1585     1  0 Jan18 ?        00:00:01 xe_psp0_XE
oracle    1588     1  0 Jan18 ?        00:00:01 xe_mman_XE
oracle    1590     1  0 Jan18 ?        00:00:03 xe_dbw0_XE
oracle    1593     1  0 Jan18 ?        00:00:11 xe_lgwr_XE
oracle    1595     1  0 Jan18 ?        00:00:07 xe_ckpt_XE
oracle    1597     1  0 Jan18 ?        00:00:04 xe_smon_XE
oracle    1599     1  0 Jan18 ?        00:00:00 xe_reco_XE
oracle    1601     1  0 Jan18 ?        00:00:15 xe_cjq0_XE
oracle    1603     1  0 Jan18 ?        00:00:09 xe_mmon_XE
oracle    1605     1  0 Jan18 ?        00:00:16 xe_mmnl_XE
oracle    1609     1  0 Jan18 ?        00:00:00 xe_d000_XE
oracle    1611     1  0 Jan18 ?        00:00:00 xe_s000_XE
oracle    1613     1  0 Jan18 ?        00:00:00 xe_s001_XE
oracle    1615     1  0 Jan18 ?        00:00:00 xe_s002_XE
oracle    1619     1  0 Jan18 ?        00:00:00 xe_s003_XE
gdm       1653     1  0 Jan18 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session
root      1658     1  0 Jan18 ?        00:00:00 /usr/lib/devicekit-power/devkit-power-daemon
root      1718  1230  0 Jan18 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
oracle    1796     1  0 Jan18 ?        00:00:00 xe_qmnc_XE
root      1875     1  0 Jan18 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
laci      1957     1  5 15:44 ?        00:17:35 /usr/lib/firefox-3.5.7/firefox
root      2009     1  0 Jan18 ?        00:00:03 /usr/sbin/apache2 -k start
www-data  2010  2009  0 Jan18 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2011  2009  0 Jan18 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2012  2009  0 Jan18 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2013  2009  0 Jan18 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  2014  2009  0 Jan18 ?        00:00:00 /usr/sbin/apache2 -k start
laci      2027  1957  4 15:45 ?        00:15:00 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/1957-2
laci      2065     1  0 Jan18 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login
laci      2080  1718  0 Jan18 ?        00:00:40 gnome-session
laci      2165  2080  0 Jan18 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
laci      2168     1  0 Jan18 ?        00:02:43 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
laci      2169     1  0 Jan18 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
root      2235     1  0 Jan18 tty1     00:00:00 /sbin/getty -8 38400 tty1
laci      2240     1  0 Jan18 ?        00:01:31 /usr/lib/libgconf2-4/gconfd-2
laci      2249     1  0 Jan18 ?        00:00:57 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
laci      2251     1  0 Jan18 ?        00:00:27 seahorse-daemon
laci      2254     1  0 Jan18 ?        00:00:14 /usr/lib/gvfs/gvfsd
laci      2259     1  0 Jan18 ?        00:00:14 /usr/lib/gvfs//gvfs-fuse-daemon /home/laci/.gvfs
laci      2278     1  0 Jan18 ?        00:00:34 /usr/lib/notify-osd/notify-osd
laci      2279  2080  0 Jan18 ?        00:00:00 /bin/sh /usr/bin/compiz
laci      2306     1  0 Jan18 ?        00:00:50 syndaemon -i 0.5 -k
laci      2340  2279  0 Jan18 ?        00:13:43 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 10df7ece75a765a8126380636298313500000020800022 move resize place decoration animation ccp
laci      2341  2080  0 Jan18 ?        00:02:30 gnome-panel
laci      2342  2080  0 Jan18 ?        00:00:43 nautilus
laci      2345     1  0 Jan18 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
laci      2348  2080  0 Jan18 ?        00:00:26 bluetooth-applet
laci      2350  2080  0 Jan18 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
laci      2351  2080  0 Jan18 ?        00:01:02 python /usr/share/system-config-printer/applet.py
laci      2355  2080  0 Jan18 ?        00:00:36 update-notifier --startup-delay=60
laci      2366     1  0 Jan18 ?        00:00:00 bash /usr/bin/tomboy-panel --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=18
laci      2369  2366  0 Jan18 ?        00:00:01 mono /usr/lib/tomboy/Tomboy.exe --sm-disable --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=18
laci      2370  2080  0 Jan18 ?        00:00:00 gnome-volume-control-applet
laci      2372     1  0 Jan18 ?        00:00:27 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=24
laci      2373  2080  0 Jan18 ?        00:00:20 /usr/lib/evolution/2.28/evolution-alarm-notify
laci      2376  2080  0 Jan18 ?        00:00:19 /usr/lib/gnome-disk-utility/gdu-notification-daemon
laci      2382     1  0 Jan18 ?        00:15:08 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=23
laci      2383  2080  0 Jan18 ?        00:00:29 nm-applet --sm-disable
root      2386     1  0 Jan18 ?        00:00:09 /usr/lib/devicekit-disks/devkit-disks-daemon
root      2387  2386  0 Jan18 ?        00:00:00 devkit-disks-daemon: not polling any devices
laci      2389     1  0 Jan18 ?        00:00:10 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_Factory --oaf-ior-fd=28
laci      2390     1  0 Jan18 ?        00:00:34 gnome-screensaver
root      2393     1  0 Jan18 ?        00:00:00 /usr/lib/policykit-1/polkitd
laci      2395  2340  0 Jan18 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
laci      2396  2395  0 Jan18 ?        00:00:25 /usr/bin/gtk-window-decorator
laci      2402     1  0 Jan18 ?        00:00:31 /usr/lib/indicator-session/indicator-status-service
laci      2405     1  0 Jan18 ?        00:00:16 /usr/lib/indicator-session/indicator-users-service
laci      2407     1  0 Jan18 ?        00:00:20 /usr/lib/indicator-session/indicator-session-service
laci      2413     1  0 Jan18 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.7 /org/gtk/gvfs/exec_spaw/0
oracle    2422     1  0 Jan18 ?        00:00:00 xe_q000_XE
laci      2424     1  0 Jan18 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
laci      2426     1  0 Jan18 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
laci      2441     1  0 Jan18 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
laci      2445     1  0 Jan18 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.7 /org/gtk/gvfs/exec_spaw/1
laci      2462     1  0 Jan18 ?        00:00:00 /bin/sh /usr/bin/icecat
laci      2474  2462  0 Jan18 ?        00:00:00 /bin/sh /usr/lib/icecat/run-icecat.sh /usr/lib/icecat/icecat-bin
laci      2478  2474  2 Jan18 ?        00:42:59 /usr/lib/icecat/icecat-bin
laci      2483     1  0 Jan18 ?        00:05:42 pidgin
laci      2543     1  1 Jan18 ?        00:29:26 xchat
laci      2565     1  1 Jan18 ?        00:25:59 skype
laci      2643  2478  2 Jan18 ?        00:42:51 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/2478-1
root      2721     1  0 Jan18 ?        00:00:00 /usr/bin/python /usr/lib/system-service/system-service-d
laci      2760     1  0 Jan18 ?        00:02:18 gnome-terminal
laci      2761  2760  0 Jan18 ?        00:00:00 gnome-pty-helper
laci      2762  2760  0 Jan18 pts/0    00:00:00 bash
root      3064     1  0 Jan18 ?        00:00:00 upstart-udev-bridge --daemon
root      3094     2  0 Jan18 ?        00:00:00 [kdmflush]
root      3095     2  0 Jan18 ?        00:00:00 [kcryptd_io]
root      3096     2  0 Jan18 ?        00:00:06 [kcryptd]
root      3113     2  0 Jan18 ?        00:00:00 [kjournald2]
root      3114     2  0 Jan18 ?        00:00:00 [ext4-dio-unwrit]
root      3115     2  0 Jan18 ?        00:00:00 [ext4-dio-unwrit]
laci      3136     1  0 Jan18 ?        00:11:51 rhythmbox
laci      3177  2762  0 Jan18 pts/0    00:00:01 mc
laci      3179  3177  0 Jan18 pts/1    00:00:00 bash -rcfile .bashrc
laci      3272  3179  0 01:42 pts/1    00:00:00 /bin/sh /usr/local/bin/sidic
laci      3644  3177  0 Jan18 pts/0    00:00:03 ssh -l root obconsulting.hu echo FISH:; /bin/sh
laci      3668     1  0 Jan18 ?        00:00:00 /usr/lib/gvfs/gvfsd-http --spawner :1.7 /org/gtk/gvfs/exec_spaw/2
laci      7851  2760  0 03:45 pts/3    00:00:00 bash
laci      7870  7851  0 03:45 pts/3    00:00:08 ssh obconsulting.hu
root     13314     1  0 20:35 ?        00:00:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Xms512M -Xmx1024M -XX:MaxPermSize=384M -Djava.awt.headless=true -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/tmp/tomcat6-temp -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap
root     13316 13314  0 20:35 ?        00:00:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Xms512M -Xmx1024M -XX:MaxPermSize=384M -Djava.awt.headless=true -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/tmp/tomcat6-temp -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap
tomcat6  13317 13314 16 20:35 ?        00:01:41 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Xms512M -Xmx1024M -XX:MaxPermSize=384M -Djava.awt.headless=true -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/tmp/tomcat6-temp -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap
oracle   13365     1  0 20:36 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13383     1  0 20:36 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13411     1  0 20:36 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13430     1  0 20:36 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13451     1  0 20:37 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13469     1  0 20:37 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13487     1  0 20:37 ?        00:00:00 oracleXE (LOCAL=NO)
oracle   13496     1  0 20:37 ?        00:00:00 oracleXE (LOCAL=NO)
laci     13850   773  0 20:45 pts/6    00:00:00 ps -ef
laci     14330     1  0 Jan18 ?        00:01:57 /usr/lib/openoffice/program/soffice.bin /tmp/Spec_emax_8.doc -splash-pipe=5
laci     22567     1  0 Jan18 ?        00:11:19 /usr/bin/pulseaudio --start --log-target=syslog
laci     22571 22567  0 Jan18 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
laci     22576     1  2 Jan18 ?        00:32:23 ekiga
laci     26114  2760  0 12:03 pts/2    00:00:00 bash
laci     26133 26114  0 12:03 pts/2    00:00:00 mc
laci     26135 26133  0 12:03 pts/4    00:00:00 bash -rcfile .bashrc
laci     32512     1  0 15:05 ?        00:00:04 /usr/lib/virtualbox/VirtualBox
laci     32518 32512  0 15:05 ?        00:00:02 /usr/lib/virtualbox/VBoxXPCOMIPCD
laci     32527     1  0 15:05 ?        00:00:09 /usr/lib/virtualbox/VBoxSVC --automate
oracle   32602     1  0 15:09 ?        00:00:00 xe_q001_XE

Please somebody explain me what's going on.  I don't wanna upgrade my RAM to 8G in my laptop.  Is it possible at all?

Laci

---

### Post by colinjones on 2010-01-30
Not sure what is the problem here, ps_mem.py is indicating you have consumed 2.7GB, and so is free - you need to look at the first number on the second line. The other number includes buffers and cache which is actually consumed... on a typical system the other number will usually be almost all memory and so is meaningless as an assessment of RAM consumed.

---

### Post by skymera on 2010-01-30
Can you post the output of ```
 free -m 
```

And please use the [code] tags to paste outputs :D easier to read

---

### Post by mcduck on 2010-01-30
Nothing strange there, all your outputs report the same amount of free & used RAM.

2,7GB of memorry used by system & applications, with 1,2 GB still available for them. You also have 1,2GB of cached data, which summed together with the RAM used by applications gives the 3,9GB you see on the first line of "free" output.

2724680 (RAM used by programs) + 2724680 (cache) + 908 (buffers) = 3924556 (total amount of RAM currently in *some* use).

Linux doesn't waste your RAM by leaving it unused, the part that isn't used for anything else is used as disk cache. That part still counts as free (from any program's point of view), since if any program needs more memory some cached data can simply be dropped (so no need to buy more RAM, after running some time all your RAM is *supposed to* be put to some use or other).. When you use "free -m" to check your RAM usage make sure to read from the "-/+ buffers/cache"-line.. :)

---

### Post by OrangeCrate on 2010-01-30
Adding to mcduck's post, here's a good read on Linux memory management...

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

---

### Post by mondalaci on 2010-04-06
It seems that setting vm.swapiness to 5 (the defaualt is 60 I believe) solved my issue.

Thanks guys!

---

