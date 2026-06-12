---
title: "Computer Suspends Randomly"
date: 2010-03-12
forum: General Help
---

### Post by Cuco3 on 2010-03-12
Hello. I'm not sure if it's the culprit, but my computer has been randomly going in to suspend (5 times in a 24 hour period) as of the last 3 days, around the time I a created a script for inhibiting suspend for XBMC, found on this post: [http://ubuntuforums.org/showpost.php?p=7054984&postcount=2](http://ubuntuforums.org/showpost.php?p=7054984&postcount=2)

> #!/bin/bash
gnome-screensaver-command -i &
xbcm && killall -15 gnome-screensaver-command ;
exitI've also included the log of my pm-suspend to determine if there's a hint that could tell me why my computer is randomly going to sleep.

---

### Post by Cuco3 on 2010-03-12
anyone?

---

### Post by tgalati4 on 2010-03-12
What are the details of your machine?  Make and model.  How old is it?  Does it go to sleep if you don't run your script?

What settings did you use in gnome power-management?

I didn't see anything unusual in your log file.

---

### Post by Cuco3 on 2010-03-13
> **tgalati4 said:**
> What are the details of your machine?  Make and model.  How old is it?  Does it go to sleep if you don't run your script?

What settings did you use in gnome power-management?

I didn't see anything unusual in your log file.
Thanks for your reply.


I doubt the make and model matters, anyway, it's a custom built Intel DX58SO with a 2.4 GHz P4 Processor.

It was working fine forever until the I ran that script. I deleted the script entirely, and to be honest, I don't think there's anything in that script that would. I remember getting a gnome-screensaver update around that time too so I'm gonna check that out and roll back.

Will keep you guys updated.

Here are the last 3 updates Update Manager has installed.

Commit Log for Mon Mar  8 22:04:03 2010

> Commit Log for Mon Mar  8 22:04:03 2010

Upgraded the following packages:
gnome-screensaver (2.24.0-0ubuntu6) to 2.24.0-0ubuntu6.1> Commit Log for Thu Mar 11 00:42:08 2010

Upgraded the following packages:
dpkg (1.14.24ubuntu1) to 1.14.24ubuntu1.1
tzdata (2009u~repack-0ubuntu9.04) to 2010e~repack-0ubuntu9.04The "gnome-screensaver" is suspect, will try rolling that back.

Edit: so I "forced version" the prior to the gnome-screensaver before the update. Let's see if that works.

---

### Post by Cuco3 on 2010-03-13
Rolled back gnome-screensaver: nothing
Uninstalled XBMC: nothing

Trying:
Roll back tzdata: ...
Roll back dpkg: ...

---

### Post by tgalati4 on 2010-03-13
If the machine is 5 years old then it's possible that the motherboard battery is worn out and causing strangeness.  Try changing it.

I have two older machines that the power-on circuitry has failed.  I hardwired a switch to turn them on and off.  Thankfully linux doesn't require many reboots.

---

### Post by Cuco3 on 2010-03-13
Thanks for your reply.

I'll try that next, but I'll leave my computer running on XP (dual boot) and test out the Power Management before I try your proposed solution.

Other things I've tried

Rolled back dpkg: nothing
Rolled back tzdata: nothing

sudo apt-get purge gnome-power-manager (then re-install): nothing.

I've set Power Mananged to never turn the monitor off or put the system to sleep and the computer didn't (randomly) go to sleep. IMO it's something that is sending a sleep signal to the computer, but I don't know where to go to determine what it is.

---

### Post by tgalati4 on 2010-03-13
What does:

dmesg | tail -100

Show right after resuming from a sleep episode?

---

### Post by Cuco3 on 2010-03-14
tgalati4: I will try it the next time the problem occurs, I even have the command on cairo-dock's stack so I can just copy+paste it in to the terminal when it happens. Thanks.

Anyway, I used Windows XP for about 8 hours yesterday (it was horrible, none of the functionality that I'm used to!) and the computer's power management worked like a champ. No random suspend while I was getting my work done. I'm more convinced it has something to do with a running process that is sending a sleep signal. So with that in mind, I printed a list of all running processes on my computer:

> USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1908   784 ?        Ss   05:34   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   05:34   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   05:34   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   05:34   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   05:34   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   05:34   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   05:34   0:00 [khelper]
root         8  0.0  0.0      0     0 ?        S<   05:34   0:00 [kstop/0]
root         9  0.0  0.0      0     0 ?        S<   05:34   0:00 [kintegrityd/0]
root        10  0.0  0.0      0     0 ?        S<   05:34   0:00 [kblockd/0]
root        11  0.0  0.0      0     0 ?        S<   05:34   0:00 [kacpid]
root        12  0.0  0.0      0     0 ?        S<   05:34   0:00 [kacpi_notify]
root        13  0.0  0.0      0     0 ?        S<   05:34   0:00 [cqueue]
root        14  0.0  0.0      0     0 ?        S<   05:34   0:00 [ata/0]
root        15  0.0  0.0      0     0 ?        S<   05:34   0:00 [ata_aux]
root        16  0.0  0.0      0     0 ?        S<   05:34   0:00 [ksuspend_usbd]
root        17  0.0  0.0      0     0 ?        S<   05:34   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   05:34   0:00 [kseriod]
root        19  0.0  0.0      0     0 ?        S<   05:34   0:00 [kmmcd]
root        20  0.0  0.0      0     0 ?        S<   05:34   0:00 [btaddconn]
root        21  0.0  0.0      0     0 ?        S<   05:34   0:00 [btdelconn]
root        22  0.0  0.0      0     0 ?        S    05:34   0:00 [pdflush]
root        23  0.0  0.0      0     0 ?        S    05:34   0:00 [pdflush]
root        24  0.0  0.0      0     0 ?        S<   05:34   0:00 [kswapd0]
root        25  0.0  0.0      0     0 ?        S<   05:34   0:00 [aio/0]
root        26  0.0  0.0      0     0 ?        S<   05:34   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   05:34   0:00 [scsi_eh_0]
root        30  0.0  0.0      0     0 ?        S<   05:34   0:00 [scsi_eh_1]
root        31  0.0  0.0      0     0 ?        S<   05:34   0:00 [kstriped]
root        32  0.0  0.0      0     0 ?        S<   05:34   0:00 [kmpathd/0]
root        33  0.0  0.0      0     0 ?        S<   05:34   0:00 [kmpath_handlerd]
root        34  0.0  0.0      0     0 ?        S<   05:34   0:00 [ksnapd]
root        35  0.0  0.0      0     0 ?        S<   05:34   0:00 [kondemand/0]
root        36  0.0  0.0      0     0 ?        S<   05:34   0:00 [krfcommd]
root       679  0.0  0.0      0     0 ?        S<   05:34   0:00 [kjournald]
root       813  0.0  0.0   2224   564 ?        S<s  05:34   0:00 /sbin/udevd --daemon
root      1209  0.0  0.0      0     0 ?        S<   05:34   0:00 [kgameportd]
root      1391  0.0  0.0      0     0 ?        S<   05:34   0:00 [kpsmoused]
daemon    2039  0.0  0.0   1940   536 ?        Ss   05:34   0:00 /sbin/portmap
statd     2060  0.0  0.0   2004   768 ?        Ss   05:34   0:00 /sbin/rpc.statd
root      2140  0.0  0.0   1808   524 tty4     Ss+  05:34   0:00 /sbin/getty 38400 tty4
root      2141  0.0  0.0   1808   524 tty5     Ss+  05:34   0:00 /sbin/getty 38400 tty5
root      2147  0.0  0.0   1808   528 tty2     Ss+  05:34   0:00 /sbin/getty 38400 tty2
root      2149  0.0  0.0   1808   528 tty3     Ss+  05:34   0:00 /sbin/getty 38400 tty3
root      2152  0.0  0.0   1808   528 tty6     Ss+  05:34   0:00 /sbin/getty 38400 tty6
root      2220  0.0  0.1   2204  1084 ?        Ss   05:34   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2265  0.0  0.0   2040   680 ?        Ss   05:34   0:00 /sbin/syslogd -u syslog
root      2288  0.0  0.0   1968   540 ?        S    05:34   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2290  0.0  0.3   4480  3192 ?        Ss   05:34   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       2313  0.0  0.1   2984  1356 ?        Ss   05:34   0:01 /bin/dbus-daemon --system
root      2679  0.0  0.1   7240  1640 ?        Ss   05:34   0:00 /usr/sbin/nmbd -D
root      2683  0.0  0.2  13032  2624 ?        Ss   05:34   0:00 /usr/sbin/smbd -D
root      2701  0.0  0.1  13032  1060 ?        S    05:34   0:00 /usr/sbin/smbd -D
113       2702  0.0  0.1  15672  1800 ?        Ssl  05:34   0:00 /usr/bin/transmission-daemon --auth --config-dir /var/lib/transmission-daemon/info
111       2761  0.0  0.4   6704  4688 ?        Ss   05:34   0:01 /usr/sbin/hald
root      2764  0.0  0.2  16356  2596 ?        Ssl  05:34   0:00 /usr/sbin/console-kit-daemon
root      2827  0.0  0.1   3328  1148 ?        S    05:34   0:00 hald-runner
root      2858  0.0  0.1   5176  1792 ?        S    05:34   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event6 /dev/in
root      2915  0.0  0.1   5180  1808 ?        S    05:34   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
111       2920  0.0  0.1   5032  1760 ?        S    05:34   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      2935  0.0  0.1   3556  1548 ?        Ss   05:34   0:00 /usr/sbin/bluetoothd
root      2968  0.0  0.1  15032  1776 ?        Ss   05:34   0:00 /usr/sbin/gdm
root      2971  0.0  0.4  20348  4928 ?        S    05:34   0:00 /usr/sbin/gdm
root      2975  0.6  5.4  66148 55632 tty7     Ss+  05:34   4:43 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      2997  0.0  0.2  16304  2712 ?        Ssl  05:34   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      3002  0.0  0.1   4280  1336 ?        S    05:34   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      3004  0.0  0.3   6936  3120 ?        S    05:34   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
avahi     3021  0.0  0.1   3052  1572 ?        Ss   05:34   0:00 avahi-daemon: running [Alex-Linux.local]
avahi     3022  0.0  0.0   2944   512 ?        Ss   05:34   0:00 avahi-daemon: chroot helper
root      3045  0.0  0.2   6108  2432 ?        Ss   05:34   0:00 /usr/sbin/cupsd
root      3074  0.0  0.1   4324  1156 ?        Ss   05:34   0:00 /usr/bin/system-tools-backends
daemon    3150  0.0  0.0   2096   452 ?        Ss   05:34   0:00 /usr/sbin/atd
root      3178  0.0  0.1   3480  1036 ?        Ss   05:34   0:00 /usr/sbin/cron
root      3274  0.0  0.0   1808   528 tty1     Ss+  05:34   0:00 /sbin/getty 38400 tty1
gdm       3300  0.0  0.0   3144   700 ?        S    05:34   0:00 dbus-launch --autolaunch 32c4623dd3389e759542b08c4b868d18 --binary-syntax --close-stderr
gdm       3301  0.0  0.0   2672   736 ?        Ss   05:34   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
alex      3368  0.0  0.2  25672  3020 ?        S    05:34   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
alex      3383  0.0  0.6  26256  6792 ?        Ssl  05:34   0:00 x-session-manager
alex      3564  0.0  0.0   4784   600 ?        Ss   05:34   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/
alex      3567  0.0  0.0   3144   700 ?        S    05:34   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --ex
alex      3568  0.0  0.1   3192  1392 ?        Ss   05:34   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
alex      3576  0.0  0.4   7612  4508 ?        S    05:34   0:03 /usr/lib/libgconf2-4/gconfd-2
alex      3588  0.0  0.6  19128  6364 ?        Ss   05:34   0:00 /usr/bin/seahorse-agent --execute x-session-manager
alex      3591  0.0  0.2   5748  2164 ?        S    05:34   0:00 /usr/lib/gvfs/gvfsd
alex      3597  0.0  0.2  29584  2404 ?        Ssl  05:34   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/alex/.gvfs
alex      3603  0.0  0.9  29904  9620 ?        Ssl  05:34   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
alex      3612  0.0  0.0   1872   564 ?        S    05:34   0:00 /bin/sh /usr/bin/compiz
alex      3671  0.2  5.3  89044 55132 ?        S    05:34   1:28 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 1012d3c33eadb38b7112685
alex      3672  0.0  2.2  66308 22896 ?        S    05:34   0:02 nautilus
alex      3673  0.0  2.0  35772 21028 ?        S    05:34   0:13 python -u /usr/share/screenlets/DigiClock/DigiClockScreenlet.py
alex      3674  0.1  4.8 194572 50168 ?        Sl   05:34   1:08 cairo-dock -o
alex      3675  0.0  1.9  35256 20080 ?        S    05:34   0:26 python -u /usr/share/screenlets/Slideshow/SlideshowScreenlet.py
alex      3676  0.0  2.5  41264 26484 ?        S    05:34   0:01 python -u /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py
alex      3677  0.0  2.1  37384 22440 ?        S    05:34   0:02 python -u /usr/share/screenlets/Sidebar/SidebarScreenlet.py
alex      3678  0.0  2.1  35672 21596 ?        S    05:34   0:01 python -u /usr/share/screenlets/Notes/NotesScreenlet.py
alex      3679  0.0  0.0   1872   512 ?        S    05:34   0:00 /bin/sh /usr/bin/gnome-do
alex      3681  0.0  1.7  33320 17620 ?        S    05:34   0:00 python /usr/share/screenlets-manager/screenlets-daemon.py
alex      3688  0.0  3.1  62632 31916 ?        Sl   05:34   0:08 /usr/bin/cli /usr/lib/gnome-do/Do.exe
alex      3699  0.0  0.6  16048  6532 ?        S    05:34   0:00 bluetooth-applet
alex      3700  0.0  1.3  27740 14208 ?        S    05:34   0:00 python /usr/share/system-config-printer/applet.py
alex      3702  0.0  1.4  27652 14372 ?        S    05:34   0:00 update-notifier --startup-delay=60
alex      3705  0.0  0.8  20012  8260 ?        S    05:34   0:00 nm-applet --sm-disable
alex      3708  0.0  0.7  17460  7808 ?        S    05:34   0:00 /usr/lib/notify-osd/notify-osd
alex      3712  0.0  0.2   5940  2760 ?        S    05:34   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
alex      3713  0.0  0.9  25340  9244 ?        Ss   05:34   0:00 gnome-power-manager
alex      3716  0.0  0.3   7984  3592 ?        S    05:34   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
alex      3718  0.0  0.3   8704  4000 ?        S    05:34   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
alex      3723  0.0  0.2   5616  2232 ?        S    05:34   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
alex      3802  0.0  0.2   5932  2664 ?        S    05:34   0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.5 /org/gtk/gvfs/exec_spaw/3
alex      3809  0.0  1.0  20884 11224 ?        S    05:35   0:07 emerald --replace
alex      3830  0.0  0.5  16576  5368 ?        Ss   05:35   0:07 gnome-screensaver
alex      3839  0.0  0.3  24484  3516 ?        Ssl  05:35   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
root      5806  0.0  0.0   2276   980 ?        S    15:46   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-et
alex      6324 30.1 19.3 420100 198992 ?       Rl   15:47  20:21 /usr/lib/firefox-3.0.18/firefox
alex      8422  2.1  0.4 158880  5068 ?        Ssl  16:06   1:03 /usr/bin/pulseaudio --start --log-target=syslog
alex      8423  0.0  0.2   7824  2596 ?        S    16:06   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
alex      9303  0.0  0.8  61824  9152 ?        Sl   16:13   0:00 /usr/lib/evolution/evolution-data-server-2.26 --oaf-activate-iid=OAFIID:GNOME_Evolution_Data
alex      9342  0.0  1.1  50904 12072 ?        Sl   16:13   0:00 /usr/lib/evolution/2.26/evolution-alarm-notify --oaf-activate-iid=OAFIID:GNOME_Evolution_Cal
alex      9500  0.0  0.3  14780  3276 ?        S    16:14   0:00 /usr/lib/gvfs/gvfsd-network --spawner :1.5 /org/gtk/gvfs/exec_spaw/4
alex      9503  0.0  0.4  22800  4740 ?        S    16:14   0:00 /usr/lib/gvfs/gvfsd-smb-browse --spawner :1.5 /org/gtk/gvfs/exec_spaw/5
alex      9511  0.0  0.2   5784  2388 ?        S    16:15   0:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.5 /org/gtk/gvfs/exec_spaw/6
alex     13862  2.0  1.4  32940 14972 ?        Sl   16:54   0:00 gnome-terminal
alex     13863  0.0  0.0   2036   700 ?        S    16:54   0:00 gnome-pty-helper
alex     13864  0.4  0.3   5824  3080 pts/0    Rs   16:54   0:00 bash
alex     13915  0.0  0.1   2768  1036 pts/0    R+   16:54   0:00 ps aux


---

### Post by Cuco3 on 2010-03-14
Well, it happened again. Here is the output of the command you gave me, tgalati4:

> [ 4733.848589] Back to C!
[ 4733.848589] ACPI: Waking up from system sleep state S3
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0xf (was 0x0, writing 0x80000)
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0x9 (was 0xfff0, writing 0xda60ba60)
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0x8 (was 0xfff0, writing 0xfe90fa90)
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2a000f0, writing 0x22a000f0)
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0x6 (was 0x0, writing 0x20010100)
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x12000)
[ 4733.848589] pci 0000:00:01.0: restoring config space at offset 0x1 (was 0xa00000, writing 0xa00107)
[ 4733.848589] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4733.848589] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4733.848589] usb usb2: root hub lost power or was reset
[ 4733.848589] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4733.848589] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 4733.848589] usb usb3: root hub lost power or was reset
[ 4733.848589] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 4733.848589] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 4733.848589] usb usb4: root hub lost power or was reset
[ 4733.864025] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[ 4733.864031] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 4733.864103] pci 0000:00:1e.0: setting latency timer to 64
[ 4733.864142] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x50000000)
[ 4733.864156] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800007)
[ 4733.864166] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 4733.864170] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 4733.878565] NVRM: RmPowerManagement: 5
[ 4734.436045] EMU10K1_Audigy 0000:02:01.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900101)
[ 4734.436064] EMU10K1_Audigy 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4734.549703] Emu10k1_gameport 0000:02:01.1: restoring config space at offset 0x4 (was 0x1, writing 0xdc01)
[ 4734.549709] Emu10k1_gameport 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 4734.549716] Emu10k1_gameport 0000:02:01.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900105)
[ 4734.564034] bttv 0000:02:02.0: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900106)
[ 4734.564047] bttv0: reset, reinitialize
[ 4734.564075] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4734.596647] pci 0000:02:02.1: restoring config space at offset 0xf (was 0xff040100, writing 0xff040109)
[ 4734.596664] pci 0000:02:02.1: restoring config space at offset 0x4 (was 0x8, writing 0xda7ff008)
[ 4734.596669] pci 0000:02:02.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 4734.596675] pci 0000:02:02.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900106)
[ 4734.612016] e100 0000:02:08.0: restoring config space at offset 0xf (was 0x38080100, writing 0x3808010b)
[ 4734.612032] e100 0000:02:08.0: restoring config space at offset 0x5 (was 0x1, writing 0xd801)
[ 4734.612037] e100 0000:02:08.0: restoring config space at offset 0x4 (was 0x0, writing 0xfeaff000)
[ 4734.612041] e100 0000:02:08.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 4734.612048] e100 0000:02:08.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900117)
[ 4734.613090] serial 00:07: activated
[ 4734.614051] parport_pc 00:08: activated
[ 4734.614122] sd 0:0:0:0: [sda] Starting disk
[ 4734.864306] ata2.00: ACPI cmd ef/03:44:00:00:00:a0 filtered out
[ 4734.864310] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 4734.912258] ata2.00: configured for UDMA/66
[ 4738.728299] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[ 4738.728303] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 4738.728401] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[ 4738.728404] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[ 4738.752372] ata1.00: configured for UDMA/100
[ 4738.768366] ata1.00: configured for UDMA/100
[ 4738.768370] ata1: EH complete
[ 4738.773950] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 4738.773973] sd 0:0:0:0: [sda] Write Protect is off
[ 4738.773976] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4738.774009] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4738.774046] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 4738.774064] sd 0:0:0:0: [sda] Write Protect is off
[ 4738.774067] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4738.774098] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4739.348013] usb 2-2: reset low speed USB device using uhci_hcd and address 3
[ 4739.668197] PM: resume devices took 5.820 seconds
[ 4739.668206] ------------[ cut here ]------------
[ 4739.668209] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()
[ 4739.668211] Component: resume devices
[ 4739.668213] Modules linked in: snd_emu10k1_synth snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_util_mem binfmt_misc bridge stp bnep vboxnetadp vboxnetflt vboxdrv video output input_polldev lp tuner_simple tuner_types tuner tvaudio bttv videodev v4l1_compat ir_common compat_ioctl32 i2c_algo_bit v4l2_common videobuf_dma_sg videobuf_core ppdev iTCO_wdt iTCO_vendor_support btcx_risc emu10k1_gp pcspkr psmouse tveeprom gameport serio_raw nvidia(P) agpgart parport_pc parport shpchp usbhid e100 mii fbcon tileblit font bitblit softcursor [last unloaded: soundcore]
[ 4739.668265] Pid: 14842, comm: pm-suspend Tainted: P        W  2.6.28-18-generic #59-Ubuntu
[ 4739.668267] Call Trace:
[ 4739.668274]  [<c0139ba0>] warn_slowpath+0x60/0x80
[ 4739.668278]  [<c015397a>] ? down_trylock+0x2a/0x40
[ 4739.668282]  [<c013a1fd>] ? try_acquire_console_sem+0xd/0x30
[ 4739.668288]  [<c02c7f80>] ? kobject_put+0x20/0x50
[ 4739.668294]  [<c04fe446>] ? printk+0x18/0x1a
[ 4739.668297]  [<c0165220>] suspend_test_finish+0x80/0x90
[ 4739.668301]  [<c01652f6>] suspend_devices_and_enter+0xc6/0x160
[ 4739.668304]  [<c04fe446>] ? printk+0x18/0x1a
[ 4739.668307]  [<c0165579>] enter_state+0xc9/0x100
[ 4739.668310]  [<c016562d>] state_store+0x7d/0xc0
[ 4739.668313]  [<c01655b0>] ? state_store+0x0/0xc0
[ 4739.668317]  [<c02c7e44>] kobj_attr_store+0x24/0x30
[ 4739.668322]  [<c020b1b2>] sysfs_write_file+0x92/0xf0
[ 4739.668327]  [<c01bdfd8>] vfs_write+0x98/0x110
[ 4739.668330]  [<c020b120>] ? sysfs_write_file+0x0/0xf0
[ 4739.668333]  [<c01be10d>] sys_write+0x3d/0x70
[ 4739.668337]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[ 4739.668340] ---[ end trace 7451c5abd184ac8b ]---
[ 4739.668371] PM: Finishing wakeup.
[ 4739.668373] Restarting tasks ... done.
[ 4740.773123] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4740.776135] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 4740.805505] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4744.829919] EMU10K1_Audigy 0000:02:01.0: PCI INT A disabled
[ 4745.924283] EMU10K1_Audigy 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4747.673628] CPU0 attaching NULL sched-domain.
[ 4747.673804] CPU0 attaching NULL sched-domain.
[ 4751.488015] eth0: no IPv6 routers present


---

### Post by tgalati4 on 2010-03-14
Well, tail -100 wasn't enough.  

Try tail -200.  We missed the actual sleep event.  "Back to C" means back to the wake state from C0 (deep sleep).

This is interesting:

[ 4739.668265] Pid: 14842, comm: pm-suspend Tainted: P W 2.6.28-18-generic #59-Ubuntu
[ 4739.668267] Call Trace:
[ 4739.668274] [<c0139ba0>] warn_slowpath+0x60/0x80
[ 4739.668278] [<c015397a>] ? down_trylock+0x2a/0x40
[ 4739.668282] [<c013a1fd>] ? try_acquire_console_sem+0xd/0x30

Something clobbered pm-suspend and that caused a traceback dump.  The fact that tainted was used would imply a proprietary driver (like an nVidia or ATI driver).  Did you update any video drivers lately.  

Video cards can go to sleep as well, and perhaps that is causing the entire machine to go down.

The module:

nvidia(P)

looks like a suspect.

---

### Post by Cuco3 on 2010-03-14
Well, it hasn't happened again (yet), but here is dmsg | trail -200 (I only copy+pasted up to "Back to C!"):

> [ 4733.864170] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 4733.878565] NVRM: RmPowerManagement: 5
[ 4734.436045] EMU10K1_Audigy 0000:02:01.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900101)
[ 4734.436064] EMU10K1_Audigy 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4734.549703] Emu10k1_gameport 0000:02:01.1: restoring config space at offset 0x4 (was 0x1, writing 0xdc01)
[ 4734.549709] Emu10k1_gameport 0000:02:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 4734.549716] Emu10k1_gameport 0000:02:01.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900105)
[ 4734.564034] bttv 0000:02:02.0: restoring config space at offset 0x1 (was 0x2900006, writing 0x2900106)
[ 4734.564047] bttv0: reset, reinitialize
[ 4734.564075] bttv0: PLL: 28636363 => 35468950 .. ok
[ 4734.596647] pci 0000:02:02.1: restoring config space at offset 0xf (was 0xff040100, writing 0xff040109)
[ 4734.596664] pci 0000:02:02.1: restoring config space at offset 0x4 (was 0x8, writing 0xda7ff008)
[ 4734.596669] pci 0000:02:02.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802000)
[ 4734.596675] pci 0000:02:02.1: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900106)
[ 4734.612016] e100 0000:02:08.0: restoring config space at offset 0xf (was 0x38080100, writing 0x3808010b)
[ 4734.612032] e100 0000:02:08.0: restoring config space at offset 0x5 (was 0x1, writing 0xd801)
[ 4734.612037] e100 0000:02:08.0: restoring config space at offset 0x4 (was 0x0, writing 0xfeaff000)
[ 4734.612041] e100 0000:02:08.0: restoring config space at offset 0x3 (was 0x0, writing 0x2008)
[ 4734.612048] e100 0000:02:08.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900117)
[ 4734.613090] serial 00:07: activated
[ 4734.614051] parport_pc 00:08: activated
[ 4734.614122] sd 0:0:0:0: [sda] Starting disk
[ 4734.864306] ata2.00: ACPI cmd ef/03:44:00:00:00:a0 filtered out
[ 4734.864310] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 4734.912258] ata2.00: configured for UDMA/66
[ 4738.728299] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[ 4738.728303] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[ 4738.728401] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[ 4738.728404] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[ 4738.752372] ata1.00: configured for UDMA/100
[ 4738.768366] ata1.00: configured for UDMA/100
[ 4738.768370] ata1: EH complete
[ 4738.773950] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 4738.773973] sd 0:0:0:0: [sda] Write Protect is off
[ 4738.773976] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4738.774009] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4738.774046] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[ 4738.774064] sd 0:0:0:0: [sda] Write Protect is off
[ 4738.774067] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4738.774098] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4739.348013] usb 2-2: reset low speed USB device using uhci_hcd and address 3
[ 4739.668197] PM: resume devices took 5.820 seconds
[ 4739.668206] ------------[ cut here ]------------
[ 4739.668209] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()
[ 4739.668211] Component: resume devices
[ 4739.668213] Modules linked in: snd_emu10k1_synth snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_util_mem binfmt_misc bridge stp bnep vboxnetadp vboxnetflt vboxdrv video output input_polldev lp tuner_simple tuner_types tuner tvaudio bttv videodev v4l1_compat ir_common compat_ioctl32 i2c_algo_bit v4l2_common videobuf_dma_sg videobuf_core ppdev iTCO_wdt iTCO_vendor_support btcx_risc emu10k1_gp pcspkr psmouse tveeprom gameport serio_raw nvidia(P) agpgart parport_pc parport shpchp usbhid e100 mii fbcon tileblit font bitblit softcursor [last unloaded: soundcore]
[ 4739.668265] Pid: 14842, comm: pm-suspend Tainted: P        W  2.6.28-18-generic #59-Ubuntu
[ 4739.668267] Call Trace:
[ 4739.668274]  [<c0139ba0>] warn_slowpath+0x60/0x80
[ 4739.668278]  [<c015397a>] ? down_trylock+0x2a/0x40
[ 4739.668282]  [<c013a1fd>] ? try_acquire_console_sem+0xd/0x30
[ 4739.668288]  [<c02c7f80>] ? kobject_put+0x20/0x50
[ 4739.668294]  [<c04fe446>] ? printk+0x18/0x1a
[ 4739.668297]  [<c0165220>] suspend_test_finish+0x80/0x90
[ 4739.668301]  [<c01652f6>] suspend_devices_and_enter+0xc6/0x160
[ 4739.668304]  [<c04fe446>] ? printk+0x18/0x1a
[ 4739.668307]  [<c0165579>] enter_state+0xc9/0x100
[ 4739.668310]  [<c016562d>] state_store+0x7d/0xc0
[ 4739.668313]  [<c01655b0>] ? state_store+0x0/0xc0
[ 4739.668317]  [<c02c7e44>] kobj_attr_store+0x24/0x30
[ 4739.668322]  [<c020b1b2>] sysfs_write_file+0x92/0xf0
[ 4739.668327]  [<c01bdfd8>] vfs_write+0x98/0x110
[ 4739.668330]  [<c020b120>] ? sysfs_write_file+0x0/0xf0
[ 4739.668333]  [<c01be10d>] sys_write+0x3d/0x70
[ 4739.668337]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[ 4739.668340] ---[ end trace 7451c5abd184ac8b ]---
[ 4739.668371] PM: Finishing wakeup.
[ 4739.668373] Restarting tasks ... done.
[ 4740.773123] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4740.776135] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 4740.805505] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4744.829919] EMU10K1_Audigy 0000:02:01.0: PCI INT A disabled
[ 4745.924283] EMU10K1_Audigy 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 4747.673628] CPU0 attaching NULL sched-domain.
[ 4747.673804] CPU0 attaching NULL sched-domain.
[ 4751.488015] eth0: no IPv6 routers present
[ 6746.961622] CPU0 attaching NULL sched-domain.
[ 6746.961810] CPU0 attaching NULL sched-domain.
[ 6748.129530] PM: Syncing filesystems ... done.
[ 6748.137515] PM: Preparing system for mem sleep
[ 6748.137522] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 6748.139041] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 6748.139153] PM: Entering mem sleep
[ 6748.139171] Suspending console(s) (use no_console_suspend to debug)
[ 6748.684102] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 6748.684258] sd 0:0:0:0: [sda] Stopping disk
[ 6748.684924] parport_pc 00:08: disabled
[ 6748.685098] serial 00:07: disabled
[ 6748.700088] ACPI handle has no context!
[ 6748.725044] EMU10K1_Audigy 0000:02:01.0: PCI INT A disabled
[ 6748.725077] ACPI handle has no context!
[ 6748.740032] NVRM: RmPowerManagement: 4
[ 6749.163614] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 6749.163714] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[ 6749.176050] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 6749.176080] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 6749.176110] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 6749.176186] PM: suspend devices took 1.040 seconds
[ 6749.176259] ACPI: Preparing to enter system sleep state S3
[ 6749.176594] Disabling non-boot CPUs ...


---

### Post by Cuco3 on 2010-03-14
[QUOTE=tgalati4]Something clobbered pm-suspend and that caused a traceback dump. The fact that tainted was used would imply a proprietary driver (like an nVidia or ATI driver). Did you update any video drivers lately. 

Video cards can go to sleep as well, and perhaps that is causing the entire machine to go down.

The module:

nvidia(P)

looks like a suspect.[/QUOTE]Hmm, interesting. No, I haven't updated any drivers since installing Ubuntu. I am using the proprietary driver from nVidia, version 180. I know there's a newer driver available from the first time I installed Ubuntu on this system, but I don't know why it hasn't been picked up by the Update Manager.

---

### Post by tgalati4 on 2010-03-14
What is this entry?

[ 4733.878565] NVRM: RmPowerManagement: 5

What is NVRM?  Why is it set to 5?

---

### Post by Cuco3 on 2010-03-14
> **tgalati4 said:**
> What is this entry?

[ 4733.878565] NVRM: RmPowerManagement: 5

What is NVRM?  Why is it set to 5?Your guess is as good as mine. I google searched it but nothing of use comes back, only that it has something to do with nVidia cards.

---

### Post by Cuco3 on 2010-03-14
I think I found the culprit: gnome-screensaver

I closed the process and the computer hasn't randomly suspended since. 

The only problem is that gnome-screensaver is responsible for locking the screen when the computer is put to sleep, so I lose that security feature.

I'm gonna continue to test out the computer to see if it suspends randomly.

---

### Post by tgalati4 on 2010-03-15
I think g-s polls the graphics card; when video goes to sleep, it sends a suspend signal.

---

### Post by Cuco3 on 2010-03-15
> **tgalati4 said:**
> I think g-s polls the graphics card; when video goes to sleep, it sends a suspend signal.I think I understand what you're saying, but why would the video card be going to sleep? Driver issue?

Anyway, still no random suspend. I'm betting now that it is gnome-screensaver process. Which goes back to that script I ran for xbmc that kills gnome-screensaver, but the commands don't appear to do anything that would persist after a restart or cold boot.

I'll try upgrading the video card drivers once I find out how to get the newest version (195 IIRC)

If nothing after that, I'll try an "sudo apt-get purge gnome-screensaver && sudo apt-get install gnome-screensaver" to hopefully delete all configuration information.

---

### Post by Cuco3 on 2010-03-15
double post. mods please delete.

---

### Post by Cuco3 on 2010-03-16
Well, it is the gnome-screensaver, or something that is telling gnome-screensaver to initiate s3 suspend.

I tried upgrading to 195 nVidia drivers but no luck.

I'm just gonna format and reinstall and see how it works. Before I do that, I'm gonna try out Karmic Koala just to see how it is. And if it fixes the problem by some miracle, I might just end up keeping it. I'll get back with more info.

---

### Post by Cuco3 on 2010-03-18
I upgraded to Karmic and the problem fixed itself.

I'm not all that impressed with the performance of Karmic on this computer, the 3d desktop to be specific. If experimenting with the video drivers doesn't improve performance, I'll just re-install Jaunty when I get the chance.

I won't mark the thread solved since it never really did get solved.

---

