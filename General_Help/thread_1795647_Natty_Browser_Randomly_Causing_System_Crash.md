---
title: "Natty Browser Randomly Causing System Crash"
date: 2011-07-03
forum: General Help
---

### Post by dsx724 on 2011-07-03
Whenever I'm browsing the web on one of my natty machines, I'm subject to periodic reboots that leave nothing in the syslog.  Here's the two constants I've discovered thus far.

It only happens when I'm using a browser (plugin?).
It doesn't matter whether I'm in Chromium or Firefox.
It doesn't matter whether I use Unity or Gnome 2.
This happens every 2-3 days from what I can tell.
This problem is not power related because I've tested it with and without an UPS present.

The computer does a full reboot without any shutdown procedure.

The configuration of this computer is as follows:
Intel i3 2100
ECS H67 Dual Nic
Haupaugge Dual ATSC Tuner
MDADM RAID 10
8GB 1333MHz (MemTested)

The browser plugins are as follows:
Flash 10.3r181
VLC Multimedia Plugin (compatible Totem 2.32.0)
Windows Media Player Plug-in 10 (compatible; Totem)
DivX Web Player version 1.4.0.233
QuickTime Plug-in 7.6.6

Anybody also have this problem?  Any insight in how determining a cause?  I don't understand how an user space program without privileges can crash an entire OS without leaving a trace.

---

### Post by dino99 on 2011-07-03
nothing logged into .xsession-errors ?
are you some related ppa installed ?

---

### Post by bluebell-saar on 2011-07-03
> **dsx724 said:**
> Whenever I'm browsing the web on one of my natty machines, I'm subject to periodic reboots that leave nothing in the syslog.  Here's the two constants I've discovered thus far.

It only happens when I'm using a browser (plugin?).
It doesn't matter whether I'm in Chromium or Firefox.
It doesn't matter whether I use Unity or Gnome 2.
This happens every 2-3 days from what I can tell.
This problem is not power related because I've tested it with and without an UPS present.

The computer does a full reboot without any shutdown procedure.


I have exactly the same problem:
- Ubuntu Natty 64 Bit
- 64 Bit Flashplayer "square"
- core i5 (Sandy Bridge)
- Intel graphics

What I tried:
- Deinstalling synaptics driver (to avoid triggering Xrecord bug in xorg)
- Installing Server kernel
- Booting with noapic
- PS/2- and USB-Keyboard

Not only xorg crashes but the whole machine reboots immediately without shutting the system down normally.
Nothing helped. It happens from time to time when interacting with the mouse. Nothing to be seen in logfiles.

---

### Post by dsx724 on 2011-08-01
The OP of this thread seems to have the same issue.  [http://ubuntuforums.org/showthread.php?t=1778643](http://ubuntuforums.org/showthread.php?t=1778643)
There's no additional PPA, this is strictly a stock Ubuntu install.  None of my /var/log/ files have anything meaningful.

It literally just does a full reboot without any messages.
[IMG]http://s1.postimage.org/3x973dacz/Screenshot_5.png[/IMG]

---

