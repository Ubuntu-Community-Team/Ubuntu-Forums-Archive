---
title: "init services not startable?"
date: 2011-05-23
forum: General Help
---

### Post by macho on 2011-05-23
I was having problems with cron and noticed the daemon wasn't running, and now it seems maybe init isn't starting any services. Is that possible?

```
# initctl list
```

...gives no output. Nor does "start cron" or "status cron". When I do Ctrl+Alt+F1 (,F2, etc.) it looks like the consoles haven't even started. It does seem like some stuff is started, but I'm not familiar with this enough to have a clue what's going on:

```
$ ps aux | grep daemon
root       361  0.0  0.0  17052   292 ?        S    13:26   0:00 upstart-udev-bridge --daemon
root       383  0.0  0.0  21856   924 ?        S<s  13:26   0:00 udevd --daemon
102        872  0.0  0.1  24952  2196 ?        Ss   13:26   0:03 dbus-daemon --system --fork --activation=upstart
avahi      894  0.0  0.0  32128   992 ?        S    13:26   0:00 avahi-daemon: running [slartibartfast.local]
avahi      895  0.0  0.0  32008   132 ?        S    13:26   0:00 avahi-daemon: chroot helper
root       901  0.0  0.1  61972  2472 ?        Sl   13:26   0:00 /usr/sbin/console-kit-daemon --no-daemon
macho     1061  0.0  0.1  26528  2692 ?        Ss   13:26   0:01 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
macho     1077  0.0  0.0  88548  1500 ?        Sl   13:26   0:00 /usr/bin/gnome-keyring-daemon --start --components=pkcs11
macho     1080  0.0  0.5 424660  9152 ?        Ssl  13:26   0:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
macho     1091  0.0  0.0  81008  1100 ?        Ssl  13:26   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/macho/.gvfs
rtkit     1100  0.0  0.0  37628   876 ?        SNl  13:26   0:00 /usr/lib/rtkit/rtkit-daemon
macho     1157  0.0  0.4 116516  7520 ?        Sl   13:26   0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
root      1299  0.0  0.1  62148  2240 ?        Sl   13:27   0:00 /usr/lib/udisks/udisks-daemon
root      1300  0.0  0.0  45168   496 ?        S    13:27   0:00 udisks-daemon: polling /dev/sr0
macho     1411  0.0  0.3 221972  6860 ?        S    13:27   0:00 /usr/lib/bamf/bamfdaemon
macho     1425  0.0  0.1 111376  2356 ?        Sl   13:27   0:00 /usr/lib/unity-place-files/unity-files-daemon
macho     1426  0.0  0.2 134820  5288 ?        Sl   13:27   0:00 /usr/lib/unity-place-applications/unity-applications-daemon
macho     1544  0.0  0.2 176844  4084 ?        S    13:27   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
macho     1565  0.1  0.4 298912  8780 ?        Sl   13:27   0:05 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
macho     4622  0.0  0.0   9140  1020 pts/1    S+   14:51   0:00 grep daemon
```

Any thoughts?

---

### Post by macho on 2011-05-24
bump

---

### Post by seawolf167 on 2011-05-24
To see your init.d

```
ls /etc/init.d
```to check if cron is running

```
ps -ef | grep -i cron
```to start|stop|restart a service (like cron)

```
sudo service cron start|restart|stop
```

---

### Post by macho on 2011-05-24
Thanks. For some reason this doesn't seem to work:

```
$ sudo service cron start
```

This gives no output (apart from asking for my password).

```
$ ps -ef | grep -i cron
macho     6446  6438  0 08:13 pts/0    00:00:00 grep -i cron
$ ls /etc/init.d/ -1
acpid
acpi-support
alsa-restore
alsa-store
anacron
apparmor
apport
atd
atieventsd
avahi-daemon
binfmt-support
bluetooth
bootlogd
brltty
console-setup
cron
cups
dbus
dmesg
dns-clean
ecryptfs-utils-restore
ecryptfs-utils-save
failsafe-x
fancontrol
gdm
grub-common
halt
hostname
hwclock
hwclock-save
irqbalance
kerneloops
killprocs
lm-sensors
module-init-tools
networking
network-interface
network-interface-security
network-manager
ondemand
pcmciautils
plymouth
plymouth-log
plymouth-splash
plymouth-stop
plymouth-upstart-bridge
pppd-dns
procps
pulseaudio
rc
rc.local
rcS
README
reboot
rsync
rsyslog
saned
screen-cleanup
sendsigs
setvtrgb
single
skeleton
speech-dispatcher
stop-bootlogd
stop-bootlogd-single
sudo
udev
udev-fallback-graphics
udev-finish
udevmonitor
udevtrigger
ufw
umountfs
umountnfs.sh
umountroot
unattended-upgrades
urandom
x11-common 

```

---

### Post by seawolf167 on 2011-05-24
Does 

```
sudo service cron restart
```

give any output? Maybe something like:

cron start/running, process 12345?

---

### Post by macho on 2011-05-24
No output for "sudo service cron restart".

I checked /var/log/syslog afterward and I can see pam_sm_authenticate stuff for the invocation of sudo, but nothing else.

---

### Post by seawolf167 on 2011-05-24
Can you please run the following commands

```
sudo apt-get purge upstart
sudo apt-get install upstart
```

then log out, log back in, and retry

```
sudo service cron restart
```

---

### Post by webofunni on 2011-05-24
What is the O/P of 

```

dpkg -L cron
grep -v ^# /etc/init/cron.conf
sudo start cron;tail -10 /var/log/syslog
sudo /etc/init.d/cron start

```

---

### Post by macho on 2011-05-25
Thanks. I couldn't purge upstart, seemingly because of dependency problems:

```
$ sudo apt-get purge upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 procps : Depends: upstart-job
          Depends: initscripts but it is not going to be installed
E: Broken packages
```

webofunni: here's the output.

```
$ dpkg -L cron
/.
/usr
/usr/bin
/usr/bin/crontab
/usr/sbin
/usr/sbin/cron
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/crontab.1.gz
/usr/share/man/man5
/usr/share/man/man5/crontab.5.gz
/usr/share/man/man8
/usr/share/man/man8/cron.8.gz
/usr/share/doc
/usr/share/doc/cron
/usr/share/doc/cron/FEATURES
/usr/share/doc/cron/THANKS
/usr/share/doc/cron/README
/usr/share/doc/cron/README.anacron
/usr/share/doc/cron/README.Debian
/usr/share/doc/cron/TODO.Debian
/usr/share/doc/cron/copyright
/usr/share/doc/cron/examples
/usr/share/doc/cron/examples/stats-cron.pl.gz
/usr/share/doc/cron/examples/crontab2english.pl.gz
/usr/share/doc/cron/NEWS.Debian.gz
/usr/share/doc/cron/changelog.Debian.gz
/usr/share/bug
/usr/share/bug/cron
/usr/share/bug/cron/script
/usr/share/bug/cron/control
/etc
/etc/cron.hourly
/etc/cron.hourly/.placeholder
/etc/cron.daily
/etc/cron.daily/.placeholder
/etc/cron.daily/standard
/etc/cron.weekly
/etc/cron.weekly/.placeholder
/etc/cron.monthly
/etc/cron.monthly/.placeholder
/etc/cron.d
/etc/cron.d/.placeholder
/etc/init.d
/etc/pam.d
/etc/pam.d/cron
/etc/init
/etc/init/cron.conf
/etc/default
/etc/default/cron
/etc/crontab
/var
/var/spool
/var/spool/cron
/var/spool/cron/crontabs
/etc/init.d/cron
```

```
$ grep -v ^# /etc/init/cron.conf 

description	"regular background program processing daemon"

start on runlevel [2345]
stop on runlevel [!2345]

expect fork
respawn

exec cron
```

```
$ sudo start cron;tail -10 /var/log/syslog
May 24 03:45:56 localhost kernel: [51546.572735] wlan0: RX AssocResp from 00:1c:f0:43:7f:72 (capab=0x431 status=0 aid=1)
May 24 03:45:56 localhost kernel: [51546.572737] wlan0: associated
May 24 05:39:23 localhost sudo: pam_sm_authenticate: Called
May 24 05:39:23 localhost sudo: pam_sm_authenticate: username = [macho]
May 24 08:13:50 localhost sudo: pam_sm_authenticate: Called
May 24 08:13:50 localhost sudo: pam_sm_authenticate: username = [macho]
May 24 09:09:03 localhost sudo: pam_sm_authenticate: Called
May 24 09:09:03 localhost sudo: pam_sm_authenticate: username = [macho]
May 24 23:13:24 localhost sudo: pam_sm_authenticate: Called
May 24 23:13:24 localhost sudo: pam_sm_authenticate: username = [macho]
```

```
$ sudo /etc/init.d/cron start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cron start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start cron
```

---

### Post by webofunni on 2011-05-25
Are you able to start it using 

```

sudo /usr/sbin/cron

```

?

You can try the following commands for upstart to avoid dep problem. 

```

sudo dpkg -P --force depends upstart
sudo apt-get install upstart

```

---

### Post by seawolf167 on 2011-05-25
You also should make sure everything else is up-to-date and working properly

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo apt-get install upstart
```

---

### Post by macho on 2011-05-25
```
sudo /usr/sbin/cron
```

This works! Thanks.

But what do you figure is the best way to get it to automatically start on a system startup/reboot?

I successfully ran your other suggested commands seawolf & webofunni, but they don't seem to have had any effect. Getting things like "sudo service cron start" to work would be ideal.

---

### Post by webofunni on 2011-05-25
```

sudo strace -vvv start cron

```

?

---

### Post by macho on 2011-05-25
```
$ sudo strace -vvv start cron
[sudo] password for macho: 
execve("/sbin/start", ["start", "cron"], ["TERM=xterm", "PATH=/usr/local/sbin:/usr/local/"..., "LANG=en_CA.UTF-8", "PS1=\\[\\033[1;37m\\][\\[\\033[1;31m\\"..., "HOME=/home/macho", "LANGUAGE=en_CA:en", "DISPLAY=:0", "COLORTERM=gnome-terminal", "XAUTHORITY=/var/run/gdm/auth-for"..., "SHELL=/bin/bash", "LOGNAME=root", "USER=root", "USERNAME=root", "MAIL=/var/mail/root", "SUDO_COMMAND=/usr/bin/strace -vv"..., "SUDO_USER=macho", "SUDO_UID=1000", "SUDO_GID=1000"]) = 0
brk(0)                                  = 0x146a000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f626a9d5000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_dev=makedev(8, 1), st_ino=2883727, st_mode=S_IFREG|0644, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=264, st_size=132822, st_atime=2011/05/23-14:37:07, st_mtime=2011/05/23-14:37:07, st_ctime=2011/05/23-14:37:07}) = 0
mmap(NULL, 132822, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f626a9b4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\360\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_dev=makedev(8, 1), st_ino=262279, st_mode=S_IFREG|0755, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=3200, st_size=1638120, st_atime=2011/05/03-13:22:17, st_mtime=2011/04/11-06:26:01, st_ctime=2011/04/30-12:59:40}) = 0
mmap(NULL, 3749080, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f626a423000
mprotect(0x7f626a5ad000, 2093056, PROT_NONE) = 0
mmap(0x7f626a7ac000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x189000) = 0x7f626a7ac000
mmap(0x7f626a7b1000, 21720, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f626a7b1000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f626a9b3000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f626a9b1000
arch_prctl(ARCH_SET_FS, 0x7f626a9b1720) = 0
mprotect(0x7f626a7ac000, 16384, PROT_READ) = 0
mprotect(0x604000, 4096, PROT_READ)     = 0
mprotect(0x7f626a9d7000, 4096, PROT_READ) = 0
munmap(0x7f626a9b4000, 132822)          = 0
brk(0)                                  = 0x146a000
brk(0x148b000)                          = 0x148b000
open("/usr/lib/locale/locale-archive", O_RDONLY) = 3
fstat(3, {st_dev=makedev(8, 1), st_ino=1573007, st_mode=S_IFREG|0644, st_nlink=1, st_uid=0, st_gid=0, st_blksize=4096, st_blocks=5328, st_size=2772576, st_atime=2011/05/03-19:24:56, st_mtime=2011/04/30-13:07:59, st_ctime=2011/04/30-13:07:59}) = 0
mmap(NULL, 2772576, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f626a17e000
close(3)                                = 0
close(1)                                = 0
close(2)                                = 0
exit_group(0)                           = ?
```

---

### Post by webofunni on 2011-05-25
which version of ubuntu u r using ? 

```

lsb_release -a

```

---

### Post by macho on 2011-05-25
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty
```

---

### Post by webofunni on 2011-05-26
mmap looks different. I need more details, also try those as actual room. Need to check, if there any environment variable problem with the user. watch sudo su - ;-)

```

ps auxxxfx
sudo su -
initctl list
initctl status udev
initctl --version
initctl -v start cron
initctl -v start udev

```

---

### Post by macho on 2011-05-26
I'm running on amd64, could that be it?

```
$ ps auxxxfx
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         2  0.0  0.0      0     0 ?        S    May25   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    May25   0:00  \_ [ksoftirqd]
root         6  0.0  0.0      0     0 ?        S    May25   0:00  \_ [migration]
root         7  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [cpuset]
root         8  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [khelper]
root         9  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [netns]
root        10  0.0  0.0      0     0 ?        S    May25   0:00  \_ [sync_supe]
root        11  0.0  0.0      0     0 ?        S    May25   0:00  \_ [bdi-defau]
root        12  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kintegrit]
root        13  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kblockd]
root        14  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kacpid]
root        15  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kacpi_not]
root        16  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kacpi_hot]
root        17  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [ata_sff]
root        18  0.0  0.0      0     0 ?        S    May25   0:00  \_ [khubd]
root        19  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [md]
root        46  0.0  0.0      0     0 ?        S    May25   0:00  \_ [khungtask]
root        47  0.0  0.0      0     0 ?        S    May25   0:00  \_ [kswapd0]
root        48  0.0  0.0      0     0 ?        SN   May25   0:00  \_ [ksmd]
root        49  0.0  0.0      0     0 ?        S    May25   0:00  \_ [fsnotify_]
root        50  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [aio]
root        51  0.0  0.0      0     0 ?        S    May25   0:00  \_ [ecryptfs-]
root        52  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [crypto]
root        56  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kthrotld]
root        68  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kmpathd]
root        69  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kmpath_ha]
root        70  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kondemand]
root        71  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kconserva]
root       234  0.0  0.0      0     0 ?        S    May25   0:02  \_ [scsi_eh_0]
root       237  0.0  0.0      0     0 ?        S    May25   0:00  \_ [scsi_eh_1]
root       262  0.0  0.0      0     0 ?        S    May25   0:00  \_ [scsi_eh_2]
root       263  0.0  0.0      0     0 ?        S    May25   0:00  \_ [scsi_eh_3]
root       264  0.0  0.0      0     0 ?        S    May25   0:00  \_ [scsi_eh_4]
root       265  0.0  0.0      0     0 ?        S    May25   0:00  \_ [scsi_eh_5]
root       295  0.0  0.0      0     0 ?        S    May25   0:00  \_ [jbd2/sda1]
root       296  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [ext4-dio-]
root       626  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [edac-poll]
root       742  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [kpsmoused]
root       754  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [cfg80211]
root       824  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [ext4-dio-]
root       845  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [hd-audio0]
root       861  0.0  0.0      0     0 ?        S    May25   0:01  \_ [jbd2/sdb1]
root       862  0.0  0.0      0     0 ?        S<   May25   0:00  \_ [ext4-dio-]
root      1010  0.0  0.0      0     0 ?        S    May25   0:00  \_ [firegl]
root      1011  0.0  0.0      0     0 ?        S    May25   0:00  \_ [firegl]
root      1012  0.0  0.0      0     0 ?        S    May25   0:00  \_ [firegl]
root      1077  0.0  0.0      0     0 ?        S    May25   0:01  \_ [flush-8:1]
root      1078  0.0  0.0      0     0 ?        S    May25   0:00  \_ [flush-8:0]
root      3169  0.0  0.0      0     0 ?        S    07:46   0:00  \_ [kworker/0]
root      3173  0.0  0.0      0     0 ?        S    07:53   0:00  \_ [kworker/u]
root      3182  0.0  0.0      0     0 ?        S    08:11   0:00  \_ [kworker/u]
root      3185  0.0  0.0      0     0 ?        S    08:12   0:00  \_ [kworker/0]
root      3231  0.0  0.0      0     0 ?        S    08:17   0:00  \_ [kworker/0]
root      3232  0.0  0.0      0     0 ?        S    08:17   0:00  \_ [kworker/u]
root         1  0.0  0.0  23872  1372 ?        Ss   May25   0:00 /sbin/init
root       315  0.0  0.0  19080     4 ?        S    May25   0:00 /sbin/ureadahea
root       358  0.0  0.0  17052   504 ?        S    May25   0:00 upstart-udev-br
root       371  0.0  0.0  21856   384 ?        S<s  May25   0:00 udevd --daemon
root       616  0.0  0.0  22000   568 ?        S<   May25   0:00  \_ udevd --dae
root       617  0.0  0.0  22000   192 ?        S<   May25   0:00  \_ udevd --dae
syslog     884  0.0  0.0  54456   876 ?        Sl   May25   0:00 rsyslogd -c4
102        888  0.0  0.0  24732  1692 ?        Ss   May25   0:02 dbus-daemon --s
root       902  0.0  0.1  79192  2144 ?        Ssl  May25   0:00 gdm-binary
root       988  0.0  0.1  93796  1824 ?        Sl   May25   0:00  \_ /usr/lib/gd
root       994  0.5  5.9 290348 106140 tty7    Ss+  May25   8:05      \_ /usr/bi
root      1027  0.0  0.0 122596  1700 ?        Sl   May25   0:00      \_ /usr/li
macho     1036  0.0  0.2 173844  3900 ?        Ssl  May25   0:00          \_ gno
macho     1071  0.0  0.0  12092    16 ?        Ss   May25   0:00              \_
macho     1109  0.5  4.0 597040 73544 ?        Sl   May25   7:20              \_
macho     1357  0.0  0.0   4220   412 ?        Ss   May25   0:00              | 
macho     1358  0.0  0.3 182680  6316 ?        Sl   May25   0:02              | 
macho     1149  0.0  0.6 458236 11572 ?        Sl   May25   0:15              \_
macho     1162  0.0  0.1 156840  2992 ?        Sl   May25   0:00              \_
macho     1163  0.0  0.3 325484  5940 ?        Sl   May25   0:04              \_
macho     1167  0.0  0.2 277516  4092 ?        Sl   May25   0:00              \_
macho     1168  0.0  0.1 185728  3412 ?        Sl   May25   0:00              \_
macho     1170  0.0  0.1 162608  2904 ?        Sl   May25   0:00              \_
macho     1175  0.0  0.2 201344  4072 ?        Sl   May25   0:00              \_
macho     1542  0.0  0.1 176496  3160 ?        S    May25   0:00              \_
macho     1627  0.0  0.2 233128  4280 ?        S    May25   0:02              \_
macho     1749  0.0  0.4 253744  8344 ?        Sl   May25   0:00              \_
avahi      908  0.0  0.0  32128  1080 ?        S    May25   0:00 avahi-daemon: r
avahi      909  0.0  0.0  32008   148 ?        S    May25   0:00  \_ avahi-daemo
root       910  0.0  0.0  75512   984 ?        Ss   May25   0:00 /usr/sbin/cupsd
root       913  0.0  0.1  92780  2948 ?        Ssl  May25   0:02 NetworkManager
root      1016  0.0  0.0   7084   596 ?        S    May25   0:00  \_ /sbin/dhcli
root       917  0.0  0.0  64656  1704 ?        S    May25   0:00 /usr/sbin/modem
root       918  0.0  0.1  59768  2080 ?        Sl   May25   0:00 /usr/sbin/conso
root       920  0.0  0.1  64156  2116 ?        Sl   May25   0:00 /usr/lib/policy
root       998  0.0  0.0  28812  1064 ?        S    May25   0:00 /sbin/wpa_suppl
macho     1074  0.0  0.0  26400   220 ?        S    May25   0:00 /usr/bin/dbus-l
macho     1075  0.0  0.1  26704  2568 ?        Ss   May25   0:07 //bin/dbus-daem
macho     1083  0.0  0.1  57264  3240 ?        S    May25   0:03 /usr/lib/libgco
macho     1090  0.0  0.1  88544  1928 ?        Sl   May25   0:00 /usr/bin/gnome-
macho     1094  0.0  0.3 460028  6716 ?        Ssl  May25   0:04 /usr/lib/gnome-
macho     1100  0.0  0.0  51972  1616 ?        S    May25   0:00 /usr/lib/gvfs/g
macho     1105  0.0  0.0  81008  1100 ?        Ssl  May25   0:00 /usr/lib/gvfs//
macho     1112  0.0  0.2 283492  5224 ?        S<sl May25   1:15 /usr/bin/pulsea
macho     1192  0.0  0.0 115836  1584 ?        Sl   May25   0:00  \_ /usr/lib/pu
rtkit     1114  0.0  0.0  37628   892 ?        SNl  May25   0:00 /usr/lib/rtkit/
macho     1172  0.0  0.4 116324  8288 ?        Sl   May25   0:00 /usr/bin/python
macho     1191  0.0  0.0   6860   428 ?        S    May25   0:00  \_ /bin/cat
macho     1201  0.0  0.0      0     0 ?        Z    May25   0:00  \_ 
macho     1194  0.0  1.8 496064 34084 ?        Ssl  May25   0:19 /home/macho/.dr
macho     1199  0.0  0.1  56700  2092 ?        S    May25   0:00 /usr/lib/gvfs/g
macho     1208  0.0  0.4 231872  8440 ?        Sl   May25   0:01 /usr/lib/notify
root      1218  0.0  0.1  77624  2220 ?        Sl   May25   0:00 /usr/lib/upower
macho     1222  0.0  0.3 263956  6208 ?        Sl   May25   0:01 /usr/lib/evolut
macho     1307  0.0  0.1  67932  2504 ?        S    May25   0:00 /usr/lib/gvfs/g
root      1309  0.0  0.1  62152  2888 ?        Sl   May25   0:03 /usr/lib/udisks
root      1310  0.0  0.0  45168   508 ?        S    May25   0:04  \_ udisks-daem
macho     1313  0.0  0.0  59568  1392 ?        S    May25   0:00 /usr/lib/gvfs/g
macho     1316  0.0  0.0  73364  1388 ?        Sl   May25   0:00 /usr/lib/gvfs/g
macho     1345  0.0  0.1  56928  1924 ?        Sl   May25   0:00 /usr/lib/d-conf
macho     1361  0.0  0.8 392652 16108 ?        Sl   May25   0:27 /usr/lib/unity/
macho     1364  0.0  0.1 111268  2532 ?        Sl   May25   0:00 /usr/lib/unity-
macho     1365  0.0  0.1 133928  2796 ?        Sl   May25   0:01 /usr/lib/unity-
macho     1396  0.0  0.2 219308  4828 ?        S    May25   0:00 /usr/lib/bamf/b
macho     1405  0.0  0.2 266788  3940 ?        Sl   May25   0:00 /usr/lib/indica
macho     1406  0.0  0.1 165716  2056 ?        Sl   May25   0:00 /usr/lib/indica
macho     1408  0.0  0.4 249704  7896 ?        Sl   May25   0:01 /usr/lib/indica
macho     1410  0.0  0.1 170700  2988 ?        Sl   May25   0:00 /usr/lib/indica
macho     1412  0.0  0.1 176072  2596 ?        Sl   May25   0:00 /usr/lib/indica
macho     1421  0.0  0.2 143056  3688 ?        Sl   May25   0:03 /usr/lib/indica
macho     1448  0.0  0.1  93680  2452 ?        Sl   May25   0:01 /usr/lib/geoclu
macho     1454  0.0  0.0 175964  1648 ?        Ss   May25   0:00 gnome-screensav
macho     1456  0.0  0.0  52232  1512 ?        S    May25   0:00 /usr/lib/gvfs/g
macho     1484  0.0  0.0  45732  1448 ?        S    May25   0:00 /usr/lib/gvfs/g
macho     1544  4.9 27.0 1408388 485832 ?      Sl   May25  71:34 /usr/lib/firefo
macho     1638  0.1  0.2 235724  4656 ?        Sl   May25   1:27  \_ /usr/lib/fi
macho     1653  0.6  1.5 136128 28296 ?        Sl   May25   9:19      \_ /usr/li
macho     1650  0.0  1.0 298572 19240 ?        Sl   May25   1:12 /usr/bin/python
root      1773  0.0  0.0  21768  1076 ?        Ss   May25   0:00 /usr/sbin/cron
macho     1816  0.0  3.2 716440 58112 ?        Sl   May25   0:26 /usr/lib/thunde
macho     2459  0.0  0.0  12312  1276 ?        S    May25   0:00 bash /usr/bin/b
macho     2465  0.5  4.2 931836 75512 ?        Sl   May25   3:31  \_ banshee /us
macho     2487  0.0  1.1 213968 19908 ?        S    May25   0:00 /usr/bin/python
macho     3255  1.8  0.8 261420 15720 ?        Sl   08:20   0:00 gnome-terminal
macho     3261  0.0  0.0  14612   816 ?        S    08:20   0:00  \_ gnome-pty-h
macho     3262  0.0  0.1  21016  2284 pts/0    Ss   08:20   0:00  \_ bash
macho     3264  0.0  0.0  17952  1168 pts/0    R+   08:20   0:00      \_ ps auxx
$ sudo su -
# initctl list
# initctl status udev
# initctl --version
true (GNU coreutils) 8.5
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Jim Meyering.
# initctl -v start cron
# initctl -v start udev

```

---

### Post by webofunni on 2011-05-26
First of all initctl is not a part of GNU coreutils. That is a part of upstart. 

```

dpkg -S `which initctl`
ls -l `which initctl`
file `which initctl`

```

---

### Post by macho on 2011-05-26
AHA! Earlier I was following these [instructions to build a custom bootable Ubuntu USB stick]("https://help.ubuntu.com/community/LiveCDCustomization") and I guess I missed restoring the initctl diversion. I undid it now and I think things are working.

Thanks so much for your patience in helping me figure this out.

```
$ dpkg -S `which initctl`
local diversion from: /sbin/initctl
local diversion to: /sbin/initctl.distrib
upstart: /sbin/initctl
$ ls -l `which initctl`
lrwxrwxrwx 1 root root 9 2011-04-30 20:16 /sbin/initctl -> /bin/true
$ file `which initctl`
/sbin/initctl: symbolic link to `/bin/true'
$ ls -l /sbin/initctl.distrib 
-rwxr-xr-x 1 root root 147208 2011-04-20 17:56 /sbin/initctl.distrib
$ file /sbin/initctl.distrib 
/sbin/initctl.distrib: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

---

### Post by webofunni on 2011-05-26
Glad to know that it is fixed and thanks for your support for my application :-)

---

