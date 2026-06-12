---
title: "Unusually high system load"
date: 2006-03-13
forum: General Help
---

### Post by ktulu1115 on 2006-03-13
I've noticed a rather odd problem on my Ubuntu box here - for some reason my system load hangs around 12 consistantly, although CPU usage is next to nothing.  At first I thought it was some background process or something, but I can't seem to locate anything.  I've killed all my open applications in X, even Gnome itself (stopped gdm) - but the load will not budge.  The only odd thing I noticed was that artsd was using a lot of CPU time, but I killed that and still no change.

`ps auwx` returns the following (I can't notice anything unusual):
```

(ktulu@eternal:pts/0)-(7/6 @ 61M)-(11:14 AM)
~$ ps auwx
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   1564   496 ?        S    Mar06   0:01 init [2]         
root         2  0.0  0.0      0     0 ?        SN   Mar06   0:05 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   Mar06   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   Mar06   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kthread]
root         7  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kacpid]
root        87  0.0  0.0      0     0 ?        S<   Mar06   0:00 [kblockd/0]
root       118  0.0  0.0      0     0 ?        S<   Mar06   0:00 [aio/0]
root       117  0.0  0.0      0     0 ?        S    Mar06   0:09 [kswapd0]
root       703  0.0  0.0      0     0 ?        S    Mar06   0:00 [kseriod]
root       925  0.0  0.0      0     0 ?        S    Mar06   0:00 [scsi_eh_0]
root      2069  0.0  0.0      0     0 ?        S<   Mar06   0:00 [ata/0]
root      2072  0.0  0.0      0     0 ?        S    Mar06   0:00 [scsi_eh_1]
root      2073  0.0  0.0      0     0 ?        S    Mar06   0:00 [scsi_eh_2]
root      2074  0.0  0.0      0     0 ?        S    Mar06   0:00 [scsi_eh_3]
root      2096  0.0  0.0      0     0 ?        S    Mar06   0:00 [scsi_eh_4]
root      2097  0.0  0.0      0     0 ?        S    Mar06   0:00 [scsi_eh_5]
root      2109  0.0  0.0      0     0 ?        R    Mar06   0:11 [khubd]
root      2200  0.0  0.0      0     0 ?        D    Mar06   0:00 [scsi_eh_6]
root      2201  0.0  0.0      0     0 ?        D    Mar06   0:21 [usb-storage]
root      4064  0.0  0.0      0     0 ?        S    Mar06   0:01 [kjournald]
root      4270  0.0  0.0   1668   552 ?        S<s  Mar06   0:00 udevd --daemon
root      5869  0.0  0.0      0     0 ?        S    Mar06   0:00 [khpsbpkt]
root      6425  0.0  0.0      0     0 ?        S    Mar06   0:00 [kjournald]
root      6426  0.0  0.0      0     0 ?        S    Mar06   0:02 [kjournald]
root      6427  0.0  0.0      0     0 ?        S    Mar06   0:00 [kjournald]
root      6434  0.0  0.0      0     0 ?        S<   Mar06   0:00 [xfslogd/0]
root      6435  0.0  0.0      0     0 ?        S<   Mar06   0:00 [xfsdatad/0]
root      6436  0.0  0.0      0     0 ?        S    Mar06   0:00 [xfsbufd]
root      6437  0.0  0.0      0     0 ?        S    Mar06   0:00 [xfssyncd]
root      6438  0.0  0.0      0     0 ?        S    Mar06   0:00 [xfssyncd]
root      6439  0.0  0.0      0     0 ?        S    Mar06   0:00 [xfssyncd]
root      6706  0.0  0.0      0     0 ?        S    Mar06   0:00 [shpchpd_event]
root      6753  0.0  0.0      0     0 ?        S    Mar06   0:00 [knodemgrd_0]
root      7168  0.0  0.0      0     0 ?        S    Mar06   0:00 [kgameportd]
root      8987  0.0  0.0   1560   368 ?        Ss   Mar06   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      8989  0.0  0.1   2456  1532 ?        Ss   Mar06   0:00 /sbin/klogd -P /var/run/klogd/kmsg
105       9002  0.0  0.1   2148  1084 ?        Ss   Mar06   0:00 /usr/bin/dbus-daemon --system
hal       9015  0.0  0.3   5192  3868 ?        Ss   Mar06   0:00 /usr/sbin/hald
hal       9020  0.0  0.0   1868   560 ?        S    Mar06   0:00 hald-addon-acpi
hal       9029  0.0  0.0   1872   644 ?        S    Mar06   0:11 hald-addon-storage
hal       9032  0.0  0.0   1872   592 ?        D    Mar06   0:04 hald-addon-storage
hal       9034  0.0  0.0   1868   592 ?        D    Mar06   0:04 hald-addon-storage
hal       9036  0.0  0.0   1872   592 ?        D    Mar06   0:04 hald-addon-storage
hal       9038  0.0  0.0   1872   596 ?        D    Mar06   0:04 hald-addon-storage
hal       9042  0.0  0.0   1868   720 ?        S    Mar06   0:27 hald-addon-storage
root      9449  0.0  0.1   4276  1372 ?        Ss   Mar06   0:00 /usr/lib/postfix/master
postfix   9473  0.0  0.1   4316  1428 ?        S    Mar06   0:00 qmgr -l -t fifo -u -c
root      9563  0.0  0.1   5476  1880 ?        Ss   Mar06   0:01 /usr/sbin/nmbd -D
root      9565  0.0  0.2   7768  2604 ?        Ss   Mar06   0:00 /usr/sbin/smbd -D
root      9583  0.0  0.2   7768  2584 ?        S    Mar06   0:00 /usr/sbin/smbd -D
root      9584  0.0  0.1   3544  1476 ?        Ss   Mar06   0:00 /usr/sbin/sshd
root      9599  0.0  0.0   1920   764 ?        Ss   Mar06   0:00 hcid: processing events
root      9605  0.0  0.0   1612   516 ?        Ss   Mar06   0:00 /usr/sbin/sdpd
root      9615  0.0  0.0      0     0 ?        S<   Mar06   0:00 [krfcommd]
daemon    9647  0.0  0.0   1748   644 ?        Ss   Mar06   0:00 /usr/sbin/atd
root      9727  0.0  0.0   1556   456 tty2     Ss+  Mar06   0:00 /sbin/getty 38400 tty2
root      9728  0.0  0.0   1560   460 tty3     Ss+  Mar06   0:00 /sbin/getty 38400 tty3
root      9729  0.0  0.0   1560   464 tty4     Ss+  Mar06   0:00 /sbin/getty 38400 tty4
root      9730  0.0  0.0   1560   460 tty5     Ss+  Mar06   0:00 /sbin/getty 38400 tty5
root      9731  0.0  0.0   1556   460 tty6     Ss+  Mar06   0:00 /sbin/getty 38400 tty6
ktulu     9919  0.0  0.0   2264   872 ?        S    Mar06   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
root      4715  0.0  0.0   3420   644 ?        DN   Mar09   0:00 /usr/lib/cups/backend/epson
root     11330  0.0  0.0   3420   644 ?        DN   Mar10   0:00 /usr/lib/cups/backend/epson
root     30044  0.0  0.1   2260  1052 tty1     Ss   Mar10   0:00 /bin/login --      
root     31430  0.0  0.0   1816   856 ?        Ss   Mar10   0:00 /usr/sbin/cron
root      9521  0.0  0.0   3424   652 ?        DN   Mar11   0:00 /usr/lib/cups/backend/epson
root     31724  0.0  0.0   1828   996 ?        SNs  Mar12   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root     31759  0.0  0.0   3424   648 ?        DN   Mar12   0:00 /usr/lib/cups/backend/epson
root     16937  0.0  0.0      0     0 ?        S    05:03   0:00 [pdflush]
root     16949  0.0  0.0      0     0 ?        S    05:03   0:00 [pdflush]
root     19092  0.0  0.1   5788  1340 ?        SNs  07:35   0:00 /usr/sbin/cupsd -F
root     19098  0.0  0.0   3424   648 ?        DN   07:35   0:00 /usr/lib/cups/backend/epson
syslog   19571  0.0  0.0   1760   780 ?        SNs  07:40   0:00 /sbin/syslogd -u syslog
ktulu    21664  0.0  0.2   4724  2092 tty1     S    10:07   0:00 -bash
postfix  21934  0.0  0.1   4276  1296 ?        S    10:37   0:00 pickup -l -t fifo -u -c
ktulu    22215  0.4  0.0   2140  1024 tty1     S+   11:12   0:00 top
root     22216  0.0  0.1   6284  1872 ?        Ss   11:14   0:00 sshd: ktulu [priv]
ktulu    22220  0.0  0.1   6284  1956 ?        S    11:14   0:00 sshd: ktulu@pts/0
ktulu    22221  0.0  0.1   4692  2032 pts/0    Ss   11:14   0:00 -bash
ktulu    22310  0.0  0.1   3864  1040 pts/0    R+   11:14   0:00 ps auwx
```

I first recall this problem after I tried to run Azureus, supposedly there is a known issue with v1.4.2 and Azureus causing high load like I'm experiencing - I tried upgrading to a newer version but was having pacakge dependency issues and abandoned it.  Also tried a few reboots, nothing works.  Any ideas??

---

### Post by ktulu1115 on 2006-03-13
Actually I think I got it fixed - I was having an issue with VMPlayer and didn't do a final reboot after the removal of the software.  I think that did the trick.

---

