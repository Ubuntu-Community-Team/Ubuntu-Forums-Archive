---
title: "No bootlogs in 10.4/Lucid"
date: 2010-12-07
forum: General Help
---

### Post by Kristian9K on 2010-12-07
Hi,
I just installed Ubuntu 10.4 from the mini.iso. I simply can't get the bootlogs to show anything of value. In /var/log....

"boot" is empty
"boot.log" shows only six lines
"boot.0" shows about eight lines
- and I have a file called "boot~" which shows perhaps twelve lines.

This is after trying suggestions from here and launchpad. Please help if you can as there seems to be something amiss during boot and I'd like to have it sorted out.

Best,
Kristian

---

### Post by wojox on 2010-12-07
dmesg usually works.

---

### Post by Kristian9K on 2010-12-07
I know, but I need the boot log.

---

### Post by drs305 on 2010-12-07
Try this:
```
gksu gedit /etc/default/bootlogd
```
Change the value to "Yes"
> 
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

On reboot, check /var/log/boot.log

---

### Post by Kristian9K on 2010-12-07
Hi. Forgot to mention that I did that already.

---

### Post by wojox on 2010-12-07
Post boot.0 up here.

---

### Post by Kristian9K on 2010-12-07
Here it is:
__________________________

Tue Dec  7 15:48:04 2010: init: tty4 main process (558) killed by TERM signal
Tue Dec  7 15:48:04 2010: init: tty5 main process (560) killed by TERM signal
Tue Dec  7 15:48:04 2010: init: tty2 main process (564) killed by TERM signal
Tue Dec  7 15:48:04 2010: init: tty3 main process (565) killed by TERM signal
Tue Dec  7 15:48:04 2010: init: tty6 main process (567) killed by TERM signal
Tue Dec  7 15:48:04 2010: init: cron main process (572) killed by TERM signal
Tue Dec  7 15:48:04 2010: init: tty1 main process (661) killed by TERM signal
Tue Dec  7 15:48:05 2010: init: avahi-daemon main process (519) terminated with status 255
Tue Dec  7 15:48:05 2010: init: Disconnected from system bus
Tue Dec  7 15:48:07 2010: 
Tue Dec  7 14:46:19 2010: ^[[74G[ OK ]

---

### Post by Kristian9K on 2010-12-07
... and here's boot.log:
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 51827/82896 files, 243060/331520 blocks
/dev/sda6: clean, 113/155040 files, 34845/620032 blocks (check in 4 mounts)
init: ureadahead-other main process (431) terminated with status 4

 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
 * Starting boot logger bootlogd       [80G
```

 - this is the mysterious boot~:
```

Tue Dec  7 15:49:36 2010: ^[[74G[ OK ]
Tue Dec  7 15:49:37 2010: ^[[74G[ OK ]Network connection manager wicd       ^[[80G 
Tue Dec  7 15:49:45 2010: ^[[74G[ OK ]vram module       ^[[80G 
Tue Dec  7 16:28:24 2010: init: tty4 main process (550) killed by TERM signal
Tue Dec  7 16:28:24 2010: init: avahi-daemon main process (506) terminated with status 255
Tue Dec  7 16:28:24 2010: init: tty5 main process (552) killed by TERM signal
Tue Dec  7 16:28:25 2010: init: tty2 main process (556) killed by TERM signal
Tue Dec  7 16:28:25 2010: init: tty3 main process (557) killed by TERM signal
Tue Dec  7 16:28:25 2010: init: tty6 main process (560) killed by TERM signal
Tue Dec  7 16:28:25 2010: init: cron main process (571) killed by TERM signal
Tue Dec  7 16:28:25 2010: init: tty1 main process (660) killed by TERM signal
Tue Dec  7 16:28:25 2010: init: Disconnected from system bus
Tue Dec  7 16:28:25 2010:
```

---

### Post by wojox on 2010-12-07
boot.log looks like your boot log. The others look like shutdown logs. Ubuntu never had very good boot logs. I remember using dmesg  and sys logs.

I run fedora now. It's a little more detailed:

```
%G%G		Welcome to [0;34mFedora[0;39m 

Starting udev: %G[60G[[0;32m  OK  [0;39m]


Setting hostname wojox-desktop:  [60G[[0;32m  OK  [0;39m]


Setting up Logical Volume Management:   No volume groups found

[60G[[0;32m  OK  [0;39m]


Checking filesystems

_Fedora-14-i686-: clean, 79720/12214272 files, 1464996/48839936 blocks

[60G[[0;32m  OK  [0;39m]


Remounting root filesystem in read-write mode:  [60G[[0;32m  OK  [0;39m]


Mounting local filesystems:  [60G[[0;32m  OK  [0;39m]


Enabling /etc/fstab swaps:  [60G[[0;32m  OK  [0;39m]


Entering non-interactive startup

Starting portreserve: [60G[[0;32m  OK  [0;39m]


Starting system logger: [60G[[0;32m  OK  [0;39m]


Enabling ondemand cpu frequency scaling: [60G[[0;32m  OK  [0;39m]


Starting irqbalance: [60G[[0;32m  OK  [0;39m]


Starting mdmonitor: [60G[[0;32m  OK  [0;39m]


Starting system message bus: [60G[[0;32m  OK  [0;39m]


Setting network parameters... [60G[[0;32m  OK  [0;39m]


Starting NetworkManager daemon: [60G[[0;32m  OK  [0;39m]


Starting Avahi daemon... [60G[[0;32m  OK  [0;39m]


Starting cups: [60G[[0;32m  OK  [0;39m]


Mounting other filesystems:  [60G[[0;32m  OK  [0;39m]


Starting HAL daemon: [60G[[0;32m  OK  [0;39m]


Retrigger failed udev events[60G[[0;32m  OK  [0;39m]


Enabling Bluetooth devices:

Starting ntpd: [60G[[0;32m  OK  [0;39m]


Starting sendmail: [60G[[0;32m  OK  [0;39m]


Starting sm-client: [60G[[0;32m  OK  [0;39m]


Starting abrt daemon: [60G[[0;32m  OK  [0;39m]


Starting crond: [60G[[0;32m  OK  [0;39m]


Starting atd: [60G[[0;32m  OK  [0;39m]
[60G[[0;32m  OK  [0;39m]

```

---

