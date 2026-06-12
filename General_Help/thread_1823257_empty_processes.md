---
title: "empty processes"
date: 2011-08-11
forum: General Help
---

### Post by mike555 on 2011-08-11
Anyone know what these are ? they show as empty processes .

[IMG]http://i55.tinypic.com/sys17k.jpg[/IMG]

---

### Post by MG&amp;TL on 2011-08-11
You could try saving your data and stopping them to see what happens. Only if you're brave though. :D

---

### Post by mike555 on 2011-08-11
I tried stopping them , they won't let me.

also I noticed the ID numbers change , and sometimes when I shut down it says "waiting for unknown to stop".

---

### Post by MG&amp;TL on 2011-08-11
Error message was...?

I don't know anything about this, I just spent quite a while one rainy day killing things to see what happened.

Do they show up on 'top' in a terminal? If so, you can forcibly stop them by typing 'top' then 'k' then entering the PID of the process, and then something like 'SIGKILL' (kills program off ultimately. not like the 'close' button at all, a lot nastier). As I said, only if you're brave, and have your documents saved.

---

### Post by AlphaLexman on 2011-08-11
What do mean by an 'Empty Process' ??

If the process is not using the cpu ??
If the process is not in memory ??

An **IDLE** process is not using the cpu...
An **EMPTY** process is active, but not in memory...

I don't see any 'empty processes' in your screenshot...

---

### Post by MG&amp;TL on 2011-08-11
He means the two totally blank ones at the top, that take no CPU, no RAM, and do nothing. ;)

---

### Post by AlphaLexman on 2011-08-11
> **MG&TL said:**
> He means the two totally blank ones at the top, that take no CPU, no RAM, and do nothing. ;)
Those processses are sleeping NOT active.

---

### Post by mike555 on 2011-08-11
Yes, I meant the top ones, sometimes there are 3 or 4 , when I click on one of them it unclicks itself ........ weird

---

### Post by MG&amp;TL on 2011-08-11
So he wants to know what they are doing there. Is there a wake up function or a last activity property or something like that?

---

### Post by haqking on 2011-08-11
use CLI

ps aux | less

---

### Post by AlphaLexman on 2011-08-11
Kill them with...```
kill 4675 4679
```

---

### Post by mike555 on 2011-08-11
I can't kill them because the numbers are constantly changing .

do any of you out there running Ubuntu 10.04 see this sort of thing in your System monitor ?

---

### Post by MG&amp;TL on 2011-08-11
That seems a tad odd. Are these persistent, or just something new?

---

### Post by haqking on 2011-08-11
> **mike555 said:**
> I can't kill them because the numbers are constantly changing .

do any of you out there running Ubuntu 10.04 see this sort of thing in your System monitor ?

ps aux | less

and see if they have a name there

---

### Post by AlphaLexman on 2011-08-11
I cannot test if this works because I don't have the same 'blank processes' but try this...
```
 ps aux | awk '{print $2, $11}' | grep "\n"
```
and post the output if any.

---

### Post by mike555 on 2011-08-11
here is results [mike@me-desktop:~$ ps aux | awk '{print $2, $11}' | grep "\n"
1 /sbin/init
3 [migration/0]
6 [migration/1]
9 [events/0]
10 [events/1]
13 [async/mgr]
16 [sync_supers]
18 [kintegrityd/0]
19 [kintegrityd/1]
23 [kacpi_notify]
28 [ksuspend_usbd]
34 [khungtaskd]
56 [kmpath_handlerd]
57 [ksnapd]
58 [kondemand/0]
59 [kondemand/1]
60 [kconservative/0]
61 [kconservative/1]
309 /sbin/v86d
385 [ext4-dio-unwrit]
386 [ext4-dio-unwrit]
405 mountall
962 dbus-daemon
979 gdm-binary
987 NetworkManager
991 avahi-daemon:
992 avahi-daemon:
999 /usr/sbin/console-kit-daemon
1000 /usr/sbin/modem-manager
1106 /usr/bin/X
1110 /sbin/getty
1114 /sbin/wpa_supplicant
1125 /sbin/getty
1135 /sbin/getty
1136 /sbin/getty
1138 /sbin/getty
1161 cron
1264 /usr/bin/freshclam
1286 /usr/sbin/cupsd
1329 /usr/sbin/preload
1388 /sbin/getty
1400 /usr/lib/gdm/gdm-session-worker
1409 gnome-session
1650 /usr/bin/ssh-agent
1669 /usr/bin/dbus-launch
1670 /bin/dbus-daemon
1818 /usr/lib/libgconf2-4/gconfd-2
2594 /usr/bin/gnome-keyring-daemon
2598 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
2605 /usr/lib/gvfs//gvfs-fuse-daemon
2614 /usr/bin/pulseaudio
2616 /usr/lib/rtkit/rtkit-daemon
2622 gnome-panel
2624 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
2625 nautilus
2626 gnome-power-manager
2628 gnome-volume-control-applet
2632 /usr/bin/python
2639 nm-applet
2652 /usr/lib/pulseaudio/pulse/gconf-helper
2669 /usr/lib/bonobo-activation/bonobo-activation-server
2700 /usr/sbin/hald
2706 hald-runner
2717 /usr/lib/gnome-panel/wnck-applet
2718 /usr/lib/gvfs/gvfs-gdu-volume-monitor
2719 /usr/lib/gnome-applets/trashapplet
2728 /usr/lib/udisks/udisks-daemon
2731 udisks-daemon:
2792 /usr/lib/gvfs/gvfs-afc-volume-monitor
2801 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
2838 hald-addon-input:
2844 /usr/lib/hal/hald-addon-rfkill-killswitch
2845 /usr/lib/hal/hald-addon-leds
2877 python
2879 /usr/lib/gnome-panel/notification-area-applet
2880 /usr/lib/netspeed/netspeed_applet2
2881 /usr/lib/indicator-applet/indicator-applet-session
2882 hald-addon-storage:
2884 /usr/lib/gnome-panel/clock-applet
2885 hald-addon-storage:
2887 /usr/lib/hal/hald-addon-cpufreq
2889 hald-addon-acpi:
2892 hald-addon-storage:
2894 hald-addon-storage:
2897 hald-addon-storage:
2933 /usr/lib/gvfs/gvfsd-burn
2966 /usr/lib/indicator-session/indicator-session-service
3027 /usr/lib/notify-osd/notify-osd
3074 /usr/bin/gnome-screensaver
4719 /usr/lib/gnome-disk-utility/gdu-notification-daemon
5225 /sbin/dhclient
8248 /usr/lib/firefox-6.0/firefox-bin
8326 [firefox-bin]
9958 python
15042 gnome-terminal
15073 gnome-pty-helper
15200 update-notifier
16340 /usr/bin/openbox
16348 gnome-settings-daemon
22099 /usr/sbin/exim4
mike@me-desktop:~$ ]

---

### Post by mike555 on 2011-08-11
This looks bad

[IMG]http://i53.tinypic.com/2w1s4le.jpg[/IMG]

---

### Post by AlphaLexman on 2011-08-11
My output for the same command is completely null...

Where are the blank processes you referenced before ??

What are their PID's ??

---

### Post by MG&amp;TL on 2011-08-11
Would it be a good idea to not connect to the web from that computer? At least until you've got rid of your bug?

---

### Post by AlphaLexman on 2011-08-11
You may have an error in the readdir(3) function, try a logout and  a re-login, or even a reboot, and see if the problem persists.

---

### Post by mike555 on 2011-08-12
as I said the number constantly changes , about ever 2 seconds or if I try to click on it in system monitor ......... also a restart did not change it .......... this is on my main operating system ,so need to fix.

---

### Post by AlphaLexman on 2011-08-12
Are you on a '**wubi**' install or by chance do you have '**wine**' installed ??

I am blindfolded and throwing darts now... sorry I can't help more!

---

### Post by mike555 on 2011-08-12
I do not have WINE installed and I did not use WUBI .......

---

### Post by AlphaLexman on 2011-08-12
Still throwing darts...

Do the blank processes show up in 'top' ??

They must be busy opening and closing and changing PID's 

Good Luck!

---

### Post by mike555 on 2011-08-12
Not sure, but I don't see them (htop)


  1  [||||||||||||||||||||||||||||||||||||||100.0%]     Tasks: 226 total, 3 running
  2  [||||||||||||||||||||||||||||||||||||||100.0%]     Load average: 2.90 3.62 4.09 
  Mem[||||||||||||||||||||||||||||||||||595/2013MB]     Uptime: 19:20:03
  Swp[|                                   4/1006MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 2144 mike      20   0  111M  105M  6756 R 69.0  5.2  0:06.11 /usr/bin/clamscan --no-summary --block-encrypte
11333 root      20   0 79220 59880 14356 S 21.0  2.9  5h19:30 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/a
11442 mike      20   0  3272  1504   672 S  4.0  0.1  1h02:52 /bin/dbus-daemon --fork --print-pid 5 --print-a
11407 mike      20   0 36588 17616  5288 S  4.0  0.9 55:39.55 gnome-session --default-session-key /desktop/gn
31199 mike      20   0  2652  1380   996 R  1.0  0.1  0:00.88 htop
31102 mike      20   0 51708 12012  9160 S  1.0  0.6  0:00.59 /usr/bin/gnome-terminal -x htop
11468 mike      20   0 89112  8984  6588 S  1.0  0.4 19:39.76 /usr/lib/gnome-settings-daemon/gnome-settings-d
11485 mike      20   0 49384 14556 10480 S  1.0  0.7 16:53.59 gnome-panel
11488 mike      20   0  126M 26220 13524 S  0.0  1.3 12:16.55 nautilus
17871 mike      20   0 31168 14380  7908 S  0.0  0.7 15:10.40 python /usr/share/system-config-printer/applet.
10739 root      35  15  8804  6912   824 S  0.0  0.3  0:30.30 preload
11496 mike      20   0 55676 20632 11876 S  0.0  1.0 16:27.16 /usr/bin/python /usr/bin/caffeine
 1329 root      35  15  8804  6840   828 S  0.0  0.3  1:31.18 /usr/sbin/preload -s /var/lib/preload/preload.s
11504 mike      20   0 67216 12632  9640 S  0.0  0.6  4:02.67 nm-applet --sm-disable
 8795 mike      20   0  172M  105M 11004 S  0.0  5.2 30:02.40 /usr/bin/perl /usr/bin/clamtk
25677 mike      20   0  336M  115M 34196 S  0.0  5.7  0:14.00 /usr/lib/firefox-6.0/firefox-bin
11476 mike      20   0 41840 11576  9232 S  0.0  0.6  4:50.16 metacity
11490 mike      20   0 19712  7484  6056 S  0.0  0.4  9:09.34 gnome-power-manager
11566 mike      20   0  100M 26192 13548 S  0.0  1.3  4:30.04 python /usr/lib/timer-applet/timer-applet --oaf
25712 mike      20   0  336M  115M 34196 S  0.0  5.7  0:00.34 /usr/lib/firefox-6.0/firefox-bin
  979 root      20   0 18788  3032  2620 S  0.0  0.1  2:35.97 gdm-binary
    1 root      20   0  2812  1500  1104 S  0.0  0.1  6:28.55 /sbin/init
  309 root      20   0  2596   192   188 S  0.0  0.0  0:00.04 /sbin/v86d
  405 root      20   0  4104  1028   872 S  0.0  0.0  0:00.02 mountall --daemon
  428 root      20   0  2316   764   636 S  0.0  0.0  0:00.08 upstart-udev-bridge --daemon
  430 root      16  -4  2660   604   340 S  0.0  0.0  0:00.04 udevd --daemon
  939 syslog    20   0 34944  1228  1004 S  0.0  0.1  0:00.14 rsyslogd -c4
  944 syslog    20   0 34944  1228  1004 S  0.0  0.1  0:00.01 rsyslogd -c4
  945 syslog    20   0 34944  1228  1004 S  0.0  0.1  0:00.00 rsyslogd -c4
  962 messageb  20   0  3336  1492   768 S  0.0  0.1  0:03.60 dbus-daemon --system --fork
 1091 root      20   0 18788  3032  2620 S  0.0  0.1  0:00.00 gdm-binary
  987 root      20   0 19004  3216  2700 S  0.0  0.2  0:02.95 NetworkManager
 5226 root      20   0 19004  3216  2700 S  0.0  0.2  0:00.00 NetworkManager
  991 avahi     20   0  2928  1164  1036 S  0.0  0.1  0:00.04 avahi-daemon: running [me-desktop.local]
  992 avahi     20   0  2928   296   264 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
  999 root      20   0 20772  2524  2144 S  0.0  0.1  0:00.11 /usr/sbin/console-kit-daemon --no-daemon
 1003 root      20   0 20772  2524  2144 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
 1004 root      20   0 20772  2524  2144 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
 1005 root      20   0 20772  2524  2144 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
 1006 root      20   0 20772  2524  2144 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
 1007 root      20   0 20772  2524  2144 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon --no-daemon
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

---

### Post by AlphaLexman on 2011-08-12
You are correct... Nothing there.

As haqking requested earlier, post the output of 
```
ps aux
```
(but without the 'less' pipe)
EDIT: In Code tags please!

---

### Post by mike555 on 2011-08-12
```
 mike@me-desktop:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.5  0.0   2812  1476 ?        Ss   Aug11   6:44 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Aug11   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Aug11   0:15 [migration/0]
root         4  0.0  0.0      0     0 ?        S    Aug11   0:05 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    Aug11   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    Aug11   0:16 [migration/1]
root         7  0.0  0.0      0     0 ?        S    Aug11   0:14 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    Aug11   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    Aug11   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    Aug11   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    Aug11   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    Aug11   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    Aug11   0:00 [async/mgr]
root        14  0.0  0.0      0     0 ?        S    Aug11   0:00 [pm]
root        16  0.0  0.0      0     0 ?        S    Aug11   0:00 [sync_supers]
root        17  0.0  0.0      0     0 ?        S    Aug11   0:00 [bdi-default]
root        18  0.0  0.0      0     0 ?        S    Aug11   0:00 [kintegrityd/0]
root        19  0.0  0.0      0     0 ?        S    Aug11   0:00 [kintegrityd/1]
root        20  0.0  0.0      0     0 ?        S    Aug11   0:00 [kblockd/0]
root        21  0.0  0.0      0     0 ?        S    Aug11   0:00 [kblockd/1]
root        22  0.0  0.0      0     0 ?        S    Aug11   0:00 [kacpid]
root        23  0.0  0.0      0     0 ?        S    Aug11   0:00 [kacpi_notify]
root        24  0.0  0.0      0     0 ?        S    Aug11   0:00 [kacpi_hotplug]
root        25  0.0  0.0      0     0 ?        S    Aug11   0:10 [ata/0]
root        26  0.0  0.0      0     0 ?        S    Aug11   0:04 [ata/1]
root        27  0.0  0.0      0     0 ?        S    Aug11   0:00 [ata_aux]
root        28  0.0  0.0      0     0 ?        S    Aug11   0:00 [ksuspend_usbd]
root        29  0.0  0.0      0     0 ?        S    Aug11   0:00 [khubd]
root        30  0.0  0.0      0     0 ?        S    Aug11   0:00 [kseriod]
root        31  0.0  0.0      0     0 ?        S    Aug11   0:00 [kmmcd]
root        34  0.0  0.0      0     0 ?        S    Aug11   0:00 [khungtaskd]
root        35  0.0  0.0      0     0 ?        S    Aug11   0:04 [kswapd0]
root        36  0.0  0.0      0     0 ?        SN   Aug11   0:00 [ksmd]
root        37  0.0  0.0      0     0 ?        S    Aug11   0:00 [aio/0]
root        38  0.0  0.0      0     0 ?        S    Aug11   0:00 [aio/1]
root        39  0.0  0.0      0     0 ?        S    Aug11   0:00 [ecryptfs-kthr]
root        40  0.0  0.0      0     0 ?        S    Aug11   0:00 [crypto/0]
root        41  0.0  0.0      0     0 ?        S    Aug11   0:00 [crypto/1]
root        45  0.0  0.0      0     0 ?        S    Aug11   0:30 [scsi_eh_0]
root        46  0.0  0.0      0     0 ?        S    Aug11   0:00 [scsi_eh_1]
root        47  0.0  0.0      0     0 ?        S    Aug11   0:00 [scsi_eh_2]
root        50  0.0  0.0      0     0 ?        S    Aug11   0:00 [scsi_eh_3]
root        53  0.0  0.0      0     0 ?        S    Aug11   0:00 [kstriped]
root        54  0.0  0.0      0     0 ?        S    Aug11   0:00 [kmpathd/0]
root        55  0.0  0.0      0     0 ?        S    Aug11   0:00 [kmpathd/1]
root        56  0.0  0.0      0     0 ?        S    Aug11   0:00 [kmpath_handle]
root        57  0.0  0.0      0     0 ?        S    Aug11   0:00 [ksnapd]
root        58  0.0  0.0      0     0 ?        S    Aug11   1:08 [kondemand/0]
root        59  0.0  0.0      0     0 ?        S    Aug11   0:55 [kondemand/1]
root        60  0.0  0.0      0     0 ?        S    Aug11   0:00 [kconservative]
root        61  0.0  0.0      0     0 ?        S    Aug11   0:00 [kconservative]
root       271  0.0  0.0      0     0 ?        S    Aug11   0:00 [scsi_eh_4]
root       272  0.0  0.0      0     0 ?        S    Aug11   0:30 [usb-storage]
root       277  0.0  0.0      0     0 ?        S    Aug11   0:00 [usbhid_resume]
root       309  0.0  0.0   2208   192 ?        Ss   Aug11   0:00 /sbin/v86d
root       310  0.0  0.0      0     0 ?        S    Aug11   0:00 [cqueue]
root       349  0.0  0.0      0     0 ?        S    Aug11   0:01 [flush-8:0]
root       384  0.0  0.0      0     0 ?        S    Aug11   0:04 [jbd2/sda2-8]
root       385  0.0  0.0      0     0 ?        S    Aug11   0:00 [ext4-dio-unwr]
root       386  0.0  0.0      0     0 ?        S    Aug11   0:00 [ext4-dio-unwr]
root       405  0.0  0.0   4104  1000 ?        S    Aug11   0:00 mountall --daem
root       428  0.0  0.0   2316   736 ?        S    Aug11   0:00 upstart-udev-br
root       430  0.0  0.0   2660   512 ?        S<s  Aug11   0:00 udevd --daemon
root       738  0.0  0.0      0     0 ?        S    Aug11   0:33 [phy0]
root       815  0.0  0.0      0     0 ?        S    Aug11   0:04 [hd-audio0]
syslog     939  0.0  0.0  34944  1144 ?        Sl   Aug11   0:00 rsyslogd -c4
102        962  0.0  0.0   3336  1492 ?        Ss   Aug11   0:03 dbus-daemon --s
root       979  0.2  0.1  18788  2916 ?        Ssl  Aug11   2:45 gdm-binary
root       987  0.0  0.1  19004  3124 ?        Ssl  Aug11   0:03 NetworkManager
avahi      991  0.0  0.0   2928  1156 ?        S    Aug11   0:00 avahi-daemon: r
avahi      992  0.0  0.0   2928   280 ?        Ss   Aug11   0:00 avahi-daemon: c
root       999  0.0  0.1  20772  2612 ?        Sl   Aug11   0:00 /usr/sbin/conso
root      1000  0.0  0.0   4172  1800 ?        S    Aug11   0:00 /usr/sbin/modem
root      1069  0.0  0.0   2656   472 ?        S<   Aug11   0:00 udevd --daemon
root      1084  0.0  0.0   2656   456 ?        S<   Aug11   0:00 udevd --daemon
root      1110  0.0  0.0   1792   468 tty4     Ss+  Aug11   0:00 /sbin/getty -8
root      1114  0.0  0.0   4836  1756 ?        S    Aug11   0:00 /sbin/wpa_suppl
root      1125  0.0  0.0   1792   472 tty5     Ss+  Aug11   0:00 /sbin/getty -8
root      1135  0.0  0.0   1792   472 tty2     Ss+  Aug11   0:00 /sbin/getty -8
root      1136  0.0  0.0   1792   472 tty3     Ss+  Aug11   0:00 /sbin/getty -8
root      1138  0.0  0.0   1792   472 tty6     Ss+  Aug11   0:00 /sbin/getty -8
root      1143  0.0  0.0   2048   564 ?        Ss   Aug11   0:00 acpid -c /etc/a
root      1159  0.0  0.0   2236   700 ?        S    09:31   0:00 /sbin/dhclient
root      1161  0.0  0.0   2376   776 ?        Ss   Aug11   0:00 cron
daemon    1162  0.0  0.0   2248   304 ?        Ss   Aug11   0:00 atd
clamav    1264  0.0  0.0  12904  1420 ?        Ss   Aug11   0:00 /usr/bin/freshc
root      1286  0.0  0.0   6844  1920 ?        Ss   Aug11   0:00 /usr/sbin/cupsd
root      1329  0.1  0.3   8804  6840 ?        SNs  Aug11   1:37 /usr/sbin/prelo
root      1388  0.0  0.0   1792   472 tty1     Ss+  Aug11   0:00 /sbin/getty -8
mike      2614  0.1  0.1  86144  3996 ?        S<sl Aug11   2:20 /usr/bin/pulsea
rtkit     2616  0.0  0.0  22908  1104 ?        SNl  Aug11   0:00 /usr/lib/rtkit/
root      2620  0.0  0.1   6312  3368 ?        S    Aug11   0:00 /usr/lib/policy
root      2647  0.0  0.1   5516  2160 ?        S    Aug11   0:00 /usr/lib/upower
mike      2652  0.0  0.1  10756  2576 ?        S    Aug11   0:00 /usr/lib/pulsea
108       2700  0.0  0.1  17012  2556 ?        Ssl  Aug11   0:00 /usr/sbin/hald
root      2706  0.0  0.0   3536  1064 ?        S    Aug11   0:00 hald-runner
root      2728  0.0  0.1  15764  2812 ?        Sl   Aug11   0:01 /usr/lib/udisks
root      2731  0.0  0.0   5188   844 ?        S    Aug11   0:36 udisks-daemon: 
root      2838  0.0  0.0   3612  1076 ?        S    Aug11   0:00 hald-addon-inpu
root      2844  0.0  0.0   3612   996 ?        S    Aug11   0:00 /usr/lib/hal/ha
root      2845  0.0  0.0   3612   996 ?        S    Aug11   0:00 /usr/lib/hal/ha
root      2882  0.0  0.0   3616  1064 ?        S    Aug11   0:03 hald-addon-stor
root      2885  0.0  0.0   3616  1060 ?        S    Aug11   0:03 hald-addon-stor
root      2887  0.0  0.0   3624   992 ?        S    Aug11   0:00 /usr/lib/hal/ha
108       2889  0.0  0.0   3420   960 ?        S    Aug11   0:00 hald-addon-acpi
root      2892  0.0  0.0   3616  1064 ?        S    Aug11   0:03 hald-addon-stor
root      2894  0.0  0.0   3616  1064 ?        S    Aug11   0:03 hald-addon-stor
root      2897  0.0  0.0   3616  1064 ?        S    Aug11   0:23 hald-addon-stor
mike      8795  8.9  5.1 176912 107188 ?       R    09:32  44:39 /usr/bin/perl /
root     10739  0.1  0.3   8804  6912 ?        SNs  09:22   0:37 preload
root     11331  0.0  0.1  20508  3420 ?        Sl   Aug11   0:00 /usr/lib/gdm/gd
root     11333 30.9  2.8  76636 58800 tty8     Rs+  Aug11 361:50 /usr/bin/X :0 -
gdm      11353  0.0  0.0   3384   776 ?        S    Aug11   0:00 /usr/bin/dbus-l
root     11372  0.0  0.1  20800  3216 ?        Sl   Aug11   0:00 /usr/lib/gdm/gd
mike     11389  0.2  0.0  23984  1856 ?        Sl   Aug11   2:51 /usr/bin/gnome-
mike     11407  5.0  0.8  36972 18084 ?        Ssl  Aug11  59:22 gnome-session -
mike     11438  0.0  0.0   3284   328 ?        Ss   Aug11   0:00 /usr/bin/ssh-ag
mike     11441  0.0  0.0   3384   780 ?        S    Aug11   0:00 /usr/bin/dbus-l
mike     11442  5.6  0.0   3272  1520 ?        Ss   Aug11  65:51 /bin/dbus-daemo
mike     11456  0.0  0.2   7464  4144 ?        S    Aug11   0:03 /usr/lib/libgco
mike     11468  1.7  0.4  89112  9032 ?        Ss   Aug11  20:37 /usr/lib/gnome-
mike     11470  0.2  0.1   6512  2332 ?        S    Aug11   2:49 /usr/lib/gvfs/g
mike     11475  0.0  0.1  38612  2600 ?        Ssl  Aug11   0:00 /usr/lib/gvfs//
mike     11476  0.4  0.5  41852 11556 ?        S    Aug11   5:06 metacity
mike     11485  1.5  0.8  51280 18460 ?        S    Aug11  17:48 gnome-panel
mike     11486  0.0  0.2  18084  5664 ?        S    Aug11   0:00 /usr/lib/policy
mike     11488  1.1  1.6 129468 33456 ?        Sl   Aug11  13:35 nautilus
mike     11490  0.8  0.3  19712  7396 ?        S    Aug11   9:33 gnome-power-man
mike     11493  0.0  0.4 108056 10044 ?        S    Aug11   0:00 gnome-volume-co
mike     11496  1.5  1.0  55676 20900 ?        S    Aug11  17:39 /usr/bin/python
mike     11504  0.3  0.6  67216 12540 ?        S    Aug11   4:13 nm-applet --sm-
mike     11511  0.0  0.1   7884  3276 ?        S    Aug11   0:00 /usr/lib/gvfs/g
mike     11525  0.0  1.6 203716 33540 ?        Ssl  Aug11   0:15 /home/mike/.dro
mike     11529  0.0  0.1  16956  2296 ?        Sl   Aug11   0:02 /usr/lib/gvfs/g
mike     11536  0.0  0.1   7128  2256 ?        S    Aug11   0:00 /usr/lib/gvfs/g
mike     11537  0.0  0.1  16236  3104 ?        S    Aug11   0:00 /usr/lib/gvfs/g
mike     11555  0.0  0.6  48476 13424 ?        S    Aug11   0:03 /usr/lib/gnome-
mike     11558  0.0  0.5  56068 12032 ?        S    Aug11   0:00 /usr/lib/gnome-
mike     11566  0.4  1.2 102700 25648 ?        S    Aug11   4:49 python /usr/lib
mike     11567  0.3  0.5  55188 11540 ?        Sl   Aug11   4:05 /usr/lib/indica
mike     11569  0.0  0.5  45764 11368 ?        S    Aug11   1:08 /usr/lib/netspe
mike     11571  0.3  0.6  31796 12508 ?        S    Aug11   4:09 /usr/lib/gnome-
mike     11572  0.0  0.4  22768  8692 ?        S    Aug11   0:00 /usr/lib/gnome-
mike     11662  0.3  0.2  17608  4616 ?        S    Aug11   4:05 /usr/lib/indica
mike     11664  0.0  0.1   6456  2180 ?        S    Aug11   0:00 /usr/lib/gvfs/g
mike     11714  0.0  0.1   6380  2276 ?        S    Aug11   0:00 /usr/lib/gvfs/g
mike     11793  0.0  0.5  44784 12332 ?        S    Aug11   0:01 /usr/lib/notify
mike     12261  0.3  0.1  17476  2932 ?        Ss   Aug11   4:13 gnome-screensav
mike     13376  0.0  0.3  18704  7088 ?        S    Aug11   0:00 /usr/lib/gnome-
mike     16626  0.0  0.1  15000  2792 ?        S    Aug11   0:00 /usr/lib/gvfs/g
mike     17871  1.3  0.6  31168 14292 ?        S    Aug11  15:49 python /usr/sha
mike     18366  0.0  0.3  17692  6284 ?        S    Aug11   0:00 gksu nautilus '
root     18373  0.0  0.9  86228 19036 ?        Ssl  Aug11   0:20 nautilus file:/
root     18382  0.0  0.0   3384   748 ?        S    Aug11   0:00 dbus-launch --a
root     18384  0.0  0.0   2664   824 ?        Ss   Aug11   0:00 /bin/dbus-daemo
root     18386  0.0  0.1   7324  3896 ?        S    Aug11   0:00 /usr/lib/libgco
mike     21698  0.0  0.1  10572  3472 ?        S    16:36   0:00 /usr/lib/gvfs/g
116      22099  0.0  0.0   6732   948 ?        Ss   Aug11   0:00 /usr/sbin/exim4
mike     24004  0.0  0.5  24472 11168 ?        S    16:36   0:00 artha
mike     24909  0.0  0.5  41820 10368 ?        S    Aug11   0:02 update-notifier
mike     25008 15.0  7.6 417232 158156 ?       Sl   17:33   2:32 /usr/lib/firefo
mike     25676  0.0  0.0   1848   592 ?        S    17:50   0:00 sh -c /usr/bin/
mike     25677 60.5  5.3 117204 111068 ?       R    17:50   0:08 /usr/bin/clamsc
mike     26979  4.3  0.5  51224 11844 ?        Sl   17:50   0:00 gnome-terminal
mike     27016  0.0  0.0   1988   712 ?        S    17:50   0:00 gnome-pty-helpe
mike     27017  4.8  0.1   5876  3244 pts/0    Ss   17:50   0:00 bash
mike     27473  0.0  0.0   1832   552 ?        S    17:50   0:00 /bin/sh /usr/bi
mike     27476  0.0  0.0   2716  1072 pts/0    R+   17:50   0:00 ps aux
mike@me-desktop:~$ 
 
```

---

### Post by AlphaLexman on 2011-08-12
I don't know enough about 'System Monitor' but if the blank processes don't show up anywhere else, it **MAY** be an issue or a BUG with the program 'System Monitor'

It seems we can't re-create the blank processes anywhere else but in 'System Monitor'

---

### Post by mike555 on 2011-08-13
anyone know what this is ............. I hate to reinstall , how does a person rid themselves of a rootkit in ubuntu if that is what it is ?

---

### Post by mike555 on 2011-08-13
no one can help me?    please at least check and see if any of you see the same strange empty processes on your System ..........

---

### Post by RHTopics on 2011-08-13
I am running Ubuntu 10.4.3.  I checked my System Monitor and do not have empty processes.

You might try running a Live CD that can check for root kits.  I think Knoppix may have that capability and a new version just came out recently.

---

### Post by AlphaLexman on 2011-08-13
Now I'm thinking maybe the process name contains an escape character or other non-printing code.

In System Monitor, can you 'select' and copy the line with the blank process, and then paste it somewhere that could interpret the non-printing code, maybe gedit or OpenOffice?

---

### Post by mike555 on 2011-08-13
I think I got it , I uninstalled Fluxbox and open box ,that I was experimenting with , now no weird processes .
  also my Memory use went down about 100 mb ... hope that is all it was .........



ok, I spoke too soon on the memory, because Firefox brought it back up 60 or more, but still no weird unnamed processes in System Monitor.

---

