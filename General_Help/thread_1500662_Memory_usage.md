---
title: "Memory usage"
date: 2010-06-03
forum: General Help
---

### Post by kernco on 2010-06-03
My system has been running really sluggishly for a while and I've finally identified the problem.  I'm using all my memory which is causing swapping to occur.

When I started trying to fix this problem though, I began to notice some strange things.  For example, I wanted to figure out what processes were taking up all my memory, and the answer I found was that none of them are.  While every tool I use to see how much memory I'm using (sysinfo, top, etc.) reports that I'm pretty much using all 2 GiB plus some swap space, all the process lists that I look at (top, system monitor) only account for maybe 750 MiB of memory.  Yes, I'm seeing root processes not just my own.

When I first boot up, I'm already using 70% of my memory.  This happens whether I run kdm/gdm and boot into KDE or Gnome.  I'm running Ubuntu 10.04.  I installed 9.04 last year when I got the computer and then upgraded to 9.10 and then 10.04 without doing a clean reinstall.

Has anyone seen this happen before?  Where is this missing memory being used up?

---

### Post by bruno9779 on 2010-06-03
Have you tested you memory with memtest86+?

It is not very likely to be, but a bad memory issue could explain what is happening to you

---

### Post by howefield on 2010-06-03
Unused RAM linux is wasted RAM. However, on a fresh boot up, I'd expect to see a 32 bit install of 10.04 take about 270 megabytes of RAM, and about a hundred more if you are running 64 bit. These aren't hard and fast figures, there is a sizeable tolerance, but the point is it shouldn't be any where near 70% of 2 gigabytes. 

I can't give you an answer other than to say, if it were mine, I'd clean install 10.04 after backing everything up. That might not fix it, but it rules out any issues coming from the upgrade path.

---

### Post by kernco on 2010-06-03
I just did a memcheck and it passed.

I'm running the 64-bit version, and have both kubuntu-desktop and ubuntu-desktop installed (initial 9.04 install was with kubuntu, installed ubuntu-desktop later).  I switched to a tty before I even logged in to a window manager and top told me it was using ~500 MiB which seemed reasonable.  I logged into Gnome and immediately checked again, and it was 600 MiB.  I've been logged in for about 10 minutes now.  Chrome is running with a few tabs open, Gwibber and Empathy are open, and now top is telling me I'm using 1.35 GiB.

---

### Post by philinux on 2010-06-03
> **kernco said:**
> I just did a memcheck and it passed.

I'm running the 64-bit version, and have both kubuntu-desktop and ubuntu-desktop installed (initial 9.04 install was with kubuntu, installed ubuntu-desktop later).  I switched to a tty before I even logged in to a window manager and top told me it was using ~500 MiB which seemed reasonable.  I logged into Gnome and immediately checked again, and it was 600 MiB.  I've been logged in for about 10 minutes now.  Chrome is running with a few tabs open, Gwibber and Empathy are open, and now top is telling me I'm using 1.35 GiB.

Something has got a memory leak. What about using htop?

---

### Post by kernco on 2010-06-03
Hmm...well now I'm noticing that I've got a lot of duplicate processes.  For example, I've got three "udevd --daemon" and 3 "rsyslogd -c4" processes running, but those aren't using much memory.  However, I have 10 "/usr/sbin/mysqld" processes running, each taking 1.2% memory.  I have even more console-kit-daemons too, those only take 0.2% memory but I have something like 20 of them it looks like.

My hunch is that boot scripts are being run multiple times.  Any ideas?

---

### Post by snkiz on 2010-06-03
Check you motherboard setting in the bios. I had the same problem with 64 bit, Turned out a setting in my bios that apparently had nothing to do with memory (But it did after all.) was set to run in 32 bit mode. I changed it and my memory use dropped by a good 30-40%

---

### Post by lavinog on 2010-06-07
Try disabling desktop effects...there is a memory leak with some video drivers.

can you post the output of **free** (terminal command)

Some other culprits are:
kernel trace memory used by ureadahead (shouldn't be more than 128M)
inode and dentry cache entries...which doesn't get reported as cache or buffer memory.
try this command and see if it frees up some memory:
```

sync; echo 2|sudo tee /proc/sys/vm/drop_caches

```

---

### Post by kernco on 2010-06-07
> **lavinog said:**
> Try disabling desktop effects...there is a memory leak with some video drivers.
Both my work computer (the one with this problem) and my home computer have nvidia cards, but I'm not seeing this problem at home.  The card models are different, though.  I'm not in the office today so I only have ssh access, so I can't test yet whether turning of desktop effects helps.

> can you post the output of **free** (terminal command)
```

             total       used       free     shared    buffers     cached
Mem:       2055384    2010764      44620          0      24564      80348
-/+ buffers/cache:    1905852     149532
Swap:      1951888     731276    1220612

```


> try this command and see if it frees up some memory:
```

sync; echo 2|sudo tee /proc/sys/vm/drop_caches

```
The output of the command was "2", and it did free up a little memory, but not a significant amount.
```

             total       used       free     shared    buffers     cached
Mem:       2055384    1942532     112852          0      11932      42788
-/+ buffers/cache:    1887812     167572
Swap:      1951888     734664    1217224


```

---

### Post by _khAttAm_ on 2010-06-07
I have same problem on Ubuntu 10.10 Maverick Meerkat 64bit. Also, Lucid Lynx 64bit on my frend's laptop also seems to have the same problem.

I have also tried to stop some processes and services, but that did not help. It seems like a memory leak but I'm unable to figure out what process is doing anything as such.

> **lavinog said:**
> 
try this command and see if it frees up some memory:
```

sync; echo 2|sudo tee /proc/sys/vm/drop_caches

```
No it does not help...


Here is output of free
```
             total       used       free     shared    buffers     cached
Mem:       2046916    1857572     189344          0      52632     439900
-/+ buffers/cache:    1365040     681876
Swap:      1951860     195832    1756028

```

and at the same time around, the output of:
```
sudo ps -eo pid,ppid,rss,vsize,pcpu,pmem,cmd -ww --sort=vsz
```:
```

  PID  PPID   RSS    VSZ %CPU %MEM CMD
    2     0     0      0  0.0  0.0 [kthreadd]
    3     2     0      0  0.0  0.0 [migration/0]
    4     2     0      0  0.0  0.0 [ksoftirqd/0]
    5     2     0      0  0.0  0.0 [watchdog/0]
    6     2     0      0  0.0  0.0 [migration/1]
    7     2     0      0  0.0  0.0 [ksoftirqd/1]
    8     2     0      0  0.0  0.0 [watchdog/1]
    9     2     0      0  0.0  0.0 [events/0]
   10     2     0      0  0.0  0.0 [events/1]
   11     2     0      0  0.0  0.0 [cpuset]
   12     2     0      0  0.0  0.0 [khelper]
   13     2     0      0  0.0  0.0 [netns]
   14     2     0      0  0.0  0.0 [async/mgr]
   15     2     0      0  0.0  0.0 [pm]
   17     2     0      0  0.0  0.0 [sync_supers]
   18     2     0      0  0.0  0.0 [bdi-default]
   19     2     0      0  0.0  0.0 [kintegrityd/0]
   20     2     0      0  0.0  0.0 [kintegrityd/1]
   21     2     0      0  0.0  0.0 [kblockd/0]
   22     2     0      0  0.0  0.0 [kblockd/1]
   23     2     0      0  0.0  0.0 [kacpid]
   24     2     0      0  0.0  0.0 [kacpi_notify]
   25     2     0      0  0.0  0.0 [kacpi_hotplug]
   26     2     0      0  0.0  0.0 [ata/0]
   27     2     0      0  0.0  0.0 [ata/1]
   28     2     0      0  0.0  0.0 [ata_aux]
   29     2     0      0  0.0  0.0 [khubd]
   30     2     0      0  0.0  0.0 [kseriod]
   31     2     0      0  0.0  0.0 [kmmcd]
   34     2     0      0  0.0  0.0 [khungtaskd]
   35     2     0      0  0.0  0.0 [kswapd0]
   36     2     0      0  0.0  0.0 [ksmd]
   37     2     0      0  0.0  0.0 [aio/0]
   38     2     0      0  0.0  0.0 [aio/1]
   39     2     0      0  0.0  0.0 [ecryptfs-kthrea]
   40     2     0      0  0.0  0.0 [crypto/0]
   41     2     0      0  0.0  0.0 [crypto/1]
   44     2     0      0  0.0  0.0 [scsi_eh_0]
   45     2     0      0  0.0  0.0 [scsi_eh_1]
   48     2     0      0  0.0  0.0 [kstriped]
   49     2     0      0  0.0  0.0 [kmpathd/0]
   50     2     0      0  0.0  0.0 [kmpathd/1]
   51     2     0      0  0.0  0.0 [kmpath_handlerd]
   52     2     0      0  0.0  0.0 [ksnapd]
   53     2     0      0  0.0  0.0 [kondemand/0]
   54     2     0      0  0.0  0.0 [kondemand/1]
   55     2     0      0  0.0  0.0 [kconservative/0]
   56     2     0      0  0.0  0.0 [kconservative/1]
  254     2     0      0  0.0  0.0 [jbd2/sda1-8]
  255     2     0      0  0.0  0.0 [ext4-dio-unwrit]
  256     2     0      0  0.0  0.0 [ext4-dio-unwrit]
  575     2     0      0  0.0  0.0 [usbhid_resumer]
  612     2     0      0  0.0  0.0 [flush-8:0]
  617     2     0      0  0.0  0.0 [i915]
  630     2     0      0  0.0  0.0 [hd-audio0]
  633     2     0      0  0.0  0.0 [kjournald]
24759     2     0      0  0.0  0.0 [xfs_mru_cache]
24760     2     0      0  0.0  0.0 [xfslogd/0]
24761     2     0      0  0.0  0.0 [xfslogd/1]
24762     2     0      0  0.0  0.0 [xfsdatad/0]
24763     2     0      0  0.0  0.0 [xfsdatad/1]
24764     2     0      0  0.0  0.0 [xfsconvertd/0]
24765     2     0      0  0.0  0.0 [xfsconvertd/1]
24768     2     0      0  0.0  0.0 [jfsIO]
24769     2     0      0  0.0  0.0 [jfsCommit]
24770     2     0      0  0.0  0.0 [jfsCommit]
24771     2     0      0  0.0  0.0 [jfsSync]
 1811     1   480   4148  0.0  0.0 /bin/sh -c gtk-window-decorator --replace
 6309     1   544   4148  0.0  0.0 /bin/sh /usr/lib/thunderbird-3.0.4/thunderbird
 6314  6309   556   4148  0.0  0.0 /bin/sh /usr/lib/thunderbird-3.0.4/run-mozilla.sh /usr/lib/thunderbird-3.0.4/thunderbird-bin
  966     1   528   4480  0.0  0.0 acpid -c /etc/acpi/events -s /var/run/acpid.socket
  950     1   508   6132  0.0  0.0 /sbin/getty -8 38400 tty4
  955     1   508   6132  0.0  0.0 /sbin/getty -8 38400 tty5
  962     1   508   6132  0.0  0.0 /sbin/getty -8 38400 tty2
  963     1   508   6132  0.0  0.0 /sbin/getty -8 38400 tty3
  965     1   508   6132  0.0  0.0 /sbin/getty -8 38400 tty6
 1625     1   508   6132  0.0  0.0 /sbin/getty -8 38400 tty1
 5730   803  1156   6608  0.0  0.0 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-2a71ce53-8469-4a1b-bc64-7ba560d43411-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
15174 13282   988   7012  0.0  0.0 ps -eo pid,ppid,rss,vsize,pcpu,pmem,cmd -ww --sort=vsz
 1088     1   316   8324  0.0  0.0 /usr/sbin/inetd
15119     1   556  11352  0.0  0.0 /usr/sbin/irqbalance
 1526  1446    28  12008  0.0  0.0 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
13281 13272   804  14540  0.0  0.0 gnome-pty-helper
 1415     1     4  14848  0.0  0.0 /usr/sbin/in.tftpd --listen --user tftp --address 0.0.0.0:69 --secure /var/lib/tftpboot
  299     1   756  16956  0.0  0.0 upstart-udev-bridge --daemon
 6449   305   804  17460  0.0  0.0 udevd --daemon
  305     1   948  17464  0.0  0.0 udevd --daemon
  970     1   148  18936  0.0  0.0 atd
14801  4689  1812  19508  0.0  0.0 /bin/bash
13282 13272  2244  19512  0.0  0.1 bash
  969     1   784  21128  0.0  0.0 cron
 1738  1737  1140  22392  0.0  0.0 hald-runner
 1004     1   744  22396  0.0  0.0 /usr/sbin/kerneloops
    1     0  1772  23868  0.0  0.0 /sbin/init
  761     1  1640  24432  0.0  0.0 dbus-daemon --system --fork
 1764  1738   860  24512  0.0  0.0 hald-addon-input: Listening on /dev/input/event2 /dev/input/event0 /dev/input/event1
 1778  1738   848  24520  0.0  0.0 /usr/lib/hal/hald-addon-cpufreq
 1544     1  1664  24664  0.0  0.0 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
 1529     1   276  26320  0.0  0.0 /usr/bin/dbus-launch --exit-with-session gnome-session
 1781  1738   908  26340  0.0  0.0 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
  889     1   656  28408  0.0  0.0 /sbin/wpa_supplicant -u -s
 1730  1671   848  29116  0.0  0.0 /usr/bin/redshift -l 27.4 85.2
  780   779   136  33980  0.0  0.0 avahi-daemon: chroot helper
  779     1  1040  34108  0.0  0.0 avahi-daemon: running [pravin-desktop.local]
 1293     1  1280  37264  0.0  0.0 /usr/lib/postfix/master
 6045  1293  2160  39328  0.0  0.1 pickup -l -t fifo -u -c
 6046  1293  2236  39488  0.0  0.1 qmgr -l -t fifo -u
 1660     1   944  43696  0.0  0.0 /usr/lib/rtkit/rtkit-daemon
 1839     1  3396  44236  0.0  0.1 /usr/lib/gvfs/gvfsd-metadata
 1552     1  4348  46568  0.0  0.2 /usr/lib/libgconf2-4/gconfd-2
 1737     1  2220  46788  0.0  0.1 /usr/sbin/hald
 1729  1728   836  47092  0.0  0.0 udisks-daemon: not polling any devices
 1895     1  1680  48260  0.0  0.0 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
 1637     1  1872  48524  0.0  0.0 /usr/lib/gvfs/gvfsd
  715     1   384  49344  0.0  0.0 /usr/sbin/sshd
 1686     1  1792  51880  0.0  0.0 /usr/lib/upower/upowerd
 1835     1  2408  52892  0.0  0.1 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
 1664     1  2432  54556  0.0  0.1 /usr/lib/policykit-1/polkitd
 1784     1  1696  55644  0.0  0.0 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
  808     1  1616  57940  0.0  0.0 /usr/sbin/modem-manager
 8653     1  2344  63056  0.0  0.1 /usr/lib/gvfs/gvfsd-computer --spawner :1.9 /org/gtk/gvfs/exec_spaw/2
 1454     1   868  63480  0.0  0.0 nmbd -D
 1728     1  2820  66144  0.0  0.1 /usr/lib/udisks/udisks-daemon
 1419     1  1024  67688  0.0  0.0 /usr/sbin/winbindd
 1453  1419   880  67756  0.0  0.0 /usr/sbin/winbindd
 1938  1419  1376  67840  0.0  0.0 /usr/sbin/winbindd
 1780     1  1532  69620  0.0  0.0 /usr/lib/gvfs/gvfs-afc-volume-monitor
 1633     1  1228  70140  0.0  0.0 gnome-keyring-daemon --start --components=pkcs11
 1311     1   824  71732  0.0  0.0 /usr/sbin/sensord -f daemon
 1455     1   836  75364  0.0  0.0 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
  770     1  2316  76992  0.0  0.1 gdm-binary
 1642     1  1280  78428  0.0  0.0 /usr/lib/gvfs//gvfs-fuse-daemon /home/pravin/.gvfs
  803     1  2884  87996  0.0  0.1 NetworkManager
 1772     1  2944  88776  0.0  0.1 /usr/lib/gvfs/gvfs-gdu-volume-monitor
  677     1  1072  93516  0.0  0.0 smbd -F
  763   677   124  93516  0.0  0.0 smbd -F
  927   770  2048  93864  0.0  0.1 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
 1684  1658  1640  97708  0.0  0.0 /usr/lib/pulseaudio/pulse/gconf-helper
  819     1  1732 122996  0.0  0.0 /usr/sbin/console-kit-daemon --no-daemon
 1073   927 27316 123248  5.5  1.3 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-xiKXRy/database -nolisten tcp vt7
 1850     1  2624 132308  0.0  0.1 /usr/lib/indicator-messages/indicator-messages-service
 1855     1  3020 135144  0.0  0.1 /usr/lib/indicator-session/indicator-session-service
 1857     1  2876 138204  0.0  0.1 /usr/lib/indicator-me/indicator-me-service
 1340   927  1904 139808  0.0  0.0 /usr/lib/gdm/gdm-session-worker
 1848     1  2784 141132  0.0  0.1 /usr/lib/indicator-application/indicator-application-service
 1763  1446  3864 148948  0.0  0.1 /usr/lib/gnome-user-share/gnome-user-share
 1788     1  1760 152784  0.0  0.0 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=18
 1668  1446  3680 160500  0.0  0.1 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 1773     1  2000 165996  0.0  0.0 gnome-screensaver
 1446  1340  4528 166052  0.0  0.2 gnome-session
 1670  1446  4696 167880  0.0  0.2 bluetooth-applet
 1553     1  1068 174960  0.0  0.0 /usr/sbin/apache2 -k start
 1586  1553   264 174960  0.0  0.0 /usr/sbin/apache2 -k start
 1587  1553   264 174960  0.0  0.0 /usr/sbin/apache2 -k start
 1588  1553   264 174960  0.0  0.0 /usr/sbin/apache2 -k start
 1589  1553   264 174960  0.0  0.0 /usr/sbin/apache2 -k start
 1590  1553   264 174960  0.0  0.0 /usr/sbin/apache2 -k start
  806     1  2236 187336  0.0  0.1 /usr/sbin/mysqld
 1679  1446  6132 188856  0.0  0.2 gnome-power-manager
  692     1   884 189436  0.0  0.0 rsyslogd -c4
 1885     1  6384 190188  0.1  0.3 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
 4695  4684 10868 195580  0.0  0.5 awn-applet -p /usr/share/avant-window-navigator/applets/digital-clock.desktop -u 1275409987 -w 18874422 -i 1
 2003  1446  9584 204424  0.0  0.4 update-notifier
 4688  4684 15088 206220  0.4  0.7 awn-applet -p /usr/share/avant-window-navigator/applets/shinyswitcher.desktop -u 1275410065 -w 18874415 -i 1
 1801     1  6156 206836  0.0  0.3 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=30
 1853     1  2720 214228  0.0  0.1 /usr/lib/indicator-sound/indicator-sound-service
 1658     1  4304 214792  0.0  0.2 /usr/bin/pulseaudio --start --log-target=syslog
14234 14233  7776 218932  0.0  0.3 /usr/lib/chromium-browser/chromium-browser
 1799     1  7264 222664  0.0  0.3 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=24
 1874  1446  5612 227700  0.0  0.2 python /usr/share/system-config-printer/applet.py
 1671  1446  8708 228796  0.0  0.4 python /usr/bin/gtk-redshift -l 27.4:85.2
 4693  4684 11880 234020  0.0  0.5 awn-applet -p /usr/share/avant-window-navigator/applets/notification-daemon.desktop -u 1275406735 -w 18874420 -i 1
 1667  1446  9344 235704  0.0  0.4 nm-applet --sm-disable
 1812  1811  8212 276276  0.0  0.4 gtk-window-decorator --replace
 4545     1  8424 278032  1.2  0.4 compiz --replace
 1665  1446  9136 280060  0.0  0.4 parcellite
 4684     1  9760 300748  0.3  0.4 avant-window-navigator
 1807     1  7820 302956  0.0  0.3 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=48
13272     1 16196 305776  0.3  0.7 gnome-terminal
 1726  1446  9016 308188  0.0  0.4 /usr/lib/gnome-disk-utility/gdu-notification-daemon
 4694  4684 13584 311928  0.0  0.6 awn-applet -p /usr/share/avant-window-navigator/applets/garbage.desktop -u 1275406495 -w 18874421 -i 1
 1632     1  7036 316060  0.0  0.3 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 4689  4684 11644 329280  0.0  0.5 awn-applet -p /usr/share/avant-window-navigator/applets/awnterm.desktop -u 1275406204 -w 18874416 -i 1
 4687  4684 13068 329440  0.0  0.6 awn-applet -p /usr/share/avant-window-navigator/applets/quick-prefs.desktop -u 1 -w 18874414 -i 1
 4690  4684 15692 331212  0.1  0.7 awn-applet -p /usr/share/avant-window-navigator/applets/taskmanager.desktop -u 1275406258 -w 18874417 -i 1
 1806     1 13656 345548  0.0  0.6 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=42
14288 14233 13824 362924  0.0  0.6 /usr/lib/chromium-browser/chromium-browser --type=plugin --plugin-path=default_plugin --lang=en-US --plugin-data-dir=/home/pravin/.config/chromium/Default --channel=14233.0x3d61000.604571768
 1680  1446 12604 363408  0.0  0.6 gnome-panel
 4692  4684 12512 364456  0.1  0.6 awn-applet -p /usr/share/avant-window-navigator/applets/sysmon.desktop -u 1275407042 -w 18874419 -i 1
 4696  4684 21604 371772  0.0  1.0 python /usr/share/avant-window-navigator/applets/quit/quit.py --uid=1275410034 --window=18874423 --panel-id=1
 2115     1  2480 372008  0.5  0.1 conky
 4691  4684 23904 374648  0.1  1.1 python /usr/share/avant-window-navigator/applets/hardware-sensors/hardware-sensors.py --uid=1275406601 --window=18874418 --panel-id=1
 1798     1 26776 375412  0.1  1.3 /usr/lib/gnome-globalmenu/GlobalMenu.PanelApplet --oaf-activate-iid=OAFIID:GlobalMenu_PanelApplet_Factory --oaf-ior-fd=18
 2996     1 13352 416756  0.0  0.6 gnote
 1803     1 10956 429452  0.0  0.5 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=36
 4685  4684 44516 555648  0.0  2.1 python /usr/share/avant-window-navigator/applets/GnoMenu/GnoMenu.py --uid=1275406498 --window=18874413 --panel-id=1
 2963     1 79016 676352  0.1  3.8 /usr/bin/perl /usr/bin/shutter
14233     1 64680 685280  1.6  3.1 /usr/lib/chromium-browser/chromium-browser
10717     1 70632 705208  3.5  3.4 filezilla
14236     1  9184 762180  0.0  0.4 /usr/lib/chromium-browser/chromium-browser --type=zygote
 1655  1446 31912 783212  0.1  1.5 nautilus
 6318  6314 100408 880576 0.6  4.9 /usr/lib/thunderbird-3.0.4/thunderbird-bin
14280 14236 18072 1360500 0.0  0.8 /usr/lib/chromium-browser/chromium-browser --type=extension --lang=en-US --force-fieldtest=DnsImpact/_default_enabled_prefetch/GlobalSdch/_global_enable_sdch/ --channel=14233.0x3a47e00.1315516775
11322 14236 28860 1368328 0.1  1.4 /usr/lib/chromium-browser/chromium-browser --type=renderer --lang=en-US --force-fieldtest=CacheSize/CacheSizeGroup_2/DnsImpact/_default_enabled_prefetch/GlobalSdch/_global_enable_sdch/ --channel=14233.0x446be00.1436438697
14277 14236 34144 1389704 0.1  1.6 /usr/lib/chromium-browser/chromium-browser --type=extension --lang=en-US --force-fieldtest=DnsImpact/_default_enabled_prefetch/GlobalSdch/_global_enable_sdch/ --channel=14233.0x3a2e600.2046770047
14353 14236 69876 1424460 0.5  3.4 /usr/lib/chromium-browser/chromium-browser --type=renderer --lang=en-US --force-fieldtest=CacheSize/CacheSizeGroup_2/DnsImpact/_default_enabled_prefetch/GlobalSdch/_global_enable_sdch/ --channel=14233.0x4717400.335883747

```

Any ideas?

PS: I am using Maverick Meerkat:

```
Linux khattam-desktop 2.6.34-5-generic #14-Ubuntu SMP 2010 x86_64 GNU/Linux
```

PPS: I will upgrade to 2.6.35 shortly and let you know what happens.

---

### Post by lavinog on 2010-06-07
> **kernco said:**
> Both my work computer (the one with this problem) and my home computer have nvidia cards, but I'm not seeing this problem at home.  The card models are different, though.  I'm not in the office today so I only have ssh access, so I can't test yet whether turning of desktop effects helps.

What some users were reporting is that even text scrolling causes a memory increase when desktop effects is enabled.  This was noticed with nvidia and fglrx drivers.
It was also discovered that running glxinfo recovers the lost memory, so give that a try when you get to the office.


@_khAttAm_: your code block wasn't terminated (I'm blind now ;) )

---

### Post by lavinog on 2010-06-07
> **_khAttAm_ said:**
> I have same problem on Ubuntu 10.10 Maverick Meerkat 64bit. Also, Lucid Lynx 64bit on my frend's laptop also seems to have the same problem.

I have also tried to stop some processes and services, but that did not help. It seems like a memory leak but I'm unable to figure out what process is doing anything as such.


No it does not help...


The glx leak could be affected by awn also (or anything that uses compositing)

try the glxinfo command and see.

---

### Post by snkiz on 2010-06-07
To further confuse the issue, I'm using nvidia drivers as well. I notice that X itself still has a slow leak and suspend causes X to use more memory when you come out of sleep. I find myself having to restart X every couple days to recover it.

---

### Post by _khAttAm_ on 2010-06-07
I would also like to mention that I am using xorg-edgers PPA (but the problem was there even when I didn't) and have Intel GMA 3xxx on-board video card. Anything someone else can relate to? 

I'll try restarting X, disable compositing and restart and do some other tests and let you know.

---

### Post by _khAttAm_ on 2010-06-07
I booted into 2.6.35-1generic and the problem seems to have magically disappeared.. Let me see if the memory gradually increases again. With Filezilla, Chrome 6 with 5 tabs, Thunderbird 3, awn, apache/mysql, compiz, deluge, gnote and some more, mem usage is just 875MB (swap=0MB).. which seems fair till now...

I will post if it gets worse again.

---

### Post by scorp123 on 2010-06-07
[QUOTE=kernco;9425778] 
```

             total       used       free     shared    buffers     cached
Mem:       2055384    2010764      44620          0      24564      80348
-/+ buffers/cache:    1905852     149532
Swap:      1951888     731276    1220612

```

Looks normal to me. But you say it's sluggish ... How about playing with a few other parameters such as swappiness then?

Open a terminal and type this into it:
```
gksudo gedit /etc/sysctl.conf
```

On the bottom of the file please add these lines:

```
vm.vfs_cache_pressure = 50
vm.swappiness = 1
vm.dirty_ratio = 10
vm.dirty_background_ratio = 5
```

And then to make sure that these settings are really really activated I'd suggest you reboot. If the settings really help then already the boot should feel faster than it did before. Logging in, getting into your desktop and starting and working with multiple applications should feel very snappy and way faster than before.

What happens if the settings don't work -- worst case scenario: Your system feels just as sluggish as it did before. In that case simply remove the settings again. But other than that nothing bad should happen.

What the first two of these lines do is explained here:
[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

The other two about "dirty ratios" tell the Linux kernel to quickly get rid of "dirty" cache memory and clean up faster. [http://en.wikipedia.org/wiki/Cache#Operation](http://en.wikipedia.org/wiki/Cache#Operation)

The point with all these settings is that the defaults "out of the box" on many Linux distributions (including Ubuntu) are way too conservative. With these settings the perceived speed of my desktop drastically increases. Everything feels way snappier and responds quicker than before. Maybe this will help you too?

---

### Post by _khAttAm_ on 2010-06-07
> **scorp123 said:**
> [QUOTE=kernco;9425778] 
```

             total       used       free     shared    buffers     cached
Mem:       2055384    2010764      44620          0      24564      80348
-/+ buffers/cache:    1905852     149532
Swap:      1951888     731276    1220612

```

Looks normal to me. But you say it's sluggish ... How about playing with a few other parameters such as swappiness then?
[/QUOTE]

How would that be normal? since kernco says total memory used by apps is only seen as 750MB.. it is probably a mem leak...

---

### Post by dabl on 2010-06-07
This might help you understand RAM usage with Linux:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by lavinog on 2010-06-07
> **scorp123 said:**
> [QUOTE=kernco;9425778] 
```

             total       used       free     shared    buffers     cached
Mem:       2055384    2010764      44620          0      24564      80348
-/+ buffers/cache:    1905852     149532
Swap:      1951888     731276    1220612

```

Looks normal to me. But you say it's sluggish ... How about playing with a few other parameters such as swappiness then?


It does not look normal.  Normal would be memory being used by buffers and cache to improve the performance.
Only 80M of memory is being used for cache,  With only 149M free, there is still only a chance to cache 230M of files.  Only 10% of his memory can be used to boost his performance.  It is also not right that his swap is holding 730M.  Using this information, the minimum requirement for Ubuntu should be 3G.

---

### Post by kernco on 2010-06-09
I ran glxinfo but that didn't seem to free up any memory.  I've turned off desktop effects and rebooted, so now I'm keeping an eye on my memory.

---

### Post by scorp123 on 2010-06-09
> **kernco said:**
> so now I'm keeping an eye on my memory. Try applying the swappiness and "dirty cache" parameters that I mentioned in my previous posting. Maybe this helps ... ?

Another question --and I am asking this because I ran into this problem recently on one of my servers-- are all your disks and filesystems OK? What filesystem do you use? Ext4? Or something else?

What happened to me is this: One of my servers where we were using the XFS filesystem (back when that server was installed, XFS was considered being better at handling large files than Ext2 or Ext3; Ext4 didn't exist yet) had a serious problem with one of its disks ... and because some processes were not able to get rid of their data in reasonable time (they couldn't write their stuff back because the disk couldn't keep pace) that data started filling that server's RAM pretty fast, and so the system got slower and slower ...  When I checked /var/log/messages there were several warnings regarding I/O errors, filesystem errors, and what not. I had to replace that disk. Taddaaa, problem solved.

You don't happen to observe anything like that on your system? e.g. any mentioning of I/O errors, disk read or write errors or something like that in your log file, e.g. /var/log/messages? Or in the output of "dmesg"?

---

### Post by kernco on 2010-06-09
> **scorp123 said:**
> Try applying the swappiness and "dirty cache" parameters that I mentioned in my previous posting. Maybe this helps ... ?
I'll try these settings, but they're not going to address the root of the problem (memory leaks), just alleviate the symptoms.

> Another question --and I am asking this because I ran into this problem recently on one of my servers-- are all your disks and filesystems OK? What filesystem do you use? Ext4? Or something else?
I have a single hard drive with three partitions: / using Ext4, /home using Ext4, and swap.

> You don't happen to observe anything like that on your system? e.g. any mentioning of I/O errors, disk read or write errors or something like that in your log file, e.g. /var/log/messages? Or in the output of "dmesg"?
I don't see any I/O errors in my system log.

---

### Post by _khAttAm_ on 2010-06-10
> **_khAttAm_ said:**
> I booted into 2.6.35-1generic and the problem seems to have magically disappeared.. Let me see if the memory gradually increases again. With Filezilla, Chrome 6 with 5 tabs, Thunderbird 3, awn, apache/mysql, compiz, deluge, gnote and some more, mem usage is just 875MB (swap=0MB).. which seems fair till now...

I will post if it gets worse again.
Apparently, I figured out later that upgrade to this kernel did not solve the issue. When I use for prolonged time, it still continues using up more and more RAM, eventually starts paging and slowing things down.. 

To test this issue further, I disabled Desktop effects altogether (I had setup many compiz effects, which I backed up and disabled compiz from Appearance->None). Now, RAM usage at startup has decreased to 450MB from 950 MB, which is certainly better. I will use this for prolonged time and let you know what happens...

---

### Post by lavinog on 2010-06-10
> **_khAttAm_ said:**
> Apparently, I figured out later that upgrade to this kernel did not solve the issue. When I use for prolonged time, it still continues using up more and more RAM, eventually starts paging and slowing things down.. 

To test this issue further, I disabled Desktop effects altogether (I had setup many compiz effects, which I backed up and disabled compiz from Appearance->None). Now, RAM usage at startup has decreased to 450MB from 950 MB, which is certainly better. I will use this for prolonged time and let you know what happens...

I just noticed you mentioned you are using xorg-edgers-ppa
There is a known issue with a gem leak.  I think the issue still exists with xorg-edgers:
more info here: [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

what version does this report:
```

glxinfo | grep "GLX version"

```
If it says 1.4, that might be the cause.

---

### Post by _khAttAm_ on 2010-06-13
> **lavinog said:**
> I just noticed you mentioned you are using xorg-edgers-ppa
There is a known issue with a gem leak.  I think the issue still exists with xorg-edgers:
more info here: [https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

what version does this report:
```

glxinfo | grep "GLX version"

```
If it says 1.4, that might be the cause.

yes that was my version.. but I guess the problem existed with or without xorg-edgers.. I have nevertheless, added other PPA and installed the packages that came as upgrades and dist-upgrades.. Memory usage is low till now (783MB of 2GB and no swap usage at all, its just half an hour after restarting though).. I'll post if this solves the problem..

Thank you very much for your help.

---

