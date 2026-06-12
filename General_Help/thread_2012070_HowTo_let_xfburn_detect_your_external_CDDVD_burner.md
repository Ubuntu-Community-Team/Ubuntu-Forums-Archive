---
title: "HowTo let xfburn detect your external CD/DVD burner"
date: 2012-06-28
forum: General Help
---

### Post by scotty64 on 2012-06-28
I had the problem that xfburn was unable to detect my external USB CD/DVD burner. The problem lies in UDEV wrongly identifying the device with ID_TYPE=floppy. See this bug: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg971826.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg971826.html)
Luckily the problem can be solved with an additional UDEV rule:

1. sudo nano /etc/udev/rules.d/70-persistent-cd.rules

2. There should be a block of rules for your external writer already. These rules automatically create symlinks in /dev. Now add another line like this:

SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="xxxxxxx", ENV{ID_TYPE}="cd", ENV{GENERATED}="1"

The trick is ENV{ID_TYPE}="cd" what tweaks the devices identification.
Do not forget to replace ENV{ID_SERIAL}=="xxxxxxx" with your devices proper serial (check the other rules in the block).

3. Save the file (Ctrl.-x), unplug the device and plug it in again.

4. (re)start xfburn and the device should be there.

---

