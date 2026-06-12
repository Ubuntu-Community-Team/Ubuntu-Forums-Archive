---
title: "dbus problem"
date: 2011-08-23
forum: General Help
---

### Post by kasans on 2011-08-23
Hello,
(sorry for my English in advance)
I was happy Ubuntu users unless some update has been installed on my system. Problem appeared when I restarted the system. I hangs on X start phase showing me something X is in low screen resolution mode blah-blah-blah... I'm able to start X though, by go to 1) safe mode in GRUB, 2) root console, 3) startx as root user or 1,2, 3) telinit 3, 4) log in as regular user, 5) startx.
While booting the system reports several process ended and being re-spawned...
Well, why I think it's dbus problem:
There are several error messages like "Failed to open connection to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused" appear when I or the system try to start something:(...
I'm a newbie in Linux, therefore I don't know to where direction should I dig...

I do appreciate any help in making my system revive and this forum is only my hope as google doesn't give any clue...

SYSTEM:
```
10.04. LTS
Linux andrey-laptop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux

sudo service dbus status
dbus start/running

ls -lah /var/run/dbus/system_bus_socket
srwxrwxrwx 1 root root 0 2011-08-23 21:03 /var/run/dbus/system_bus_socket


```I believe the following is not good)
```

sudo dbus-monitor --system
 Failed to open connection to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused
 
sudo service --status-all
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-mixer-save
 [ ? ]  anacron
 [ + ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ ? ]  console-setup
 [ ? ]  cron
 [ + ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  failsafe-x
 [ - ]  fancontrol
 [ ? ]  gdm
 [ - ]  grub-common
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  irqbalance
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ - ]  lm-sensors
 [ ? ]  module-init-tools
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  network-manager
 [ ? ]  networking
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ - ]  rsync
 [ ? ]  rsyslog
 [ - ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  speech-dispatcher
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
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
 [ + ]  winbind
 [ ? ]  wpa-ifupdown
 [ - ]  x11-common
```

---

### Post by kasans on 2011-08-23
I've archived some progress, by removing dbus pid fils and restarting dbus it seems it starts to work, but problem still exists from startup and many services don't work anyway...
```

sudo rm /var/run/dbus/pid
sudo stop dbus
sudo start dbus
sudo status dbus
dbus start/running, process 1408 #(before this string ends on comma)

ps aux | grep dbus | grep -v grep
102       1408  0.0  0.0   3248  1708 ?        Ss   00:24   0:00 dbus-daemon --system --fork
andrey    1839  0.0  0.0   3548  1016 tty1     S    00:24   0:00 /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session x-session-manager
andrey    1869  0.0  0.0   3284   356 ?        Ss   00:24   0:00 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session x-session-manager
andrey    1881  0.0  0.0   3384   776 tty1     S    00:24   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
andrey    1882  0.0  0.0   3192  1444 ?        Ss   00:24   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session

#and this is working now:
$ dbus-monitor --system
signal sender=org.freedesktop.DBus -> dest=:1.41 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.41"


```

when I try to start other service like networking:
```
$ service networking restart
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.46" (uid=1000 pid=4026 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
```
not sure if it's okay

---

### Post by kasans on 2011-08-24
Guys, any ideas?
Maybe you can suggest your check list at least, in order I could find what is not working exactly?
got boot.log by adding --debug option to GRUB

---

### Post by kasans on 2011-08-29
fixed by reintallation

---

