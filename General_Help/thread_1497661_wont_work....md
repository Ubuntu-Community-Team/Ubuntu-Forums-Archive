---
title: "wont work..."
date: 2010-05-30
forum: General Help
---

### Post by jstone626 on 2010-05-30
Hello, just yesterday I switched from windows to ubuntu, and I really  enjoyed it.
Tonight, however, after installing and uninstalling a lot of addons, I  rebooted it. To my surprise, the welcome screen just keeps reloading  after I enter my pass.

I did some searching, now when I press ctrl+alt+f7, here's what I get:

[...] fsck from util-linux-ng 2.17.2
udevd[401]: BUS= will be removed in a future udev version, please use  SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent  device, in /etc/udev/rules.d/40-usrp.rules:1

udevd[401]: SYSFS{}= will be removed in a future udev version, please  use ATTR{}= to match the event device, or ATTRS{}= to match a parent   device, in /etc/udev/rules.d/40-usrp.rules:1

/dev/sda5: clean, 233213/567840 files, 1750400/2269173 blocks
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable" usr.bin.firefox

* Setting sensors limits
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
* gammu-smsd not yet configured, please edit /etc/gammu-smsdrc
* Not starting internet superserver: no services enabled.
* Starting Postfix Mail Transport Agent postfix


I should note that I still have Windows 7 running on the machine on a  different partition, and that this is a 64bit Toshiba A500.

please help me!

Johnny

---

### Post by Brandon Williams on 2010-06-01
Try this: press Ctrl+F1 to get to a console login prompt and then enter your login credentials. From there, view the X environment error log by running 'less ~/.xession-errors'. Are there any important looking error message in that file, post them here if the problem is not immediately evident.

---

