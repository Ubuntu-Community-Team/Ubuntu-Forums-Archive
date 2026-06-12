---
title: "How do I run commands on startup?"
date: 2011-12-31
forum: General Help
---

### Post by carlosbgois on 2011-12-31
This is something I found searching the forum and I think would help me with my issue. The problem is I don't know how to do what is said:

> If you want to use Intel card only, you can disable nvidia by running these commands at startup:

modprobe acpi_call
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

Thanks

---

### Post by Dave_L on 2011-12-31
The easiest way is to add them to /etc/rc.local, just before the "exit 0" line.  You'll need to edit that file as root.

I recommend making a backup copy of the file first. And make sure that you can boot into recovery mode and/or from a LiveCD, in case it doesn't work, and you need to restore the file.

---

### Post by carlosbgois on 2012-01-01
Many thanks, I'll try it.

---

### Post by syerges on 2012-01-01
If you don't want to mess with the startup files you could also try using this to make a file with the code and putting it in your startup folder.
gnome-desktop-item-edit --create-new ~/Desktop

---

### Post by carlosbgois on 2012-01-01
I added the exact two lines I posted before to rc.local and rebooted, but nothing has changed. 

Actually, there are two rc.local files containing different commands:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe acpi_call
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch 

exit 0
``````
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}

case "$1" in
    start)
    do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```(the first is the one I have edited).

**syerges**, thanks for your help too, I'm gonna try to do your way after I get it working.
Is there some way of choosing wheter I want the commands to execute or not when the system is starting?

---

### Post by Haneef Mubarak on 2012-01-01
If you'd like to do it manually each startup, you could hit <CTRL><ALT><F1> at startup, login as root (or just login as admin and use # sudo -s), and type in your commands.

---

