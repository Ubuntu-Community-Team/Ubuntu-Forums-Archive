---
title: "Trouble mounting USB hdds during boot"
date: 2006-03-12
forum: General Help
---

### Post by droazen on 2006-03-12
I have two external USB hard drives connected to my laptop via a Cardbus USB 2.0 adapter (since the laptop has no native USB 2.0 ports). The drives aren't recognized during boot until the hotplug system loads. My problem is that the script that mounts all drives runs BEFORE hotplug during bootup, and as a result the drives fail to be mounted. This isn't a huge problem since I just mount them manually after every boot, but I'd really like to find a way to either:

1. Change the order in which the rc?.d scripts run during boot so that hotplug is loaded before drives are mounted (I don't know if this is such a great idea haha - but it'd be good to know how to do it anyway if it's do-able)

2. Make a script with a couple mount commands and have it run at the end of the boot process (but before the GUI loads)

Any help doing either of these two things is much appreciated!

---

### Post by chuckyp on 2006-03-13
1.  You can play around with update-rc.d and see if you can change the way processes are loaded.

2.  You can add your script to the rc.local and it would run after all other procs.

---

### Post by dcstar on 2006-03-13
[QUOTE=droazen]
......
2. Make a script with a couple mount commands and have it run at the end of the boot process (but before the GUI loads)

Any help doing either of these two things is much appreciated![/QUOTE]
I have the following as mountudf (in /etc/init.d, permissions 755, owner+group root) and linked from /etc/rc2.d as S99mountudf:

```
#! /bin/sh
#
# mountudf	Mount UDF CD/DWD RW (if already in the drive) on machine startup.
#
# Version:      1.0 07-12-2005 David Clayton
#

PATH=/sbin:/bin:/usr/sbin:/usr/bin

. /lib/lsb/init-functions

log_begin_msg "Mounting UDF RW ..."
mount /media/cdvdrw
log_end_msg $?

: exit 0
```
The log messages are just for my own use, basically make the appropriate changes to mount your own stuff, and it should run late in the process after you login.

And if you want your USB drives to mount as the same names (no matter what you do), have a look at:

[http://ubuntuforums.org/showthread.php?t=139535](http://ubuntuforums.org/showthread.php?t=139535)

---

### Post by droazen on 2006-03-13
Thanks for the help guys!  Since changing the order of the rc?.d scripts seemed a bit risky, I ended up writing a little mounting script and putting it in /etc/rc.boot. The /etc/inid.d/rcS script auto-runs all the scripts in that dir after finishing the rcS.d scripts but before the runlevel 2 scripts, which is late enough in the boot process for my purposes. Though I like your way of putting a S99* link in rc2.d, which pretty much guarantees it's the last thing run.

Also thanks for the tip about getting usb drives to always mount at the same point - I didn't know you could use disk labels in /etc/fstab. Nice! :)

---

