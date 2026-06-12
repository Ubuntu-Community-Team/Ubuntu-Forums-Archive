---
title: "constant load on cpu and hardrive"
date: 2006-03-20
forum: General Help
---

### Post by usergentoo on 2006-03-20
Update:: It seems it has something to do with dbus. I diasbled the service. Wow that made a big speed improvement. Could someone tell me what dbus is for? Do I need it? Is there an alternative something else that can replace it? Can it be configured so it dosent cause the lag and constant cpu and hardrive spikes?


Sitting at idle my cpu spikes about every second and hardrive being accessed every 4 seconds.Im sitting here looking at my led's and watching them constantly flicker. Look at my process but dont see anything, but it is showing a constant on the cpu.


Here is my setup
Laptop 1.8ghz PIII 512mb geforce2 go 32mb fresh install kubuntu 5.10
I had this problem before with 5.04 and never could find a answer and been using the latest version of gentoo for awhile now and it didnt give me these problems nor did ubuntu 5.10.******************

---

### Post by usergentoo on 2006-03-20
I think I may have found something. I rebooted and when it said shuting down "Stopping K Display Manager KDM" It stopped the constant flickering. Even before it stop the other processes. Also when I booted back up and it brought KDM back up to login it started again.

Well I thought if I install and use GDM it might fix it but it didnt seem to help any.

---

### Post by coolclassic on 2006-03-20
Whilst your computer is working hard open ksysguard and check to see what process is using cpu.

---

### Post by gnu2tux on 2006-03-20
go to a terminal and type 'ps aux' and paste the results of it here.

That should be enough for us to go on.

---

### Post by usergentoo on 2006-03-20
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1   1560   528 ?        S    08:35   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   08:35   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   08:35   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   08:35   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   08:35   0:00 [kthread]
root         7  0.0  0.0      0     0 ?        S<   08:35   0:00 [kacpid]
root        98  0.0  0.0      0     0 ?        S<   08:35   0:00 [kblockd/0]
root       124  0.0  0.0      0     0 ?        S    08:35   0:00 [pdflush]
root       125  0.0  0.0      0     0 ?        S    08:35   0:00 [pdflush]
root       127  0.0  0.0      0     0 ?        S<   08:35   0:00 [aio/0]
root       126  0.0  0.0      0     0 ?        S    08:35   0:00 [kswapd0]
root       712  0.0  0.0      0     0 ?        S    08:35   0:00 [kseriod]
root      1897  0.0  0.0      0     0 ?        S    08:35   0:00 [khubd]
root      3049  0.0  0.0      0     0 ?        S    08:35   0:00 [kjournald]
root      3175  0.0  0.1   1656   576 ?        S<s  08:35   0:00 udevd --daemon
root      4361  0.0  0.0      0     0 ?        S    08:35   0:00 [khpsbpkt]
root      5197  0.0  0.0      0     0 ?        S    08:35   0:00 [shpchpd_event]
root      5536  0.0  0.0      0     0 ?        S    08:35   0:00 [pccardd]
root      5546  0.0  0.0      0     0 ?        S    08:35   0:00 [pccardd]
root      5633  0.0  0.0      0     0 ?        S    08:35   0:00 [knodemgrd_0]
dhcp      6713  0.0  0.2   2300  1116 ?        Ss   08:36   0:00 dhclient3 -pf /
root      7055  0.0  0.2   1956  1036 ?        Ss   08:36   0:00 /usr/sbin/acpid
syslog    7070  0.0  0.1   1764   772 ?        Ss   08:36   0:00 /sbin/syslogd -
root      7087  0.0  0.0   1560   396 ?        Ss   08:36   0:00 /bin/dd bs 1 if
klog      7089  0.0  0.3   2460  1568 ?        Ss   08:36   0:00 /sbin/klogd -P
105       7102  0.0  0.2   2144  1056 ?        Ss   08:36   0:00 /usr/bin/dbus-d
hal       7115  0.0  0.7   5120  3812 ?        Ss   08:36   0:00 /usr/sbin/hald
hal       7120  0.0  0.1   1864   700 ?        S    08:36   0:00 hald-addon-acpi
hal       7136  0.0  0.1   1868   632 ?        S    08:36   0:00 hald-addon-stor
root      7494  0.0  0.4  10604  2576 ?        Ss   08:36   0:00 /usr/sbin/gdm
root      7499  0.0  0.5  10932  2992 ?        S    08:36   0:00 /usr/sbin/gdm
root      7551  4.6  3.6  21708 18976 ?        SL   08:36   0:36 /usr/X11R6/bin/
cupsys    7562  0.0  0.6   6280  3204 ?        Ss   08:36   0:00 /usr/sbin/cupsd
hplip     7628  0.0  0.2  12608  1276 ?        Ssl  08:36   0:00 /usr/sbin/hpiod
hplip     7652  0.0  1.1   8828  5844 ?        S    08:36   0:00 python /usr/sbi
root      7756  0.0  0.1   1704   744 ?        Ss   08:36   0:00 /sbin/cardmgr
root      7900  0.0  0.1   1548   528 ?        SNs  08:36   0:00 /usr/sbin/power
root      7918  0.0  0.1   1916   808 ?        Ss   08:36   0:00 hcid: processin
root      7924  0.0  0.1   1604   544 ?        Ss   08:36   0:00 /usr/sbin/sdpd
root      7934  0.0  0.0      0     0 ?        S<   08:36   0:00 [krfcommd]
daemon    7968  0.0  0.1   1752   656 ?        Ss   08:36   0:00 /usr/sbin/atd
root      7981  0.0  0.1   1808   848 ?        Ss   08:36   0:00 /usr/sbin/cron
root      8022  0.0  0.0   1556   492 tty1     Ss+  08:36   0:00 /sbin/getty 384
root      8023  0.0  0.0   1556   492 tty2     Ss+  08:36   0:00 /sbin/getty 384
root      8024  0.0  0.0   1556   492 tty3     Ss+  08:36   0:00 /sbin/getty 384
root      8025  0.0  0.0   1560   496 tty4     Ss+  08:36   0:00 /sbin/getty 384
root      8026  0.0  0.0   1560   492 tty5     Ss+  08:36   0:00 /sbin/getty 384
root      8027  0.0  0.0   1556   492 tty6     Ss+  08:36   0:00 /sbin/getty 384
bigbilly  8058  0.0  0.3   4316  1608 ?        Ss   08:36   0:00 /bin/sh /usr/bi
bigbilly  8088  0.0  0.1   3124  1004 ?        Ss   08:36   0:00 /usr/bin/ssh-ag
bigbilly  8111  0.0  2.0  24716 10692 ?        Ss   08:36   0:00 kdeinit Running
bigbilly  8114  0.0  1.8  24032  9632 ?        S    08:36   0:00 dcopserver [kde
bigbilly  8116  0.0  2.1  25108 10940 ?        S    08:36   0:00 klauncher [kdei
bigbilly  8119  0.5  3.3  30068 17420 ?        S    08:36   0:04 kded [kdeinit]
bigbilly  8121  0.0  0.2   2704  1424 ?        S    08:36   0:00 /usr/lib/gamin/
bigbilly  8129  0.1  1.7  22664  8788 ?        S    08:36   0:01 /usr/bin/artsd
bigbilly  8131  0.0  2.4  25780 12864 ?        S    08:36   0:00 kaccess [kdeini
bigbilly  8132  0.0  0.3   4264  1920 ?        S    08:36   0:00 /usr/bin/ivman
bigbilly  8133  0.0  0.0   1544   340 ?        S    08:36   0:00 kwrapper ksmser
bigbilly  8135  0.0  2.5  25880 12964 ?        S    08:36   0:00 ksmserver [kdei
bigbilly  8139  0.2  2.9  27864 15432 ?        S    08:36   0:01 kwin [kdeinit]
bigbilly  8148  0.2  4.2  33684 21864 ?        S    08:36   0:01 kdesktop [kdein
bigbilly  8150  0.3  3.7  31220 19332 ?        S    08:36   0:02 kicker [kdeinit
bigbilly  8151  0.0  2.2  24976 11432 ?        S    08:36   0:00 kio_file [kdein
bigbilly  8154  0.0  2.7  26924 14412 ?        S    08:36   0:00 kbluetoothd --d
bigbilly  8157  0.0  2.7  26680 14124 ?        S    08:36   0:00 klipper [kdeini
bigbilly  8159  0.0  2.9  27904 15344 ?        S    08:36   0:00 kio_uiserver [k
bigbilly  8160  0.0  3.3  29228 17276 ?        S    08:36   0:00 kmix [kdeinit]
bigbilly  8161  0.1  3.0  28248 15780 ?        S    08:36   0:00 katapult -sessi
bigbilly  8163  0.0  3.4  34672 17892 ?        S    08:36   0:00 knotify [kdeini
bigbilly  8169  5.1  5.9  41412 30572 ?        S    08:37   0:37 konqueror [kdei
bigbilly  8174  0.0  2.3  59568 12236 ?        S    08:37   0:00 kio_http [kdein
bigbilly  8178  0.0  2.3  51368 12196 ?        S    08:37   0:00 kio_http [kdein
bigbilly  8179  0.0  2.3  51368 12200 ?        S    08:37   0:00 kio_http [kdein
bigbilly  8180  0.0  2.3  51368 12192 ?        S    08:37   0:00 kio_http [kdein
bigbilly  8184  0.0  2.3  51372 12216 ?        S    08:37   0:00 kio_http [kdein
bigbilly  8309  0.0  2.3  59568 12212 ?        S    08:42   0:00 kio_http [kdein
bigbilly  8318  0.0  2.3  51372 12192 ?        S    08:42   0:00 kio_http [kdein
bigbilly  8324  0.0  2.3  51372 12192 ?        S    08:42   0:00 kio_http [kdein
bigbilly  8406  0.0  2.3  51372 12192 ?        S    08:45   0:00 kio_http [kdein
bigbilly  8517  0.1  0.9   8176  4956 ?        S    08:48   0:00 aspell -a -S -C
bigbilly  8518 19.0  3.2  29444 16516 ?        S    08:49   0:00 konsole [kdeini
bigbilly  8519  0.5  0.3   4628  2012 pts/1    Ss   08:49   0:00 /bin/bash
bigbilly  8528  0.0  0.2   3856  1044 pts/1    R+   08:49   0:00 ps aux

```

---

### Post by usergentoo on 2006-03-20
what processes can i kill? Maybe I can find it that way cause looking at the above I dont see anything. But when I open the ksysguard looking at the gui graph I can see the spikes but I cant catch them to see what the are. I kinda think its kubuntu specific cause ubuntu, gentoo with kde, mepis, pclos. None of them do this.


*Update* The only two processes I see that are bouncing around a bit are xorg and ksysguard. After watching each process for several mintues these are the only ones I see doing anything the rest are at 0

---

### Post by usergentoo on 2006-03-20
ok i couldnt figure out what it was so i booted to terminal and started killing process 1 at a time untill I figured out what it was. So when i killed dbus it seemed to do the trick. Since I know what it was sort of now I need to know what dbus is and what its for.

---

### Post by usergentoo on 2006-03-20
Here is some more info if anybody can help
```
top - 17:01:46 up 55 min,  1 user,  load average: 0.18, 0.16, 0.24
Tasks:  81 total,   1 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3% us,  0.3% sy,  0.0% ni, 99.0% id,  0.0% wa,  0.0% hi,  0.3% si
Mem:    515804k total,   435700k used,    80104k free,    27180k buffers
Swap:  1502036k total,        0k used,  1502036k free,   274652k cached

```
```
top - 17:03:46 up 57 min,  1 user,  load average: 0.31, 0.22, 0.24
Tasks:  81 total,   1 running,  80 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.0% us,  1.0% sy,  0.0% ni, 77.8% id, 13.9% wa,  0.0% hi,  0.3% si
Mem:    515804k total,   435716k used,    80088k free,    27372k buffers
Swap:  1502036k total,        0k used,  1502036k free,   274652k cached

```

---

### Post by gnu2tux on 2006-03-21
From the manual:

Name: dbus
Version: 0.61
revision 0
Description: A message bus system, a simple way for applications to talk to one another.

Fairly useful app to be running. I wouldn't kill it.

Have you performed an update on your system? Perhaps do another one now - there may be a bug in your version which has been fixed in a later update.

If no joy there, you may want to raise a bug, or look into the output of lsof to see what files it has open (perhaps lsof|grep -i dbus)

Regards,

Al.

---

### Post by usergentoo on 2006-03-21
I have the newest version from the repos its 0.36. Could you point me in the right direction to get the new version. 
Thanks

---

### Post by CompShrink on 2006-03-21
There are multiple versions of dbus 0.36, is yours 0.36-2.0Ubuntu7?

And I gnu2tux sounded (at least to me) to be suggesting a full update/upgrade. Even if not, I would suggest it.

Open synaptic, click the "Mark All Upgrades" button, choose "Smart Upgrade" if the option comes up, and then click apply.

or, on command line:

sudo apt-get update
sudo apt-get upgrade

---

### Post by usergentoo on 2006-03-21
Here is the output. 
```
hcid       7547       root  mem       REG        3,1  204084     678894 /usr/lib/libdbus-1.so.1.0.0
kded      11006   bigbilly  mem       REG        3,1   61700     679485 /usr/lib/libdbus-qt-1.so.1.0.0
kded      11006   bigbilly  mem       REG        3,1  204084     678894 /usr/lib/libdbus-1.so.1.0.0
dbus-daem 21764 messagebus  cwd   unknown                               /proc/21764/cwd (readlink: Permission denied)
dbus-daem 21764 messagebus  rtd   unknown                               /proc/21764/root (readlink: Permission denied)
dbus-daem 21764 messagebus  txt   unknown                               /proc/21764/exe (readlink: Permission denied)
dbus-daem 21764 messagebus  mem       REG        3,1  294332     681915 /usr/bin/dbus-daemon
dbus-daem 21764 messagebus  mem       REG        0,0                  0 [heap] (stat: No such file or directory)
dbus-daem 21764 messagebus  mem       REG        3,1   37480    4096192 /lib/tls/i686/cmov/libnss_files-2.3.5.so
dbus-daem 21764 messagebus  mem       REG        3,1   34612    4096194 /lib/tls/i686/cmov/libnss_nis-2.3.5.so
dbus-daem 21764 messagebus  mem       REG        3,1   32380    4096190 /lib/tls/i686/cmov/libnss_compat-2.3.5.so
dbus-daem 21764 messagebus  mem       REG        3,1 1226096    4096183 /lib/tls/i686/cmov/libc-2.3.5.so
dbus-daem 21764 messagebus  mem       REG        3,1   77176    4096189 /lib/tls/i686/cmov/libnsl-2.3.5.so
dbus-daem 21764 messagebus  mem       REG        3,1  125168     677762 /usr/lib/libexpat.so.1.0.0
dbus-daem 21764 messagebus  mem       REG        3,1   86596    4096019 /lib/ld-2.3.5.so
dbus-daem 21764 messagebus NOFD                                         /proc/21764/fd (opendir: Permission denied)

```

---

### Post by usergentoo on 2006-03-21
I did the upgrade here is what it said
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by usergentoo on 2006-03-21
if I file this in a bug report what should I call it?

---

### Post by usergentoo on 2006-03-30
Ive added to the already posted bug about this issue.
One guy told me that by running in recovery mode fixed this issue.

So whats the difference in recovery mode?

Any way not sure if this had anything to do with my 1 year old hardrive dying but had to switch back to my old 20 gig.Ive don some more research and seen in other distro's that several people have the same problem. Didnt notice it till the other day but my desktop's also have this problem but watching the led on the pc gave a constant very faint blink. By disabling dbus it fixed their problem also. I curious to know if this is a kernel releated problem. By using recovery mode is there a difference in the kernel? 

Here is a few things I checked. By installing Breezy or Dapper in server mode only I get this problem. So its not related to the wm. Seems to be something else.

Anyway Im willing to try anything if it will help. Maybe rebuild the kernel later today and see if it helps any.

---

