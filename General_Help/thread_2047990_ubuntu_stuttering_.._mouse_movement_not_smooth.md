---
title: "ubuntu stuttering .. mouse movement not smooth"
date: 2012-08-25
forum: General Help
---

### Post by paichkash on 2012-08-25
hi
i have ubuntu 10.10 .. its running like crap.. when i open just 3 of the ubuntforums pages in opera 11  it stutters and hangs.. there is a delay in typin txt in a post.... also even without any anthing open on fresh reboot  wehn i just open the nautilius it behaves like tihs.. 
while my system requirements are low such as PIII with 1ghz. 512 MB RAM and 256 MB AGP nVidia 5500..

how to put the output of top command in a file so i can post here..

i tried top > mytop.dat but the result was garbled text i tried opening in gvim and in kate but the text made no sense.. there were strange characteres..
i think i have installed some shitware on my old pc which is making it run like crap..

also i ahve earlier been runing ubuntu 9,04 flawlessly .. but whenever i asked qestions i was pissed and harrased to upgrade ... tried latest 12 and found that pathatecially slow and bloated tired 11 .. same bloated .. tired 10.10 its also runing like shiiit.. i am just normal casual home user who want to learn linux for fun.. especiall the CLI portion..

---

### Post by sienile on 2012-08-25
Did you make a swap partition? If not, adding one might help things.

---

### Post by lakerssuperman on 2012-08-26
How did you upgrade?  Was it an upgrade via the Software Manager or did you do a clean install?  

You may want to try disabling the Compiz effects and see if that takes care of the problem.  The further up the release ladder you go the higher the system requirements get, especially with Compiz.  You would lose the eyecandy, but gain back a usuable desktop.

You may also want to consider backing up your settings and deleting the hidden settings files in your home directory.  I have occasionally upgraded a system and retained my home directory and settings only to find it was messing with the new install.  One way to check if this is the case is to create a temporary test user account to see if you are having the same problems in this new account.  If not then you may have some left over garbage from the previous release.

---

### Post by 2F4U on 2012-08-26
With respect to the top problem try:

```
top -b > test.txt
```

You will get several iterations in the file, depending on how long the command runs. Terminate the program with Ctrl-C.

---

### Post by paichkash on 2012-08-26
i did fresh install.. using ext4 fs.. and also swap is there and activated..swap partition is 1.5 gb ..compiz is disabled.. nvidia driver 173 is installed.. how can i try using alternative driver versiomn like 96 (?) that i think in the past worked flawlessly..

---

### Post by paichkash on 2012-08-26
i also tried kde and xfce .. while kde was faucking slow on fresh boot and ram usage hit sky high then gnome .. xfce on the otherhand was light on fresh boot but as soon i loaded any browser with few tabs of ubuntu forums r opened a low quality mp4 file it stareted to stutter more ..

---

### Post by beboylips on 2012-08-26
run

```


ps aux > ps.txt


```

and paste it here. Or paste the output of the top command. We need to see what's using your resources.

---

### Post by paichkash on 2012-08-26
i ended up formating and reinstalling 10.10 now its fine.. but for the sake of refrence for future problems i will post the output of currently working fine version of ubuntu..


ps aux > ps.txt
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   2872  1364 ?        Ss   18:37   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    18:37   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    18:37   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    18:37   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    18:37   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    18:37   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    18:37   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    18:37   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    18:37   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    18:37   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    18:37   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    18:37   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    18:37   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    18:37   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    18:37   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    18:37   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    18:37   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    18:37   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    18:37   0:00 [ata_aux]
root        20  0.0  0.0      0     0 ?        S    18:37   0:00 [ata_sff/0]
root        21  0.0  0.0      0     0 ?        S    18:37   0:00 [khubd]
root        22  0.0  0.0      0     0 ?        S    18:37   0:00 [kseriod]
root        23  0.0  0.0      0     0 ?        S    18:37   0:00 [kmmcd]
root        25  0.0  0.0      0     0 ?        S    18:37   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S    18:37   0:01 [kswapd0]
root        27  0.0  0.0      0     0 ?        SN   18:37   0:00 [ksmd]
root        28  0.0  0.0      0     0 ?        S    18:37   0:00 [aio/0]
root        29  0.0  0.0      0     0 ?        S    18:37   0:00 [ecryptfs-kthrea]
root        30  0.0  0.0      0     0 ?        S    18:37   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    18:37   0:00 [scsi_eh_0]
root        37  0.0  0.0      0     0 ?        S    18:37   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S    18:37   0:00 [kstriped]
root        41  0.0  0.0      0     0 ?        S    18:37   0:00 [kmpathd/0]
root        42  0.0  0.0      0     0 ?        S    18:37   0:00 [kmpath_handlerd]
root        43  0.0  0.0      0     0 ?        S    18:37   0:00 [ksnapd]
root        44  0.0  0.0      0     0 ?        S    18:37   0:00 [kondemand/0]
root        45  0.0  0.0      0     0 ?        S    18:37   0:00 [kconservative/0]
root       221  0.0  0.0      0     0 ?        S    18:37   0:00 [usbhid_resumer]
root       227  0.0  0.0      0     0 ?        S    18:37   0:00 [jbd2/sdb1-8]
root       228  0.0  0.0      0     0 ?        S    18:37   0:00 [ext4-dio-unwrit]
root       262  0.0  0.0      0     0 ?        S    18:37   0:00 [flush-8:16]
root       291  0.0  0.1   2392   604 ?        S    18:38   0:00 upstart-udev-bridge --daemon
root       293  0.0  0.0   2672   412 ?        S<s  18:38   0:00 udevd --daemon
root       407  0.0  0.0      0     0 ?        S    18:38   0:00 [kpsmoused]
root       460  0.0  0.0   2752   384 ?        S<   18:38   0:00 udevd --daemon
root       467  0.0  0.1   2752   684 ?        S<   18:38   0:00 udevd --daemon
root       476  0.0  0.0      0     0 ?        S    18:38   0:00 [kgameportd]
syslog     676  0.0  0.1  34596   908 ?        Sl   18:38   0:00 rsyslogd -c4
102        692  0.0  0.3   3608  1764 ?        Ss   18:38   0:01 dbus-daemon --system --fork
avahi      713  0.0  0.2   3012  1104 ?        S    18:38   0:00 avahi-daemon: running [rDR.local]
root       715  0.0  0.5  19476  2732 ?        Ssl  18:38   0:00 NetworkManager
avahi      719  0.0  0.0   3012   112 ?        S    18:38   0:00 avahi-daemon: chroot helper
root       731  0.0  0.3   4432  1704 ?        S    18:38   0:00 /usr/sbin/modem-manager
root       758  0.0  0.1   4900   816 ?        S    18:38   0:00 /sbin/wpa_supplicant -u -s
root       763  0.0  0.1   2300   532 ?        S    18:38   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-cd748d25-4a50-441e-9f5e-ed76216ff18d-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root       843  0.0  0.0   1856   428 tty4     Ss+  18:38   0:00 /sbin/getty -8 38400 tty4
root       847  0.0  0.0   1856   432 tty5     Ss+  18:38   0:00 /sbin/getty -8 38400 tty5
root       855  0.0  0.0   1856   432 tty2     Ss+  18:38   0:00 /sbin/getty -8 38400 tty2
root       857  0.0  0.0   1856   432 tty3     Ss+  18:38   0:00 /sbin/getty -8 38400 tty3
root       860  0.0  0.0   1856   432 tty6     Ss+  18:38   0:00 /sbin/getty -8 38400 tty6
root       861  0.0  0.0   2116   468 ?        Ss   18:38   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       865  0.0  0.1   2460   676 ?        Ss   18:38   0:00 cron
daemon     866  0.0  0.0   2316   180 ?        Ss   18:38   0:00 atd
root       893  0.0  0.0  13292   428 ?        Ss   18:38   0:00 /usr/sbin/winbindd
root       900  0.0  0.0  13292   340 ?        S    18:38   0:00 /usr/sbin/winbindd
root       936  0.0  0.5  19848  2872 ?        Ssl  18:38   0:00 gdm-binary
root       946  0.0  0.2   6776  1508 ?        Ss   18:38   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root       959  0.0  0.4  19984  2192 ?        Sl   18:38   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1042  0.0  0.4  21548  2328 ?        Sl   18:38   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1059  7.9  4.8  59108 24552 tty7     Ss+  18:38   3:04 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-FLaKlp/database -nolisten tcp vt7
root      1157  0.0  0.0   1856   432 tty1     Ss+  18:38   0:00 /sbin/getty -8 38400 tty1
root      1166  0.0  0.4  20072  2036 ?        Sl   18:38   0:00 /usr/lib/gdm/gdm-session-worker
r         1175  0.0  1.2  34804  6164 ?        Ssl  18:38   0:00 gnome-session
r         1205  0.0  0.0   3348    16 ?        Ss   18:38   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
r         1208  0.0  0.0   3456   312 ?        S    18:38   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
r         1209  0.0  0.3   4356  1560 ?        Ss   18:38   0:02 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
r         1214  0.0  0.8   9300  4108 ?        S    18:38   0:01 /usr/lib/libgconf2-4/gconfd-2
r         1217  0.0  1.3  28524  6832 ?        Sl   18:38   0:00 gnome-power-manager
r         1222  0.0  0.3  24828  1580 ?        Sl   18:38   0:00 /usr/bin/gnome-keyring-daemon --start --components=ssh
r         1225  0.1  1.8  99520  9624 ?        Ssl  18:38   0:03 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root      1229  0.0  0.5   8436  2588 ?        S    18:38   0:00 /usr/lib/upower/upowerd
root      1249  0.0  0.7   9056  4036 ?        S    18:38   0:02 /usr/lib/policykit-1/polkitd
r         1256  0.0  0.4   7532  2076 ?        S    18:38   0:00 /usr/lib/gvfs/gvfsd
r         1280  0.0  0.3  30748  1908 ?        Ssl  18:38   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/r/.gvfs
r         1295  0.0  1.2  27784  6556 ?        Sl   18:38   0:00 bluetooth-applet
r         1297  0.0  1.3  38452  6964 ?        Sl   18:38   0:00 /usr/lib/evolution/2.30/evolution-alarm-notify
r         1300  2.8  6.0  53776 30808 ?        Sl   18:38   1:05 /usr/bin/compiz
r         1302  0.0  2.1  86508 10752 ?        Sl   18:38   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
r         1307  1.5  5.4 166564 27620 ?        Sl   18:38   0:36 nautilus
r         1308  0.5  2.8  91256 14480 ?        Sl   18:38   0:12 gnome-panel
r         1311  0.0  1.8 141936  9584 ?        Sl   18:38   0:00 nm-applet --sm-disable
r         1320  0.0  0.6 112160  3212 ?        S<sl 18:38   0:01 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1323  0.0  0.2  22992  1052 ?        SNl  18:38   0:00 /usr/lib/rtkit/rtkit-daemon
r         1360  0.0  0.5  20668  2756 ?        Sl   18:38   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
r         1376  0.0  0.5   7888  2788 ?        S    18:38   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.13 /org/gtk/gvfs/exec_spaw/0
r         1393  0.0  0.6  50668  3100 ?        Ssl  18:38   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
r         1397  0.0  0.6  33396  3304 ?        S    18:38   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1402  0.0  0.6  16340  3244 ?        Sl   18:38   0:00 /usr/lib/udisks/udisks-daemon
r         1403  0.0  0.5  26680  2672 ?        Ss   18:38   0:00 gnome-screensaver
root      1404  0.0  0.1   5612   660 ?        S    18:38   0:00 udisks-daemon: not polling any devices
r         1412  0.5  2.4  88984 12428 ?        Sl   18:38   0:11 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=22
r         1413  0.0  1.8  87344  9308 ?        Sl   18:38   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=28
r         1415  0.0  0.3  17992  1988 ?        Sl   18:38   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
r         1418  0.0  0.4   8172  2072 ?        S    18:38   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
r         1424  0.0  2.2  98112 11344 ?        Sl   18:38   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=25
r         1428  0.0  2.2  39948 11356 ?        Sl   18:38   0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=34
r         1429  0.0  2.3  96736 11700 ?        Sl   18:38   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=42
r         1430  0.0  1.5  31104  7664 ?        Sl   18:38   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=48
r         1432  0.0  0.4   7432  2152 ?        S    18:38   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.13 /org/gtk/gvfs/exec_spaw/1
r         1457  0.0  0.3   7316  1796 ?        S    18:38   0:00 /usr/lib/gvfs/gvfsd-metadata
r         1459  0.0  0.8  28004  4248 ?        Sl   18:38   0:00 /usr/lib/indicator-me/indicator-me-service
r         1463  0.0  1.1  19212  5956 ?        S    18:38   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
r         1465  0.0  0.9  27032  4748 ?        Sl   18:38   0:00 /usr/lib/indicator-session/indicator-session-service
r         1469  0.0  0.7  86836  3736 ?        S    18:38   0:00 /usr/lib/indicator-sound/indicator-sound-service
r         1471  0.0  0.6  15732  3244 ?        S    18:38   0:00 /usr/lib/indicator-application/indicator-application-service
r         1473  0.0  0.7  18200  3744 ?        S    18:38   0:00 /usr/lib/indicator-messages/indicator-messages-service
r         1474  0.0  0.0   1900   468 ?        Ss   18:38   0:00 /bin/sh -c /usr/bin/compiz-decorator
r         1475  0.1  1.7  28828  9128 ?        Sl   18:38   0:03 /usr/bin/gtk-window-decorator
r         1478  0.0  2.4  32424 12212 ?        S    18:38   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
r         1491  0.0  2.0  85704 10512 ?        Sl   18:39   0:01 update-notifier
root      1518  0.0  1.2  13932  6252 ?        S    18:39   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
r         1532  0.0  0.5  16084  2684 ?        S    18:39   0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.13 /org/gtk/gvfs/exec_spaw/2
r         1571  0.0  2.0  85380 10296 ?        Sl   18:39   0:01 /usr/lib/notify-osd/notify-osd
root      2872  0.0  0.5   5812  2640 ?        S    18:57   0:00 /usr/sbin/system-tools-backends
root      2874  0.0  1.7  12792  9052 ?        S    18:57   0:00 /usr/bin/perl /usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
root      2913  0.0  0.1   2052   676 ?        S    18:58   0:00 gnome-pty-helper
ntp       3070  0.0  0.2   4472  1280 ?        Ss   18:59   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 114:124
root      3163  0.0  0.1   3456   556 ?        S    19:02   0:00 dbus-launch --autolaunch=ebdd61ca9187febe671b29f00000000b --binary-syntax --close-stderr
root      3164  0.0  0.1   2756   840 ?        Ss   19:02   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
r         3172  9.4 14.2 152424 72204 ?        Sl   19:04   1:12 /usr/lib/opera/opera
r         3287  1.0  2.7 104004 13864 ?        Sl   19:14   0:01 gnome-terminal
r         3290  0.0  0.1   2052   684 ?        S    19:14   0:00 gnome-pty-helper
r         3291  0.4  0.6   6816  3440 pts/0    Ss   19:14   0:00 bash
root      3334  0.0  0.0      0     0 ?        S    19:15   0:00 [flush-0:20]
r         3407  0.0  0.2   4588  1060 pts/0    R+   19:17   0:00 ps aux
```

---

### Post by beboylips on 2012-08-29
Yeah everything seems as it should be. However, unless we get some statistics from the malfunctioning install, I doubt we will be able to help with it.

---

