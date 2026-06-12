---
title: "big log files"
date: 2011-03-18
forum: General Help
---

### Post by noxified on 2011-03-18
How to delete big log files from ubuntu?
It takes all my space.:confused:

---

### Post by seawolf167 on 2011-03-18
I'd be willing to bet the logs don't take up *that *much space, you can see how much disk space they are using by typing the following command

```
sudo du -hs /var/log
```in a terminal (Applications -> Accessories -> Terminal)

---

### Post by noxified on 2011-03-18
i know about terminal,lol.
8.9G    /var/log
For my hdd,it`s pretty much.
How can i delete them?It`s safe?
syslog.1 2.3 gb
ufw.log 3.1 gb
kern.log 3.1 gb

---

### Post by r-senior on 2011-03-18
You ought to have a look at logrotate, which automates the process of archiving and compressing log files on a regular basis and deleting archives beyond a certain age. 

It's part of a standard Ubuntu install. Config files are in /etc/logrotate.d and scheduled in /etc/cron.daily.

If it is running, and I don't know why it isn't in your case, you'll have old logs compressed in /var/log but they disappear after a configurable number of days, e.g. from this machine:

```

$ ls -l /var/log/syslog*
-rw-r----- 1 syslog adm 104802 2011-03-18 18:34 /var/log/syslog
-rw-r----- 1 syslog adm  20472 2011-03-18 07:35 /var/log/syslog.1
-rw-r----- 1 syslog adm   4010 2011-03-17 07:35 /var/log/syslog.2.gz
-rw-r----- 1 syslog adm  71354 2011-03-16 01:54 /var/log/syslog.3.gz
-rw-r----- 1 syslog adm   2477 2011-03-15 07:35 /var/log/syslog.4.gz
-rw-r----- 1 syslog adm    938 2011-03-14 07:35 /var/log/syslog.5.gz
-rw-r----- 1 syslog adm   2583 2011-03-13 07:35 /var/log/syslog.6.gz
-rw-r----- 1 syslog adm   1485 2011-03-12 07:35 /var/log/syslog.7.gz

```

If you really need to free the space before you set up/re-enable logrotate, you can truncate them in place rather than delete them:

```

$ sudo truncate --size 0 <filename>

```

---

### Post by noxified on 2011-03-18
-rw-r----- 1 syslog adm  137261973 2011-03-18 20:31 /var/log/syslog
-rw-r----- 1 syslog adm 2440207166 2011-03-18 10:44 /var/log/syslog.1

How do i delete them?
And how do i set logrotate,to 2 days or smth.or one day.
Do i really need those logs?
if my system crashes(i don`t see why ) i wouldn`t know how to repair it.xD

---

### Post by r-senior on 2011-03-18
OK, you have a problem. It appears logrotate is running because you have a rotated log file in /var/log/syslog.1.

Have you looked at what's happening in those logs?

```

$ tail -f /var/log/syslog

```

Ctrl-C to stop following the log file.

I'm guessing something is just spitting out vast amounts of log information and that is your problem.

---

### Post by seawolf167 on 2011-03-18
That's a a quite bit larger than I expected for your logs - ensure you look at them because they shouldn't be that large, there is probably a problem.

I'm going to take a round-about way to get to your requested answer:

You can see what logs are being rotated by typing

```
ls -l /etc/logrotate.d
```Then switch over and edit the logrotate.config file (man page online [here]("http://manpages.ubuntu.com/manpages/lucid/man8/logrotate.8.html"))

```
gedit /etc/logrotate.conf
```And here there are 4 settings you may want to change:

*weekly *-> how often logs are rotated
*rotate # *-> how many rotated logs are kept
*compress* -> compresses logs if uncommented
*create* -> creates new logs after rotating
Being concerned about space - I would probably set the logs to rotate weekly, keep 1 old log, compress the logs, and create new ones after rotating. If you then wait 1 week (to ensure you have logs available between now and then), when the logs are rotated you can safely delete the rotated old ones.

---

### Post by noxified on 2011-03-18
-rw-r----- 1 syslog adm  137261973 2011-03-18 20:31 /var/log/syslog
-rw-r----- 1 syslog adm 2440207166 2011-03-18 10:44 /var/log/syslog.1
fabbs@fabbs-desktop:~$ tail -f /var/log/syslog
Mar 18 20:24:38 fabbs-desktop kernel: [   31.840024] vmnet1: no IPv6 routers present
Mar 18 20:24:39 fabbs-desktop kernel: [   32.564985] EXT4-fs (sda6): re-mounted. Opts: commit=0
Mar 18 20:25:35 fabbs-desktop kernel: [   88.572032] Clocksource tsc unstable (delta = -249971182 ns)
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Version 2010.8.8 external FUSE 28
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Mounted /dev/sdb1 (Read-Write, label "New Volume", NTFS 3.1)
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Global ownership and permissions enforced, configuration type 1
Mar 18 20:28:25 fabbs-desktop pulseaudio[1590]: ratelimit.c: 1 events suppressed
Mar 18 20:31:05 fabbs-desktop kernel: [  418.863125] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
^C


Do i really need those logs?
how about kernel and firewall log?

---

### Post by tgm4883 on 2011-03-18
> **noxified said:**
> -rw-r----- 1 syslog adm  137261973 2011-03-18 20:31 /var/log/syslog
-rw-r----- 1 syslog adm 2440207166 2011-03-18 10:44 /var/log/syslog.1
fabbs@fabbs-desktop:~$ tail -f /var/log/syslog
Mar 18 20:24:38 fabbs-desktop kernel: [   31.840024] vmnet1: no IPv6 routers present
Mar 18 20:24:39 fabbs-desktop kernel: [   32.564985] EXT4-fs (sda6): re-mounted. Opts: commit=0
Mar 18 20:25:35 fabbs-desktop kernel: [   88.572032] Clocksource tsc unstable (delta = -249971182 ns)
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Version 2010.8.8 external FUSE 28
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Mounted /dev/sdb1 (Read-Write, label "New Volume", NTFS 3.1)
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Mar 18 20:25:58 fabbs-desktop ntfs-3g[2151]: Global ownership and permissions enforced, configuration type 1
Mar 18 20:28:25 fabbs-desktop pulseaudio[1590]: ratelimit.c: 1 events suppressed
Mar 18 20:31:05 fabbs-desktop kernel: [  418.863125] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
^C


Do i really need those logs?
how about kernel and firewall log?

Yes you need all of those logs. As said before, the logs aren't normally that large, so if they do get that big it indicates either problem (most likely), or that you have changed some configuration incorrectly (less likely)

---

### Post by r-senior on 2011-03-18
> **noxified said:**
> Do i really need those logs?
Not absolutely essential, but they come in useful. 

You need to find out why they are getting so large in the space of a day. Seawolf expected them to be many orders of magnitude smaller and so did I.

---

### Post by noxified on 2011-03-18
how do i find out what`s happening,and what`s the problem?
and how do i fix it?):P

---

### Post by tgm4883 on 2011-03-18
> **noxified said:**
> how do i find out what`s happening,and what`s the problem?
and how do i fix it?):P

you need to read the logs and see what the error messages are

---

### Post by noxified on 2011-03-18
Mar 13 12:37:39 fabbs-desktop kernel: [ 7586.612072] usb 2-1: new low speed USB device using ohci_hcd and address 6
Mar 13 12:37:40 fabbs-desktop kernel: [ 7586.796063] usb 2-1: device descriptor read/64, error -62
Mar 13 12:37:40 fabbs-desktop kernel: [ 7587.084054] usb 2-1: device descriptor read/64, error -62
Mar 13 12:37:40 fabbs-desktop kernel: [ 7587.364054] usb 2-1: new low speed USB device using ohci_hcd and address 7
Mar 13 12:37:40 fabbs-desktop kernel: [ 7587.548051] usb 2-1: device descriptor read/64, error -62
Mar 13 12:37:41 fabbs-desktop kernel: [ 7587.832646] usb 2-1: device descriptor read/64, error -62
Mar 13 12:37:41 fabbs-desktop kernel: [ 7588.112057] usb 2-1: new low speed USB device using ohci_hcd and address 8
Mar 13 12:37:41 fabbs-desktop kernel: [ 7588.520032] usb 2-1: device not accepting address 8, error -62
Mar 13 12:37:41 fabbs-desktop kernel: [ 7588.696055] usb 2-1: new low speed USB device using ohci_hcd and address 9
Mar 13 12:37:42 fabbs-desktop kernel: [ 7589.104063] usb 2-1: device not accepting address 9, error -62
Mar 13 12:37:42 fabbs-desktop kernel: [ 7589.104097] hub 2-0:1.0: unable to enumerate USB device on port 1
Mar 13 12:43:34 fabbs-desktop kernel: [ 7941.152057] usb 2-1: new low speed USB device using ohci_hcd and address 10
Mar 13 12:43:34 fabbs-desktop kernel: [ 7941.336069] usb 2-1: device descriptor read/64, error -62
Mar 13 12:43:34 fabbs-desktop kernel: [ 7941.624059] usb 2-1: device descriptor read/64, error -62
Mar 13 12:43:35 fabbs-desktop kernel: [ 7941.904048] usb 2-1: new low speed USB device using ohci_hcd and address 11
Mar 13 12:43:35 fabbs-desktop kernel: [ 7942.088052] usb 2-1: device descriptor read/64, error -62
Mar 13 12:43:35 fabbs-desktop kernel: [ 7942.372041] usb 2-1: device descriptor read/64, error -62
Mar 13 12:43:35 fabbs-desktop kernel: [ 7942.652057] usb 2-1: new low speed USB device using ohci_hcd and address 12
Mar 13 12:43:36 fabbs-desktop kernel: [ 7943.060228] usb 2-1: device not accepting address 12, error -62
Mar 13 12:43:36 fabbs-desktop kernel: [ 7943.236080] usb 2-1: new low speed USB device using ohci_hcd and address 13
Mar 13 12:43:36 fabbs-desktop kernel: [ 7943.644040] usb 2-1: device not accepting address 13, error -62
Mar 13 12:43:36 fabbs-desktop kernel: [ 7943.644074] hub 2-0:1.0: unable to enumerate USB device on port 1
Mar 13 12:46:13 fabbs-desktop kernel: [ 8099.844054] usb 2-1: new low speed USB device using ohci_hcd and address 14
Mar 13 12:46:13 fabbs-desktop kernel: [ 8100.028049] usb 2-1: device descriptor read/64, error -62
Mar 13 12:46:13 fabbs-desktop kernel: [ 8100.316055] usb 2-1: device descriptor read/64, error -62
Mar 13 12:46:13 fabbs-desktop kernel: [ 8100.596046] usb 2-1: new low speed USB device using ohci_hcd and address 15
Mar 13 12:46:13 fabbs-desktop kernel: [ 8100.780093] usb 2-1: device descriptor read/64, error -62
Mar 13 12:46:14 fabbs-desktop kernel: [ 8101.064047] usb 2-1: device descriptor read/64, error -62
Mar 13 12:46:14 fabbs-desktop kernel: [ 8101.344045] usb 2-1: new low speed USB device using ohci_hcd and address 16
Mar 13 12:46:14 fabbs-desktop kernel: [ 8101.752035] usb 2-1: device not accepting address 16, error -62
Mar 13 12:46:15 fabbs-desktop kernel: [ 8101.928075] usb 2-1: new low speed USB device using ohci_hcd and address 17
Mar 13 12:46:15 fabbs-desktop kernel: [ 8102.336040] usb 2-1: device not accepting address 17, error -62
Mar 13 12:46:15 fabbs-desktop kernel: [ 8102.336073] hub 2-0:1.0: unable to enumerate USB device on port 1
Mar 13 12:50:13 fabbs-desktop kernel: [ 8340.268074] usb 2-1: new low speed USB device using ohci_hcd and address 18
Mar 13 12:50:13 fabbs-desktop kernel: [ 8340.452047] usb 2-1: device descriptor read/64, error -62
Mar 13 12:50:13 fabbs-desktop kernel: [ 8340.740072] usb 2-1: device descriptor read/64, error -62
Mar 13 12:50:14 fabbs-desktop kernel: [ 8341.020063] usb 2-1: new low speed USB device using ohci_hcd and address 19
Mar 13 12:50:14 fabbs-desktop kernel: [ 8341.204045] usb 2-1: device descriptor read/64, error -62
Mar 13 12:50:14 fabbs-desktop kernel: [ 8341.492073] usb 2-1: device descriptor read/64, error -62
Mar 13 12:50:14 fabbs-desktop kernel: [ 8341.772065] usb 2-1: new low speed USB device using ohci_hcd and address 20
Mar 13 12:50:15 fabbs-desktop kernel: [ 8342.180051] usb 2-1: device not accepting address 20, error -62
Mar 13 12:50:15 fabbs-desktop kernel: [ 8342.357104] usb 2-1: new low speed USB device using ohci_hcd and address 21
Mar 13 12:50:15 fabbs-desktop kernel: [ 8342.764054] usb 2-1: device not accepting address 21, error -62
Mar 13 12:50:15 fabbs-desktop kernel: [ 8342.764087] hub 2-0:1.0: unable to enumerate USB device on port 1
Mar 13 12:52:27 fabbs-desktop kernel: [ 8474.020048] usb 2-1: new low speed USB device using ohci_hcd and address 22
Mar 13 12:52:27 fabbs-desktop kernel: [ 8474.204045] usb 2-1: device descriptor read/64, error -62
Mar 13 12:52:27 fabbs-desktop kernel: [ 8474.492050] usb 2-1: device descriptor read/64, error -62
Mar 13 12:52:27 fabbs-desktop kernel: [ 8474.772074] usb 2-1: new low speed USB device using ohci_hcd and address 23
Mar 13 12:52:28 fabbs-desktop kernel: [ 8474.956054] usb 2-1: device descriptor read/64, error -62
Mar 13 12:52:28 fabbs-desktop kernel: [ 8475.240050] usb 2-1: device descriptor read/64, error -62
Mar 13 12:52:28 fabbs-desktop kernel: [ 8475.520056] usb 2-1: new low speed USB device using ohci_hcd and address 24
Mar 13 12:52:29 fabbs-desktop kernel: [ 8475.928043] usb 2-1: device not accepting address 24, error -62
Mar 13 12:52:29 fabbs-desktop kernel: [ 8476.104058] usb 2-1: new low speed USB device using ohci_hcd and address 25
Mar 13 12:52:29 fabbs-desktop kernel: [ 8476.512043] usb 2-1: device not accepting address 25, error -62
Mar 13 12:52:29 fabbs-desktop kernel: [ 8476.512076] hub 2-0:1.0: unable to enumerate USB device on port 1
Mar 13 13:21:16 fabbs-desktop kernel: [10203.088406] psmouse.c: Explorer Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Mar 13 14:51:42 fabbs-desktop kernel: [15629.004341] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Mar 13 14:57:34 fabbs-desktop kernel: [15981.475491] lo: Disabled Privacy Extensions
Mar 13 15:09:37 fabbs-desktop kernel: [16704.656620] lo: Disabled Privacy Extensions
Mar 13 15:11:53 fabbs-desktop kernel: [16840.172606] lo: Disabled Privacy Extensions
Mar 13 16:23:56 fabbs-desktop kernel: [21163.530529] audit_printk_skb: 18 callbacks suppressed
Mar 13 16:23:56 fabbs-desktop kernel: [21163.530534] type=1400 audit(1300026236.736:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=688 comm="apparmor_parser"
Mar 13 16:23:56 fabbs-desktop kernel: [21163.530956] type=1400 audit(1300026236.736:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=688 comm="apparmor_parser"
Mar 13 16:27:23 fabbs-desktop kernel: [21370.183395] /dev/vmmon[3717]: Module vmmon: registered with major=10 minor=165
Mar 13 16:27:23 fabbs-desktop kernel: [21370.183410] /dev/vmmon[3717]: Module vmmon: initialized
Mar 13 16:27:23 fabbs-desktop kernel: [21370.236627] /dev/vmci[3726]: VMCI: Driver initialized.
Mar 13 16:27:23 fabbs-desktop kernel: [21370.238270] /dev/vmci[3726]: Module vmci: registered with major=10 minor=53
Mar 13 16:27:23 fabbs-desktop kernel: [21370.238276] /dev/vmci[3726]: Module vmci: initialized
Mar 13 16:27:23 fabbs-desktop kernel: [21370.621540] /dev/vmnet: open called by PID 3769 (vmnet-bridge)
Mar 13 16:27:23 fabbs-desktop kernel: [21370.621552] /dev/vmnet: hub 0 does not exist, allocating memory.
Mar 13 16:27:23 fabbs-desktop kernel: [21370.621580] /dev/vmnet: port on hub 0 successfully opened
Mar 13 16:27:23 fabbs-desktop kernel: [21370.621599] bridge-eth0: up
Mar 13 16:27:23 fabbs-desktop kernel: [21370.621603] bridge-eth0: attached
Mar 13 16:27:25 fabbs-desktop kernel: [21371.924635] /dev/vmnet: open called by PID 3776 (vmnet-dhcpd)


this is not all,there`s much more.
What do i do?How do i fix them?Etc.I`m not a linux expert or smth.I instaled few weeks ago,and i`m learning.

---

### Post by seawolf167 on 2011-03-18
> **noxified said:**
> how do i find out what`s happening,and what`s the problem?
and how do i fix it?):P

If you open the logs (say with gedit) - note that they are huge and will be *thousands *of lines, there will almost certainly be a couple lines that repeat over and over and over (hundreds or even thousands of times). Pay attention to these lines as this is most likely a (if not *the*) problem.

If you don't understand what they are saying, post them (but not the full logs!) here so we can take a look.

---

### Post by seawolf167 on 2011-03-18
Didn't see your post before I posted my previous comment

Can you run

```
lsusb
```to list your usb devices, then find your usb device and run

```
sudo fsck /dev/sdXY
```where */dev/sdXY* is the name of the device from the first command (could be something like /dev/sda1 or /dev/hda1, etc.)

---

### Post by noxified on 2011-03-19
I tried opening those files,i waited,and when i was back my hdd had crashed.
So nevermind.I won`t try to open those files again.I`ll try to delete them.
So how do i set up those log to delete after 1 day?

---

### Post by tgm4883 on 2011-03-19
> **noxified said:**
> I tried opening those files,i waited,and when i was back my hdd had crashed.
So nevermind.I won`t try to open those files again.I`ll try to delete them.
So how do i set up those log to delete after 1 day?

Use tail to read the last 100 lines of the file

---

### Post by noxified on 2011-03-19
nevermind my hdd crashed.

---

