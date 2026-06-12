---
title: "High CPU Usage in Ubuntu and Kubuntu (9.10)"
date: 2010-02-12
forum: General Help
---

### Post by lucasreece on 2010-02-12
Looking for some help here please guys.

I'm running desktop machine with with a core2 duo E6400 with 2GB RAM. I have completed a fresh install of Ubuntu 9.10 (fully updated). I have 10GB root, 2GB swap, 10GB home and 80GB data parititons.

I log in to main administrator account (first boot), create a new user (desktop) account and then use the switch user to log into the desktop account (so logged in to two accounts at the same time).

Whilst logged into the desktop account the CPU usage as seen in system monitor shows the two CPU's alternating at around 100% and the system slows down greatly.

Any ideas what's going on here? Not sure where to start so looking for some advice please.

Many thanks.

---

### Post by lovinglinux on 2010-02-12
It could be the vino-server behaving badly. Go to "System >> Preferences >> Startup Applications (aka Session)" and disable "Remote Desktop" then reboot.

---

### Post by ajgreeny on 2010-02-12
You may also get a clue about what is using all your cpu by running ```
top
``` in a terminal.  By default that will list all the processes running in order of cpu usage, so look at what is top of the list and report back if needed.

---

### Post by lucasreece on 2010-02-12
I've tried running top but how can I get the results from that and post on here? In the terminal there's no option to select all to then copy the results.

Sorry, I'm pretty new to all this.

I've just tried exactly the same thing on my netbook and CPU usage is normal (nowhere near 100%). Both CPU's report generally 6% (CPU1) and about 14% (CPU2) or thereabouts.

On the machine in question might that indicate a problem with the CPU I wonder?

I'm at work at the moment so can't access my home machine but will report back later (if I can the results from top copied and pasted in here).

Thanks guys.

---

### Post by ironclaw on 2010-02-12
You can use "ps aux" in a terminal to output static information about all processes. Run 
```
ps aux > cpu-usage
```
to save the output to the file 'cpu-usage'.

---

### Post by lucasreece on 2010-02-12
[FONT="Courier New"][FONT="Courier New"]Just found the same with Linux Mint * (obviously based on 9.10) and exactly the same problem.

Here's the result...

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.0   2528  1496 ?        Ss   21:09   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   21:09   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   21:09   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   21:09   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   21:09   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   21:09   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   21:09   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   21:09   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   21:09   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   21:09   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   21:09   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   21:09   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   21:09   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S<   21:09   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S<   21:09   0:00 [kintegrityd/0]
root        16  0.0  0.0      0     0 ?        S<   21:09   0:00 [kintegrityd/1]
root        17  0.0  0.0      0     0 ?        S<   21:09   0:00 [kblockd/0]
root        18  0.0  0.0      0     0 ?        S<   21:09   0:00 [kblockd/1]
root        19  0.0  0.0      0     0 ?        S<   21:09   0:00 [kacpid]
root        20  0.0  0.0      0     0 ?        S<   21:09   0:00 [kacpi_notify]
root        21  0.0  0.0      0     0 ?        S<   21:09   0:00 [kacpi_hotplug]
root        22  0.0  0.0      0     0 ?        S<   21:10   0:00 [ata/0]
root        23  0.0  0.0      0     0 ?        S<   21:10   0:00 [ata/1]
root        24  0.0  0.0      0     0 ?        S<   21:10   0:00 [ata_aux]
root        25  0.0  0.0      0     0 ?        S<   21:10   0:00 [ksuspend_usbd]
root        26  0.0  0.0      0     0 ?        S<   21:10   0:00 [khubd]
root        27  0.0  0.0      0     0 ?        S<   21:10   0:00 [kseriod]
root        28  0.0  0.0      0     0 ?        S<   21:10   0:00 [kmmcd]
root        29  0.0  0.0      0     0 ?        S<   21:10   0:00 [bluetooth]
root        30  0.0  0.0      0     0 ?        S    21:10   0:00 [khungtaskd]
root        31  0.0  0.0      0     0 ?        S    21:10   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S    21:10   0:00 [pdflush]
root        33  0.0  0.0      0     0 ?        S<   21:10   0:00 [kswapd0]
root        34  0.0  0.0      0     0 ?        S<   21:10   0:00 [aio/0]
root        35  0.0  0.0      0     0 ?        S<   21:10   0:00 [aio/1]
root        36  0.0  0.0      0     0 ?        S<   21:10   0:00 [ecryptfs-kthrea]
root        37  0.0  0.0      0     0 ?        S<   21:10   0:00 [crypto/0]
root        38  0.0  0.0      0     0 ?        S<   21:10   0:00 [crypto/1]
root        42  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_0]
root        43  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_1]
root        44  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_2]
root        45  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_3]
root        46  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_4]
root        47  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_5]
root        53  0.0  0.0      0     0 ?        S<   21:10   0:00 [kstriped]
root        54  0.0  0.0      0     0 ?        S<   21:10   0:00 [kmpathd/0]
root        55  0.0  0.0      0     0 ?        S<   21:10   0:00 [kmpathd/1]
root        56  0.0  0.0      0     0 ?        S<   21:10   0:00 [kmpath_handlerd]
root        57  0.0  0.0      0     0 ?        S<   21:10   0:00 [ksnapd]
root        58  0.0  0.0      0     0 ?        S<   21:10   0:00 [kondemand/0]
root        59  0.0  0.0      0     0 ?        S<   21:10   0:00 [kondemand/1]
root        60  0.0  0.0      0     0 ?        S<   21:10   0:00 [kconservative/0]
root        61  0.0  0.0      0     0 ?        S<   21:10   0:00 [kconservative/1]
root        62  0.0  0.0      0     0 ?        S<   21:10   0:00 [krfcommd]
root       316  0.0  0.0      0     0 ?        S<   21:10   0:00 [scsi_eh_6]
root       317  0.0  0.0      0     0 ?        S<   21:10   0:00 [usb-storage]
root       332  0.0  0.0      0     0 ?        S<   21:10   0:00 [usbhid_resumer]
root       428  0.0  0.0      0     0 ?        S<   21:10   0:00 [kjournald2]
root       476  0.0  0.0   2280   828 ?        S    21:10   0:00 upstart-udev-bridge --daemon
root       480  0.0  0.0   2752  1152 ?        S<s  21:10   0:00 udevd --daemon
root       669  0.0  0.0   2748  1132 ?        S<   21:10   0:00 udevd --daemon
root       688  0.0  0.0   2748  1136 ?        S<   21:10   0:00 udevd --daemon
root       718  0.0  0.0      0     0 ?        S<   21:10   0:00 [hd-audio0]
root       765  0.0  0.0      0     0 ?        D<   21:10   0:00 [kjournald2]
root       793  0.0  0.0      0     0 ?        S<   21:10   0:00 [kpsmoused]
root       863  0.0  0.0      0     0 ?        S<   21:10   0:00 [kjournald2]
root       872  0.0  0.0   1848   548 ?        Ss   21:10   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
syslog     898  0.0  0.0  34852  1808 ?        Sl   21:10   0:00 rsyslogd -c4
102        955  0.1  0.0   3600  1764 ?        Ss   21:10   0:00 dbus-daemon --system --fork
107        961  0.0  0.2   6284  4228 ?        Ss   21:10   0:00 hald --daemon=yes
avahi      965  0.0  0.0   2820  1492 ?        Ss   21:10   0:00 avahi-daemon: running [dde520-mint-gno.local]
avahi      966  0.0  0.0   2820   532 ?        Ss   21:10   0:00 avahi-daemon: chroot helper
root       967  0.0  0.1  20428  2956 ?        Ssl  21:10   0:00 /usr/sbin/console-kit-daemon
root      1030  0.0  0.0   3336  1220 ?        S    21:10   0:00 hald-runner
root      1034  0.0  0.1  18576  3736 ?        Ssl  21:10   0:00 NetworkManager
root      1045  0.0  0.1   3904  2108 ?        S    21:10   0:00 /usr/sbin/modem-manager
root      1066  0.0  0.0   4932  1656 ?        S    21:10   0:00 /sbin/wpa_supplicant -u -s
root      1104  0.0  0.0   3412  1140 ?        S    21:10   0:00 hald-addon-input: Listening on /dev/input/event13 /dev/input/event0 /dev/input/event1 /dev/input/event3
root      1105  0.0  0.0   3412  1136 ?        S    21:10   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      1106  0.0  0.0   3412  1144 ?        S    21:10   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      1107  0.0  0.0   3412  1140 ?        S    21:10   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
root      1117  0.0  0.0   3412  1140 ?        S    21:10   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1119  0.0  0.0   2140   944 ?        S    21:10   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-258f3b37-a7d5-4c5d-8833-b8176720c497-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
107       1120  0.0  0.0   3256  1136 ?        S    21:10   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1121  0.0  0.0   3412  1140 ?        S    21:10   0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
root      1237  0.0  0.1   8616  3380 ?        Ss   21:10   0:00 gdm-binary
root      1329  0.0  0.0   1700   544 tty4     Ss+  21:10   0:00 /sbin/getty -8 38400 tty4
root      1333  0.0  0.0   1700   544 tty5     Ss+  21:10   0:00 /sbin/getty -8 38400 tty5
root      1349  0.0  0.0   1700   548 tty2     Ss+  21:10   0:00 /sbin/getty -8 38400 tty2
root      1350  0.0  0.0   1700   548 tty3     Ss+  21:10   0:00 /sbin/getty -8 38400 tty3
root      1352  0.0  0.0   1700   544 tty6     Ss+  21:10   0:00 /sbin/getty -8 38400 tty6
root      1355  0.0  0.0   1972   864 ?        Ss   21:10   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1357  0.0  0.0   1960   420 ?        Ss   21:10   0:00 atd
root      1358  0.0  0.0   2088   860 ?        Ss   21:10   0:00 cron
kernoops  1359  0.0  0.0   3340   912 ?        Ss   21:10   0:00 /usr/sbin/kerneloops
root      1392  0.0  0.0   8888  1684 ?        Ss   21:10   0:00 /usr/sbin/nmbd -D
root      1398  0.0  0.1  15856  2868 ?        Ss   21:10   0:00 /usr/sbin/smbd -D
root      1435  0.0  0.1   6756  2516 ?        Ss   21:10   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1502  0.0  0.0  15856  1316 ?        S    21:10   0:00 /usr/sbin/smbd -D
root      1638  0.0  0.0   1700   548 tty1     Ss+  21:10   0:00 /sbin/getty -8 38400 tty1
root      1653  0.0  0.1   5140  2520 ?        S    21:10   0:00 /usr/lib/devicekit-power/devkit-power-daemon
root      1686  0.0  0.0   1892   808 ?        Ss   21:10   0:00 anacron -s
root      1943  0.0  0.1   7212  3676 ?        S    21:10   0:00 /usr/lib/policykit-1/polkitd
root      1967  0.0  0.1   5068  2832 ?        S    21:10   0:00 /usr/lib/devicekit-disks/devkit-disks-daemon
root      1972  0.0  0.0   4820   748 ?        S    21:10   0:00 devkit-disks-daemon: polling /dev/sdb /dev/sr0 /dev/sdc /dev/sdd /dev/sde
root      2019  0.0  0.1   4852  2476 ?        S    21:10   0:00 /usr/sbin/system-tools-backends
root      2021  0.0  0.5  12520 10648 ?        S    21:10   0:00 /usr/bin/perl /usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
root      2282  0.0  0.1   8540  3452 ?        S    21:12   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      2283 10.6  1.9  62392 39916 tty7     Ss+  21:12   0:39 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-o9g7By/database -nolisten tcp
gdm       2318  0.0  0.0   3380   712 ?        S    21:12   0:00 /usr/bin/dbus-launch --exit-with-session
root      2352  0.0  0.1  10888  3384 ?        S    21:12   0:00 /usr/lib/gdm/gdm-session-worker
lucas     2371  0.0  0.1  40720  3520 ?        Sl   21:12   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
lucas     2386  0.0  0.5  39280 11744 ?        Ssl  21:12   0:00 gnome-session
lucas     2423  0.0  0.0   4916   612 ?        Ss   21:12   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
lucas     2426  0.0  0.0   2972  1164 ?        Ss   21:12   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
lucas     2427  0.0  0.0   3380   696 ?        S    21:12   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
lucas     2431  0.0  0.2  94008  4456 ?        Ssl  21:12   0:00 /usr/bin/pulseaudio --start
lucas     2436  0.0  0.1  10628  2904 ?        S    21:12   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
lucas     2438  0.0  0.2   7480  4432 ?        S    21:12   0:00 /usr/lib/libgconf2-4/gconfd-2
lucas     2447  0.0  0.3  22436  7208 ?        Ss   21:12   0:00 seahorse-daemon
lucas     2449  0.0  0.4  96440  8760 ?        Ssl  21:12   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
lucas     2451  0.0  0.1   5752  2156 ?        S    21:12   0:00 /usr/lib/gvfs/gvfsd
lucas     2457  0.0  0.1  29788  2476 ?        Ssl  21:12   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/lucas/.gvfs
lucas     2476  0.0  0.3  17504  6364 ?        S    21:12   0:00 /usr/lib/notify-osd/notify-osd
lucas     2477  0.0  0.0   1748   556 ?        S    21:12   0:00 /bin/sh /usr/bin/compiz
lucas     2550  0.3  0.9  29748 20576 ?        S    21:12   0:01 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id 10cb350e095f3a6010126600915714567500000023860022 move resize place decoration animation ccp
lucas     2551  0.1  0.8  42304 16512 ?        S    21:12   0:00 gnome-panel
lucas     2552  0.2  1.2  90192 26516 ?        S    21:12   0:01 nautilus
lucas     2554  0.0  0.1  41612  3352 ?        Ssl  21:12   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
lucas     2560  0.0  0.2  16628  5640 ?        S    21:12   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
lucas     2562  0.0  0.7  29560 14436 ?        S    21:12   0:00 python /usr/share/system-config-printer/applet.py
lucas     2564  0.0  0.3  17600  7296 ?        S    21:12   0:00 bluetooth-applet
lucas     2575  0.0  0.6  39276 14276 ?        S    21:12   0:00 nm-applet --sm-disable
lucas     2582  0.8  1.5  64840 32784 ?        Sl   21:12   0:02 python /usr/lib/linuxmint/mintMenu/mintMenu.py --oaf-activate-iid=OAFIID:GNOME_mintMenu_Factory --oaf-ior-fd=18
lucas     2584  0.0  0.0   4492  1548 ?        S    21:12   0:00 bash /usr/bin/tomboy-panel --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=24
lucas     2587  0.0  0.3  17636  6980 ?        S    21:12   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
lucas     2591  0.0  0.5 170648 11600 ?        Sl   21:12   0:00 gnome-volume-control-applet
lucas     2593  0.2  1.2  58448 26216 ?        Sl   21:12   0:00 mono /usr/lib/tomboy/Tomboy.exe --sm-disable --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=24
lucas     2595  0.0  0.3  17744  7392 ?        S    21:12   0:00 gnome-power-manager
lucas     2598  0.0  0.2  17884  4180 ?        Ss   21:12   0:00 gnome-screensaver
lucas     2604  0.0  0.1   6204  2804 ?        S    21:12   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
lucas     2617  0.0  0.1   6516  3016 ?        S    21:12   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
lucas     2624  0.0  0.1   6592  2208 ?        S    21:12   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
lucas     2631  0.0  0.0   1748   484 ?        Ss   21:12   0:00 /bin/sh -c /usr/bin/compiz-decorator
lucas     2632  0.0  0.4  19848  9324 ?        S    21:12   0:00 /usr/bin/gtk-window-decorator
lucas     2656  0.0  0.1   5756  2252 ?        S    21:12   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
lucas     2658  6.4  0.8  37516 18440 ?        S    21:12   0:21 gnome-system-monitor
lucas     2659  0.0  0.0      0     0 ?        Z    21:13   0:00 [gnome-session-s] <defunct>
root      2662  0.0  0.1   8540  3452 ?        S    21:13   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display2
root      2666 84.1  1.3  40328 28732 tty9     Rs+  21:13   3:54 /usr/bin/X :1 -br -verbose -auth /var/run/gdm/auth-for-gdm-IwspSp/database -nolisten tcp
lucas     2703  0.0  0.2  17676  5520 ?        S    21:13   0:00 /usr/lib/gnome-screensaver/gnome-screensaver-gl-helper
gdm       2707  0.0  0.0   3380   712 ?        S    21:13   0:00 /usr/bin/dbus-launch --exit-with-session
root      2741  0.0  0.1  10888  3384 ?        S    21:14   0:00 /usr/lib/gdm/gdm-session-worker
tester    2760  0.0  0.1  40720  3500 ?        Sl   21:14   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
tester    2775  0.0  0.3  25580  6560 ?        Ssl  21:14   0:00 gnome-session
tester    2814  0.0  0.0   4916   612 ?        Ss   21:14   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
tester    2817  0.0  0.0   3380   704 ?        S    21:14   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
tester    2818  0.0  0.0   2972  1164 ?        Ss   21:14   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
tester    2822  0.0  0.2  94008  4464 ?        Ssl  21:14   0:00 /usr/bin/pulseaudio --start
tester    2825  0.0  0.1  10628  2908 ?        S    21:14   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
tester    2827  0.0  0.2   7484  4440 ?        S    21:14   0:00 /usr/lib/libgconf2-4/gconfd-2
tester    2836  0.0  0.3  22572  7268 ?        Ss   21:14   0:00 seahorse-daemon
tester    2838  0.0  0.4  96356  8696 ?        Rsl  21:14   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
tester    2841  0.0  0.1   5752  2152 ?        S    21:14   0:00 /usr/lib/gvfs/gvfsd
tester    2846  0.0  0.1  29788  2452 ?        Ssl  21:14   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/tester/.gvfs
tester    2865  0.0  0.3  17512  6360 ?        S    21:14   0:00 /usr/lib/notify-osd/notify-osd
tester    2866  0.0  0.5  28344 11360 ?        S    21:14   0:00 /usr/bin/metacity --replace
tester    2929  0.1  0.8  42340 16632 ?        S    21:14   0:00 gnome-panel
tester    2930  0.3  1.2  98336 26544 ?        S    21:14   0:00 nautilus
tester    2932  0.0  0.1  41612  3392 ?        Ssl  21:14   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
tester    2942  0.0  0.0   4492  1548 ?        S    21:14   0:00 bash /usr/bin/tomboy-panel --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=18
tester    2944  0.8  1.5  63176 31148 ?        Sl   21:14   0:02 python /usr/lib/linuxmint/mintMenu/mintMenu.py --oaf-activate-iid=OAFIID:GNOME_mintMenu_Factory --oaf-ior-fd=24
tester    2947  0.3  1.2  56712 25212 ?        Sl   21:14   0:00 mono /usr/lib/tomboy/Tomboy.exe --sm-disable --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=18
tester    2951  0.0  0.2  16616  5656 ?        S    21:14   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
tester    2959  0.0  0.7  29568 14460 ?        S    21:14   0:00 python /usr/share/system-config-printer/applet.py
tester    2961  0.0  0.3  17608  7360 ?        S    21:14   0:00 bluetooth-applet
tester    2968  0.0  0.3  17692  7012 ?        S    21:14   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
tester    2970  0.0  0.5  96804 11212 ?        S    21:14   0:00 gnome-volume-control-applet
tester    2971  0.0  0.3  17760  7544 ?        S    21:14   0:00 gnome-power-manager
tester    2978  0.0  0.1  17876  2728 ?        Ss   21:14   0:00 gnome-screensaver
tester    2988  0.0  0.1   6204  2728 ?        S    21:14   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
tester    2996  0.0  0.1   6516  2936 ?        S    21:14   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
tester    2998  0.0  0.1   6592  2204 ?        S    21:14   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
tester    3007  0.0  0.1   5756  2252 ?        S    21:14   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
tester    3008  0.4  0.8  37168 17288 ?        S    21:14   0:01 gnome-system-monitor
tester    3009  0.0  0.6  39688 12616 ?        Sl   21:14   0:00 gnome-terminal
tester    3010  0.0  0.0   1900   712 ?        S    21:15   0:00 gnome-pty-helper
tester    3011  0.0  0.1   6192  3484 pts/0    Ss   21:15   0:00 bash
tester    3030  2.7  3.0 277484 63568 ?        Sl   21:15   0:05 /usr/lib/firefox-3.5.3/firefox
root      3046  0.0  0.0   1748   492 ?        S    21:15   0:00 /bin/sh -c nice run-parts --report /etc/cron.daily
root      3047  0.0  0.0   1664   556 ?        SN   21:15   0:00 run-parts --report /etc/cron.daily
root      3052  0.0  0.0   1748   548 ?        SN   21:15   0:00 /bin/sh /etc/cron.daily/apt
root      3080  0.0  0.0   1684   436 ?        SN   21:15   0:00 sleep 783
tester    3114  0.0  0.0   2640  1016 pts/0    R+   21:18   0:00 ps aux


The line "root      2666 84.1  1.3  40328 28732 tty9     Rs+  21:13   3:54 /usr/bin/X :1 -br -verbose -auth /var/run/gdm/auth-for-gdm-IwspSp/database -nolisten tcp" looks a bit dubious. Any ideas please?[FONT="Courier New"][/FONT][/FONT][/FONT]

---

### Post by lucasreece on 2010-02-12
> **lovinglinux said:**
> It could be the vino-server behaving badly. Go to "System >> Preferences >> Startup Applications (aka Session)" and disable "Remote Desktop" then reboot.
Thanks for the suggestion but tried this in the Mint Gnome but still the same problem.

---

### Post by ajgreeny on 2010-02-12
Your problem is shown here in your posted output, at 84.1 cpu usage:-
> [FONT=Courier New][FONT=Courier New]root 2666 84.1 1.3 40328 28732 tty9 Rs+ 21:13 3:54 /usr/bin/X :1 -br -verbose -auth /var/run/gdm/auth-for-gdm-IwspSp/database -nolisten tcp[/FONT][/FONT]
Unfortunately, I don't really understand what it all means, but am surprised to see a tty9 noted.  I thought ubuntu ran only up to tty7. It looks as if gdm is something to do with the problem in some way, but have no idea how to help you solve it, other than suggesting you try reinstalling gdm, or removing the autologin, if you have that enabled.

---

### Post by lucasreece on 2010-02-12
mmmm... thanks for the reply. I don't have a clue either or even where to start. Anyone?

I will do what you suggest and re-install gdm. No, dont have autologin enabled. Seems wierd it's happening on Ubuntu, Kubuntu and Mint. My laptop and netbook run fine. The affected machine is a Dell Dimension E520, E6300 (not E6400 as previously stated) Core2 Duo with 2GB RAM. As I say, as default fresh install.

---

### Post by lucasreece on 2010-02-12
Just re-installed gdm, rebooted but still the same! aaaaarrrrhhhh :o

---

### Post by ironclaw on 2010-02-12
```
root 2283 10.6 1.9 62392 39916 tty7 Ss+ 21:12 0:39 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-o9g7By/database -nolisten tcp
root 2666 84.1 1.3 40328 28732 tty9 Rs+ 21:13 3:54 /usr/bin/X :1 -br -verbose -auth /var/run/gdm/auth-for-gdm-IwspSp/database -nolisten tcp
```

There are two X server displays running - I don't think that's normal. It's the second one that's using up all the CPU time.

I'm not sure - maybe have a look in the Xorg logs in /var/log/. Or try
```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure the X server.

---

### Post by ajgreeny on 2010-02-13
Unfortunately there is no point in using that command any more.  It has been deprecated for the last few versions of ubuntu and will now do precisely nothing.

X is now expected to successfully detect everything and set it up automatically; it's only when it doesn't do so that other more difficult means have to be found.

Do you have two graphics cards in your machine, one pci and one on-board perhaps,which might account for the two x-servers, which I hadn't noticed?

---

### Post by lucasreece on 2010-02-13
> **ajgreeny said:**
> Do you have two graphics cards in your machine, one pci and one on-board perhaps,which might account for the two x-servers, which I hadn't noticed?

One graphics card. It's an ATI X1300 Pro.

---

### Post by lucasreece on 2010-02-15
Anyone any other ideas please?

---

### Post by Jaok on 2010-02-24
I seem to have the same problem with my machine (AMD Athlon X2, ATI Radeon X1200 onboard, 2GB Ram, Ubuntu 9.10 x64, fresh install) and have no idea how to solve it.

Everytime I log in with a second user (via System->Logout->Switch user), surfing the internet with Firefox or anything else is very slow for the poor person who logged in afterwards.
I notice a high CPU load of the second Xorg. User 1's performance is not affected.

> **ironclaw said:**
> 
There are two X server displays running - I don't think that's normal. It's the second one that's using up all the CPU time.


I think having two Xs might be the normal behavior, because every logged in user gets his X-server running on an own virtual terminal. For me the first user goes on VT 7 and the second on VT 9. I can easily switch between them using ctrl-alt-F7 or -F9.

Any help would be appreciated :-)

---

### Post by lucasreece on 2010-03-01
Bump.

Anyone any help please? Do I need to file a bug? If so how do I do that please?

---

