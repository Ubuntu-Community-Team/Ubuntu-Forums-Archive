---
title: "apt problem"
date: 2011-08-21
forum: General Help
---

### Post by med linux on 2011-08-21
hi 
I have a problem I can't install any software 
cold you help me ?? 
```
user@user-Compaq-610:~$ sudo apt-get install  postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-sip
Use 'apt-get autoremove' to remove them.
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf postfix-cdb
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,306kB of archives.
After this operation, 3,211kB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 294203 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.7.1-1ubuntu0.2_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/postfix_2.7.1-1ubuntu0.2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.7.1-1ubuntu0.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user-Compaq-610:~$ 

```look at ps -aux result 
```
user@user-Compaq-610:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2880  1732 ?        Ss   Aug21   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Aug21   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Aug21   0:01 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    Aug21   0:02 [migration/0]
root         5  0.0  0.0      0     0 ?        S    Aug21   0:00 [watchdog/0]
root         9  0.0  0.0      0     0 ?        S    Aug21   0:01 [events/0]
root        11  0.0  0.0      0     0 ?        S    Aug21   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    Aug21   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    Aug21   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    Aug21   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    Aug21   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    Aug21   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    Aug21   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    Aug21   0:00 [kintegrityd/0]
root        21  0.0  0.0      0     0 ?        S    Aug21   0:00 [kblockd/0]
root        23  0.0  0.0      0     0 ?        S    Aug21   0:18 [kacpid]
root        24  0.2  0.0      0     0 ?        S    Aug21   1:46 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    Aug21   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    Aug21   0:00 [ata_aux]
root        27  0.0  0.0      0     0 ?        S    Aug21   0:00 [ata_sff/0]
root        29  0.0  0.0      0     0 ?        S    Aug21   0:00 [khubd]
root        30  0.0  0.0      0     0 ?        S    Aug21   0:00 [kseriod]
root        31  0.0  0.0      0     0 ?        S    Aug21   0:00 [kmmcd]
root        32  0.0  0.0      0     0 ?        S    Aug21   0:00 [khungtaskd]
root        33  0.0  0.0      0     0 ?        S    Aug21   0:00 [kswapd0]
root        34  0.0  0.0      0     0 ?        SN   Aug21   0:00 [ksmd]
root        35  0.0  0.0      0     0 ?        S    Aug21   0:00 [aio/0]
root        37  0.0  0.0      0     0 ?        S    Aug21   0:00 [ecryptfs-kthrea]
root        38  0.0  0.0      0     0 ?        S    Aug21   0:00 [crypto/0]
root        52  0.0  0.0      0     0 ?        S    Aug21   0:00 [scsi_eh_0]
root        53  0.0  0.0      0     0 ?        S    Aug21   0:00 [scsi_eh_1]
root        56  0.0  0.0      0     0 ?        S    Aug21   0:00 [kstriped]
root        57  0.0  0.0      0     0 ?        S    Aug21   0:00 [kmpathd/0]
root        59  0.0  0.0      0     0 ?        S    Aug21   0:00 [kmpath_handlerd]
root        60  0.0  0.0      0     0 ?        S    Aug21   0:00 [ksnapd]
root        61  0.0  0.0      0     0 ?        S    Aug21   0:25 [kondemand/0]
root        63  0.0  0.0      0     0 ?        S    Aug21   0:00 [kconservative/0]
root       231  0.0  0.0      0     0 ?        S    Aug21   0:00 [scsi_eh_2]
root       279  0.0  0.0      0     0 ?        S    Aug21   0:00 [scsi_eh_3]
root       301  0.0  0.0      0     0 ?        S    Aug21   0:03 [scsi_eh_4]
root       311  0.0  0.0      0     0 ?        S    Aug21   0:00 [usbhid_resumer]
root       330  0.0  0.0      0     0 ?        S    Aug21   0:03 [jbd2/sda6-8]
root       331  0.0  0.0      0     0 ?        S    Aug21   0:00 [ext4-dio-unwrit]
root       365  0.0  0.0      0     0 ?        S    Aug21   0:01 [flush-8:0]
root       393  0.0  0.0   2524   876 ?        S    Aug21   0:00 upstart-udev-bridge --daemon
root       396  0.0  0.0   2632  1024 ?        S<s  Aug21   0:00 udevd --daemon
root       578  0.0  0.0      0     0 ?        S    Aug21   0:00 [kpsmoused]
root       709  0.0  0.0      0     0 ?        S    Aug21   0:00 [cfg80211]
root       786  0.0  0.0      0     0 ?        S    Aug21   0:00 [rtl92s_pci/0]
root       804  0.0  0.0      0     0 ?        S    Aug21   0:00 [phy0]
root       841  0.0  0.0      0     0 ?        S    Aug21   0:00 [i915]
syslog     875  0.0  0.0  34592  1148 ?        Sl   Aug21   0:00 rsyslogd -c4
102        894  0.0  0.0   3576  1920 ?        Ss   Aug21   0:03 dbus-daemon --system --fork
root       901  0.0  0.2  19268  4332 ?        Ssl  Aug21   0:00 NetworkManager
avahi      903  0.0  0.0   3012  1376 ?        S    Aug21   0:00 avahi-daemon: running [user-Compaq-610.local]
avahi      905  0.0  0.0   3012   444 ?        S    Aug21   0:00 avahi-daemon: chroot helper
root       906  0.0  0.1   4432  2444 ?        S    Aug21   0:00 /usr/sbin/modem-manager
root       964  0.0  0.0   4900  1520 ?        S    Aug21   0:00 /sbin/wpa_supplicant -u -s
root       979  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kslowd000]
root       980  0.0  0.0      0     0 ?        S<   Aug21   0:00 [kslowd001]
root       981  0.0  0.0   1856   560 tty4     Ss+  Aug21   0:00 /sbin/getty -8 38400 tty4
root       989  0.0  0.0   1856   564 tty5     Ss+  Aug21   0:00 /sbin/getty -8 38400 tty5
root       997  0.0  0.0   1856   564 tty2     Ss+  Aug21   0:00 /sbin/getty -8 38400 tty2
root       998  0.0  0.0   1856   560 tty3     Ss+  Aug21   0:00 /sbin/getty -8 38400 tty3
root      1001  0.0  0.0   1856   564 tty6     Ss+  Aug21   0:00 /sbin/getty -8 38400 tty6
root      1004  0.0  0.0   2244  1044 ?        Ss   Aug21   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1010  0.0  0.1  19544  3220 ?        Ssl  Aug21   0:00 gdm-binary
root      1020  0.0  0.0      0     0 ?        S    Aug21   0:00 [hd-audio0]
root      1026  0.0  0.1  21632  3364 ?        Sl   Aug21   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1043  0.0  0.0   2456   912 ?        Ss   Aug21   0:00 cron
daemon    1044  0.0  0.0   2316   356 ?        Ss   Aug21   0:00 atd
root      1149  0.0  0.1   6792  2436 ?        Ss   Aug21   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1343  0.0  0.0   1856   560 tty1     Ss+  Aug21   0:00 /sbin/getty -8 38400 tty1
root      1366  0.0  0.2  10780  5620 ?        S    Aug21   0:03 /usr/lib/upower/upowerd
rtkit     1381  0.0  0.0  22992  1220 ?        SNl  Aug21   0:00 /usr/lib/rtkit/rtkit-daemon
root      1388  0.0  0.2   9660  5016 ?        S    Aug21   0:02 /usr/lib/policykit-1/polkitd
root      1638  0.0  0.1  16140  3204 ?        Sl   Aug21   0:01 /usr/lib/udisks/udisks-daemon
root      1639  0.0  0.0   5620   724 ?        S    Aug21   0:04 udisks-daemon: polling /dev/sr0
root      3261  0.0  0.0      0     0 ?        S    Aug21   0:00 [migration/1]
root      3262  0.0  0.0      0     0 ?        S    Aug21   0:01 [ksoftirqd/1]
root      3263  0.0  0.0      0     0 ?        S    Aug21   0:00 [watchdog/1]
root      3264  0.0  0.0      0     0 ?        S    Aug21   0:00 [rtl92s_pci/1]
root      3265  0.0  0.0      0     0 ?        S    Aug21   0:00 [ext4-dio-unwrit]
root      3266  0.0  0.0      0     0 ?        S    Aug21   0:00 [kconservative/1]
root      3267  0.0  0.0      0     0 ?        S    Aug21   0:20 [kondemand/1]
root      3268  0.0  0.0      0     0 ?        S    Aug21   0:00 [kmpathd/1]
root      3269  0.0  0.0      0     0 ?        S    Aug21   0:00 [crypto/1]
root      3270  0.0  0.0      0     0 ?        S    Aug21   0:00 [aio/1]
root      3271  0.0  0.0      0     0 ?        S    Aug21   0:00 [ata_sff/1]
root      3272  0.0  0.0      0     0 ?        S    Aug21   0:00 [kblockd/1]
root      3273  0.0  0.0      0     0 ?        S    Aug21   0:00 [kintegrityd/1]
root      3274  0.0  0.0      0     0 ?        S    Aug21   0:00 [events/1]
root      4315  0.0  0.0   2628  1036 ?        S<   Aug21   0:00 udevd --daemon
root      4341  0.0  0.0   2628  1032 ?        S<   Aug21   0:00 udevd --daemon
root     11321  0.0  0.0   1896   512 ?        S    Aug21   0:00 /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root     11322  0.0  0.4  12148  8528 ?        S    Aug21   0:00 /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
root     11328  0.0  0.0      0     0 ?        Z    Aug21   0:00 [dpkg-preconfigu] <defunct>
root     11331  0.0  0.1   6204  2480 ?        S    Aug21   0:00 /usr/bin/perl -w /tmp/postfix.config.113291 configure 
root     12298 94.6  0.0   5720  1664 ?        R    Aug21  77:38 whiptail --backtitle Package configuration --title Postfix Configuration --output-fd 12 --msgbox Please
root     12534  0.0  0.1  21544  3864 ?        Sl   Aug21   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root     12537  1.4  1.5  60540 32248 tty8     Ss+  Aug21   1:07 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-AY1XiC/database -nolisten tcp
gdm      12558  0.0  0.0   3456   576 ?        S    Aug21   0:00 /usr/bin/dbus-launch --exit-with-session
root     12577  0.0  0.1  19872  3140 ?        Sl   Aug21   0:00 /usr/lib/gdm/gdm-session-worker
user     12769  0.0  0.1  41376  2928 ?        Sl   Aug21   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
user     12788  0.0  0.3  34804  7144 ?        Ssl  Aug21   0:00 gnome-session
user     12818  0.0  0.0   3348   200 ?        Ss   Aug21   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
user     12821  0.0  0.0   3456   584 ?        S    Aug21   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
user     12822  0.0  0.0   4552  1808 ?        Ss   Aug21   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
user     12827  0.0  0.2   9284  4228 ?        S    Aug21   0:01 /usr/lib/libgconf2-4/gconfd-2
user     12834  0.0  0.6 144780 13284 ?        Ssl  Aug21   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
user     12835  0.0  0.3  30056  8140 ?        Sl   Aug21   0:00 gnome-power-manager
user     12840  0.0  0.1   7420  2344 ?        S    Aug21   0:00 /usr/lib/gvfs/gvfsd
user     12845  0.0  0.1  30652  2108 ?        Ssl  Aug21   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/user/.gvfs
user     12850  0.0  0.2  19264  5872 ?        S    Aug21   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
user     12851  0.0  0.7 124284 16080 ?        SLl  Aug21   0:02 nm-applet --sm-disable
user     12854  0.0  0.4  38456  9504 ?        Sl   Aug21   0:00 /usr/lib/evolution/2.30/evolution-alarm-notify
user     12855  0.0  0.7  79928 15352 ?        Sl   Aug21   0:01 gnome-panel
user     12857  0.2  1.2  72064 25484 ?        Sl   Aug21   0:09 /usr/bin/compiz
user     12858  0.0  0.2  95460  4756 ?        S<sl Aug21   0:00 /usr/bin/pulseaudio --start --log-target=syslog
user     12859  0.0  1.3 131736 28280 ?        Sl   Aug21   0:02 nautilus
user     12860  0.0  0.4  73212  9288 ?        Sl   Aug21   0:00 bluetooth-applet
user     12889  0.0  0.4  47180  8344 ?        Sl   Aug21   0:00 /usr/lib/evolution/e-calendar-factory
user     12895  0.0  0.1  51552  3744 ?        Ssl  Aug21   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
user     12901  0.0  0.1  20680  3296 ?        Sl   Aug21   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
user     12907  0.0  0.1   7800  2808 ?        S    Aug21   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
user     12928  0.0  0.4  54828  8624 ?        Sl   Aug21   0:00 /usr/lib/evolution/e-addressbook-factory
user     12930  0.0  0.6  78452 14008 ?        Sl   Aug21   0:02 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=22
user     12932  0.0  0.1   8816  3312 ?        S    Aug21   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
user     12933  0.0  0.5  76792 10872 ?        Sl   Aug21   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-
user     12944  0.0  0.1  18000  2260 ?        Sl   Aug21   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
user     12948  0.0  0.0   3908   912 ?        S    Aug21   0:00 syndaemon -i 0.5 -k
user     12949  0.0  0.1   8192  2196 ?        S    Aug21   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
user     12952  0.0  0.0   1896   512 ?        Ss   Aug21   0:00 /bin/sh -c /usr/bin/compiz-decorator
user     12953  0.0  0.4  28960 10072 ?        Sl   Aug21   0:00 /usr/bin/gtk-window-decorator
user     12963  0.0  0.6  86556 13448 ?        Sl   Aug21   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet
user     12964  0.0  0.6  40892 14348 ?        Sl   Aug21   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=32
user     12965  0.0  0.6  86196 13080 ?        Sl   Aug21   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oa
user     12966  0.0  0.4  31008  8912 ?        Sl   Aug21   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Fa
user     12981  0.0  0.1   7820  2508 ?        S    Aug21   0:00 /usr/lib/gvfs/gvfsd-metadata
user     12983  0.0  0.2  26928  4904 ?        Sl   Aug21   0:00 /usr/lib/indicator-session/indicator-session-service
user     12984  0.0  0.2  87264  5284 ?        S    Aug21   0:00 /usr/lib/indicator-sound/indicator-sound-service
user     12988  0.0  0.2  27996  4856 ?        Sl   Aug21   0:00 /usr/lib/indicator-me/indicator-me-service
user     12991  0.0  0.1  15720  3644 ?        S    Aug21   0:00 /usr/lib/indicator-application/indicator-application-service
user     12992  0.0  0.2  18060  4140 ?        S    Aug21   0:00 /usr/lib/indicator-messages/indicator-messages-service
user     12997  0.0  0.1   7452  2412 ?        S    Aug21   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/1
user     13014  0.0  0.2  26820  5588 ?        Ss   Aug21   0:00 gnome-screensaver
user     13027  0.0  0.3  19120  6656 ?        S    Aug21   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
user     13037  0.0  0.7  32420 15536 ?        S    Aug21   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
user     13040  0.0  0.6  75240 12372 ?        Sl   Aug21   0:00 /usr/lib/notify-osd/notify-osd
user     13054  0.0  0.7  94916 15188 ?        Sl   Aug21   0:03 gnome-terminal
user     13057  0.0  0.0   2052   716 ?        S    Aug21   0:00 gnome-pty-helper
user     13078  0.0  0.5  75140 12036 ?        Sl   Aug21   0:00 update-notifier
root     13106  0.0  0.1   7136  2808 ?        S    Aug21   0:00 /usr/sbin/pppd nodetach lock nodefaultroute user IABDELLANI plugin rp-pppoe.so nic-eth0 noauth nodeflat
user     13110  3.2  7.3 629236 149880 ?       Sl   Aug21   2:05 /usr/lib/firefox-6.0/firefox-bin
user     13222  0.6  1.0 109248 22464 ?        Sl   Aug21   0:23 /usr/lib/firefox-6.0/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/li
user     13229  0.0  0.2  28332  4808 ?        Sl   Aug21   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.10 /org/gtk/gvfs/exec_spaw/2
user     13428  0.0  0.1   6896  3560 pts/1    Ss   Aug21   0:00 bash
user     14623  0.0  0.0   4588  1100 pts/1    R+   00:27   0:00 ps -aux

```

---

### Post by rodrigr2006 on 2011-09-14
Your thread is marked solved, did you get it fixed?  If not, what happens when you use the software center or synaptic?

---

### Post by psrdotcom on 2011-09-14
If your problem not solved, then this may help you

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/260319](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/260319)

---

