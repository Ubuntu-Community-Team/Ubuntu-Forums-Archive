---
title: "kernel.softlockup_panic"
date: 2011-06-24
forum: General Help
---

### Post by ajvok on 2011-06-24
edit /etc/sysctl.conf
add
kernel.softlockup_panic = 1
then
sysctl -p
get
error: "kernel.softlockup_panic" is an unknown key

Also:
ls: cannot access /proc/sys/kernel/softlockup_panic: No such file or directory

How do I set softlockup_panic to be on?

Thanks for any help.

---

### Post by ajvok on 2011-06-24
[FONT=Verdana][SIZE=2]Although "kernel.softlockup_panic" is an unknown key I can get the result I want by:

[/SIZE][/FONT][FONT=Verdana][SIZE=2]1. Install watchdog package
2. /etc/modules: add softdog
3. remove softdog from /etc/modprobe.d/blacklist-watchdog.conf
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
Seems to do the trick.[/SIZE][/FONT][SIZE=2] Now soft lockups cause a reboot.[/SIZE]

---

