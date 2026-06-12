---
title: "Warning: Fake start-stop-daemon called, doing nothing"
date: 2009-12-19
forum: General Help
---

### Post by at0m1sk on 2009-12-19
I updated Ubuntu 9.10 today on my desktop and almost all services will not auto start, I googled around find that apt-get install dpkg --reinstall was suppose to fix it but no dice.  I found this was the issue by looking into my bootstrap log and found this:

```
Warning: Fake start-stop-daemon called, doing nothing
```anyone experience this issue after update that could help me out?

P.S. I can start all my services with /etc/init.d/* start

---

### Post by Sin@Sin-Sacrifice on 2009-12-19
```
apt-get install dpkg --reinstall
```

---

### Post by at0m1sk on 2009-12-19
tried no dice : (

_______________________________________

what is happening in essence is that anything in /etc/init.d/ is not being started on startup, does that better describe the issue?

---

### Post by arrange on 2009-12-19
What's the output of```
ls -l /sbin/start-stop-daemon*
```? (i.e., is there the REAL script left?)

---

### Post by at0m1sk on 2009-12-19
```
$ ls -l /sbin/start-stop-daemon*
-rwxr-xr-x 1 root root 26772 2009-09-20 03:23 /sbin/start-stop-daemon
-rwxr-xr-x 1 root root 26772 2009-12-19 12:00 /sbin/start-stop-daemon.FAKE

```

i was was trying a fix and made a .FAKE but no .REAL

---

### Post by arrange on 2009-12-19
Have you tried to install *ltsp* or *xen*?```
dpkg -l | grep -E 'xen|ltsp'
```

---

### Post by at0m1sk on 2009-12-19
No, I have not, what are those?

---

### Post by arrange on 2009-12-19
These use the fake daemon and could have given you the error message.

So when you reboot, you find yourself in a shell with no *gdm*, *cron* etc running? What's the output of ```
initctl list | sort
```then?

---

### Post by at0m1sk on 2009-12-19
I get into ubuntu 9.10 100% w/ none of my daemons in /etc/init.d started automatically and i have to manually issue a "start" to them

```
$ initctl list | sort
acpid stop/waiting
anacron stop/waiting
apport stop/waiting
atd stop/waiting
avahi-daemon start/running, process 825
control-alt-delete stop/waiting
cron stop/waiting
dbus start/running, process 815
dmesg stop/waiting
failsafe-x stop/waiting
gdm start/running, process 1052
hal start/running, process 823
hostname stop/waiting
hwclock-save stop/waiting
hwclock stop/waiting
module-init-tools stop/waiting
mountall-net stop/waiting
mountall-reboot stop/waiting
mountall-shell stop/waiting
mountall stop/waiting
mythtv-backend stop/waiting
networking stop/waiting
network-interface stop/waiting
network-manager start/running, process 824
procps stop/waiting
rcS stop/waiting
rc stop/waiting
rc-sysinit stop/waiting
rsyslog-kmsg start/running, process 811
rsyslog start/running, process 813
tty1 stop/waiting
tty2 stop/waiting
tty3 stop/waiting
tty4 stop/waiting
tty5 stop/waiting
tty6 stop/waiting
udev-finish stop/waiting
udevmonitor stop/waiting
udev start/running, process 442
udevtrigger stop/waiting
ufw start/running
upstart-udev-bridge start/running, process 440
ureadahead-other stop/waiting
ureadahead stop/waiting
usplash stop/waiting


```this is the service --status-all list
```

$ service --status-all
 [ - ]  NetworkManager.dpkg-backup
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-utils
 [ + ]  alsasound
 [ ? ]  amavis
 [ ? ]  anacron
 [ - ]  apache2
 [ ? ]  apmd
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ - ]  bind9
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ - ]  clamav-daemon
 [ - ]  clamav-freshclam
 [ ? ]  console-setup
 [ ? ]  courier-authdaemon
 [ ? ]  courier-imap
 [ ? ]  courier-imap-ssl
 [ ? ]  cron
 [ - ]  cups
 [ ? ]  dbus
 [ - ]  dkms_autoinstaller
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ - ]  dovecot
 [ ? ]  failsafe-x
 [ ? ]  fancontrol
 [ ? ]  gdm
 [ - ]  grub-common
 [ ? ]  hal
 [ ? ]  hddtemp
 [ ? ]  hotkey-setup
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  hwclock.sh.dpkg-obsolete
 [ - ]  kerneloops
 [ ? ]  keyboard-setup
 [ ? ]  killprocs
 [ - ]  klogd
 [ - ]  laptop-mode
 [ ? ]  linux-restricted-modules-common
 [ ? ]  lm-sensors
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  mysql-ndb
 [ ? ]  mysql-ndb-mgm
 [ - ]  nagios
 [ - ]  nagios3
 [ ? ]  network-manager
 [ ? ]  networking
 [ - ]  ntp
 [ ? ]  ondemand
 [ ? ]  openbsd-inetd
 [ ? ]  openvpn
 [ ? ]  pcmciautils
 [ ? ]  policykit
 [ - ]  postfix
 [ ? ]  postgrey
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  proftpd
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ ? ]  readahead
 [ ? ]  readahead-desktop
 [ - ]  rsync
 [ ? ]  rsyslog
 [ ? ]  rsyslog-kmsg
 [ - ]  samba
 [ - ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ - ]  snmpd
 [ ? ]  snmptrapfmt
 [ ? ]  spamassassin
 [ ? ]  speech-dispatcher
 [ - ]  ssh
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  stop-readahead
 [ - ]  sysklogd
 [ - ]  sysstat
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  usplash
 [ ? ]  ventrilo
 [ ? ]  virtualbox-ose
 [ - ]  winbind
 [ ? ]  wpa-ifupdown
 [ - ]  x11-common
 [ - ]  xinetd

```

here is the sysv-rc-conf list(if it helps)

```

$ sysv-rc-conf --list
acpi-support 1:off    2:on    3:on    4:on    5:on
acpid        2:on    3:on    4:on    5:on
alsa-utils   0:off    6:off
alsasound   
amavis       0:off    1:off    2:on    3:on    4:on    5:on    6:off
anacron     
apache2      0:off    1:off    2:on    3:on    4:on    5:on    6:off
apmd         1:off    2:off    3:off    4:off    5:off    S:on
apparmor     S:on
apport      
atd         
avahi-daemon
bind9        0:off    1:off    2:on    3:on    4:on    5:on    6:off
binfmt-suppo 2:on    3:on    4:on    5:on
bluetooth    0:off    1:off    2:off    3:off    4:off    5:off    6:off    S:off
bootlogd    
brltty       S:off
clamav-daemo 0:off    1:off    2:on    3:on    4:on    5:on    6:off
clamav-fresh 0:off    1:off    2:on    3:on    4:on    5:on    6:off
console-setu S:on
courier-auth 0:off    1:off    2:on    3:on    4:on    5:on    6:off
courier-imap 0:off    1:off    2:on    3:on    4:on    5:on    6:off
courier-imap 0:off    1:off    2:on    3:on    4:on    5:on    6:off
cron         2:on    3:on    4:on    5:on
cups         1:off    2:on    3:on    4:on    5:on
dbus         2:on    3:on    4:on    5:on
dkms_autoins 2:on    3:on    4:on    5:on
dmesg       
dns-clean    1:off    2:off    3:off    4:off    5:off
dovecot      1:off    2:off    3:off    4:off    5:off
failsafe-x  
fancontrol   0:off    1:off    2:on    3:on    4:on    5:on    6:off
gdm         
grub-common  2:on    3:on    4:on    5:on
hal         
halt         0:on
hddtemp      0:off    1:off    2:on    3:on    4:on    5:on    6:off
hotkey-setup 1:off    2:off    3:off    4:off    5:off    S:off
hwclock     
hwclock-save
kerneloops   0:off    1:off    2:on    3:on    4:on    5:on    6:off
keyboard-set S:on
killprocs    1:on
klogd        1:off    2:on    3:on    4:on    5:on
laptop-mode  0:off    1:off    2:off    3:off    4:off    5:off    6:off    S:off
linux-restri 0:on    6:on    S:on
lm-sensors   S:on
module-init-
mysql        0:off    1:off    2:on    3:on    4:on    5:on    6:off
mysql-ndb    0:off    1:off    2:on    3:on    4:on    5:on    6:off
mysql-ndb-mg 0:off    1:off    2:on    3:on    4:on    5:on    6:off
nagios       S:on
nagios3      0:off    1:off    2:off    3:off    4:off    5:off    6:off
network-mana
networking   0:on    6:on
ntp          1:off    2:on    3:on    4:on    5:on
ondemand     2:on    3:on    4:on    5:on
openbsd-inet 0:off    1:off    2:on    3:on    4:on    5:on    6:off
openvpn      0:off    1:off    2:on    3:on    4:on    5:on    6:off
pcmciautils  S:off
policykit    1:off    2:on    3:on    4:on    5:on
postfix      0:off    1:off    2:on    3:on    4:on    5:on    6:off
postgrey     0:off    1:off    2:on    3:on    4:on    5:on    6:off
pppd-dns     1:off    2:off    3:off    4:off    5:off    S:off
procps      
proftpd      0:off    1:off    2:on    3:on    4:on    5:on    6:off
pulseaudio   1:off    2:on    3:on    4:on    5:on
rc.local     2:on    3:on    4:on    5:on
readahead    S:on
readahead-de S:on
reboot       6:on
rsync        1:off    2:on    3:on    4:on    5:on
rsyslog     
rsyslog-kmsg
samba        0:off    1:off    2:on    3:on    4:on    5:on    6:off
saned        1:off    2:on    3:on    4:on    5:on
screen-clean 6:on    S:on
sendsigs     0:on    6:on
single       1:on
snmpd        1:off    2:on    3:on    4:on    5:on
snmptrapfmt  0:off    1:off    2:on    3:on    4:on    5:on    6:off
spamassassin 0:off    1:off    2:on    3:on    4:on    5:on    6:off
speech-dispa 1:off    2:on    3:on    4:on    5:on
ssh          1:off    2:on    3:on    4:on    5:on
stop-bootlog
stop-bootlog
stop-readahe 2:on    3:on    4:on    5:on
sysklogd     1:off    2:on    3:on    4:on    5:on
sysstat      1:off    2:on    3:on    4:on    5:on
udev         S:on
udev-finish 
udevmonitor 
udevtrigger 
ufw         
umountfs     0:on    6:on
umountroot   0:on    6:on
unattended-u 0:on    6:on
urandom      0:on    6:on    S:on
usplash     
ventrilo     0:off    1:off    2:on    3:on    4:on    5:on    6:off
virtualbox-o 0:off    1:off    2:on    3:on    4:on    5:on    6:off
winbind      0:off    1:off    2:on    3:on    4:on    5:on    6:off
wpa-ifupdown 0:off    6:off    S:off
x11-common   S:on
xinetd       0:off    1:off    2:on    3:on    4:on    5:on    6:of

```

---

### Post by arrange on 2009-12-19
Sorry, doesn't make sense to me. If no daemons are running, you can't boot into 9.10. The outputs are after a fresh reboot?

Maybe you mean scripts in */etc/rc2.d*, not */etc/init.d*. That would mean that only *cups*, *pulseaudio*, *rc.local* etc are not working. Is that true?

---

### Post by at0m1sk on 2009-12-19
cups,samba,ssh,proftpd,postfix,apache2,bind9,etc all of them need to be manually started by me from terminal.  I am new to linux so i can't exactly tell u whats happening but this is my issue.  I updated ubuntu, rebooted, and all of these daemons that i listed must be manually started =/.  Essentially all "server" mode scripts that i typically launch with "/etc/init.d/apache2 start" for example require that exact command to start and are not started on boot.

---

### Post by at0m1sk on 2009-12-19
bump...already saw 1 other post about this, interested to see if anyone else has this issue and any solution to it, it is very bothersome.

---

### Post by Kieron on 2009-12-20
> **arrange said:**
> Sorry, doesn't make sense to me. If no daemons are running, you can't boot into 9.10. The outputs are after a fresh reboot?

Maybe you mean scripts in */etc/rc2.d*, not */etc/init.d*. That would mean that only *cups*, *pulseaudio*, *rc.local* etc are not working. Is that true?
I'm having the exact same problem starting SAMBA, I've tried everything above and nothing has worked. And anything that outputted, mine was almost identicle to at0m1sk's.

Anyone? :(

---

### Post by john newbuntu on 2009-12-20
I am not having this problem.  However, from reading the debian forum it appears to be a problem with an installation/update gone bad.  So, logically, the first place to start looking at would be the logs at /var/log/dpkg.log (or maybe the dpkg.log.1 etc).  See if you can spot anything out of the ordinary.  Also look at /var/log/apt/term.log.

---

### Post by at0m1sk on 2009-12-20
i noticed the first thing that was updated was upstart here is some of the log stating it's progress, again 1st thing that started the update.

```

2009-12-19 09:39:51 startup archives unpack
2009-12-19 09:40:10 upgrade upstart 0.6.3-10 0.6.3-11
2009-12-19 09:40:10 status half-configured upstart 0.6.3-10
2009-12-19 09:40:10 status unpacked upstart 0.6.3-10
2009-12-19 09:40:10 status half-installed upstart 0.6.3-10
2009-12-19 09:40:10 status triggers-pending man-db 2.5.6-2
2009-12-19 09:40:10 status half-installed upstart 0.6.3-10
2009-12-19 09:40:11 status triggers-pending ureadahead 0.90.3-2
2009-12-19 09:40:11 status half-installed upstart 0.6.3-10
2009-12-19 09:40:11 status half-installed upstart 0.6.3-10
2009-12-19 09:40:11 status unpacked upstart 0.6.3-11
2009-12-19 09:40:11 status unpacked upstart 0.6.3-11
2009-12-19 09:40:11 trigproc man-db 2.5.6-2 2.5.6-2
2009-12-19 09:40:11 status half-configured man-db 2.5.6-2
2009-12-19 09:40:12 status installed man-db 2.5.6-2
2009-12-19 09:40:12 trigproc ureadahead 0.90.3-2 0.90.3-2
2009-12-19 09:40:12 status half-configured ureadahead 0.90.3-2
2009-12-19 09:40:12 status installed ureadahead 0.90.3-2
2009-12-19 09:40:13 startup packages configure
2009-12-19 09:40:13 configure upstart 0.6.3-11 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status unpacked upstart 0.6.3-11
2009-12-19 09:40:13 status half-configured upstart 0.6.3-11
2009-12-19 09:40:13 status installed upstart 0.6.3-11

```

---

### Post by arrange on 2009-12-20
Have a look at this
[http://ubuntuforums.org/showthread.php?t=1305226](http://ubuntuforums.org/showthread.php?t=1305226)

Is it the same problem?

---

### Post by at0m1sk on 2009-12-20
upstart 0.6.3-11 was the issue, reverted to 0.6.3-10 and everything is back to normal

tyvm for the suggestions to check the THAT log ;)

---

### Post by DataMatrix on 2010-07-15
Well, the problem seems to be back again in 10.04.
I've edited /etc/init/rc-sysinit.conf like this:
```
sudo mcedit /etc/init/rc-sysinit.conf
```
on line 8 instead of
```
start on filesystem and net-device-up IFACE=lo
stop on runlevel

```
I now have
```
# start on filesystem and net-device-up IFACE=lo
start on filesystem
stop on runlevel

```
and now apache starts. But what about mysql?
```
user@server:~$ sudo service mysql start

Warning: Fake initctl called, doing nothing.
user@server:/sbin$ ls -l | grep initctl
-rwxr-xr-x 1 root root       84 2010-06-09 12:32 initctl
-rwxr-xr-x 1 root root   104428 2010-04-01 22:35 initctl.REAL

```
the fix:
```
sudo mv /sbin/initctl /sbin/initctl.FAKE
sudo ln -s /sbin/initctl.REAL /sbin/initctl

```

PS: I have to say that this system had an unclean install, e.g. it crashed at about 99% and there where many problems on the system after that, this is just one of them.

---

