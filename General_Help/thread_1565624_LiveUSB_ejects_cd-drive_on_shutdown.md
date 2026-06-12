---
title: "LiveUSB ejects cd-drive on shutdown"
date: 2010-09-01
forum: General Help
---

### Post by M8R-yap4c51 on 2010-09-01
Hello, I have created a liveUSB according to:

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

I have my reasons for using this method - I change iso's every day, so I will not perform an installation on the usb stick.

I am also using the "TORAM=yes" boot parameter in grub (grub is on the LiveUSB stick).

Anyway, after creating the LiveUSB of Ubuntu 10.04.1 64bit, whenever I shutdown the computer the CD-drive ejects. How can I stop this?

I have tried adding the noeject noprompt --- parameters, but to no change.

-------
Edit:

My grub.cfg looks like this:
menuentry "Ubuntu 10.04.1 x64" {
 loopback loop /boot/iso/ubuntu-10.04.1-desktop-amd64.iso 
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04.1-desktop-amd64.iso noeject noprompt TORAM=yes --
 initrd (loop)/casper/initrd.lz
}

My exact boot procedure is like this:
1) Computer is shutdown (it is a laptop).
2) I insert USB stick into USB port.
3) I start computer.
4) Computer is set to boot from USB.
5) I am presented with grub2 menu.
6) I choose the only option (shown above).
7) It boots the system.
8) I open terminal.
9) sudo umount -l /dev/sdx1
10) I do the above command to be able to remove the USB stick, since it is no longer necessary due to the TORAM=yes parameter.
11) I remove the usb stick.
12) I shutdown computer.
13) While computer is shutting down, the cd-drive ejects.

---

### Post by C.S.Cameron on 2010-09-01
Have you tried changing the order of:
noeject noprompt TORAM=yes
to say: 
TORAM=yes noeject noprompt

---

### Post by M8R-yap4c51 on 2010-09-01
Alternatively, how would I go about disabling the CD-drive? If I disable the CD-drive before shutting down the system, then it might not eject.

Alternatively alternatively, if there are no expert users on these forums, can you point me in the correct direction? Since ubuntu is based on Debian, would I be better of asking in Debian forums? Or are there any expert forums around?

---

### Post by M8R-yap4c51 on 2010-09-01
> **C.S.Cameron said:**
> Have you tried changing the order of:
noeject noprompt TORAM=yes
to say: 
TORAM=yes noeject noprompt

Hmm, I did not think it would matter (I did not read anywhere that it would). I will give it a try right now.

---------
Edit:
I tested all permutations of those boot options and no change occured.

---

### Post by dcstar on 2010-09-02
Ok, looking at a Live USB I find that this /etc/init.d script does the actual CD eject:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          casper
# Required-Start:    $syslog
# Required-Stop:
# Should-Start:      $local_fs
# Should-Stop:       halt reboot
# X-Stop-After:      umountroot
# Default-Start:
# Default-Stop:      0 6
# Short-Description: Casper init script
# Description:       Resyncs snapshots, evantually caches files in order
#                    to let remove the media.
### END INIT INFO

# Author: Tollef Fog Heen <tfheen@canonical.com>
#         Marco Amadori <marco.amadori@gmail.com>
#
PATH=/usr/sbin:/usr/bin:/sbin:/bin
NAME=casper
SCRIPTNAME=/etc/init.d/${NAME}
DO_SNAPSHOT=/sbin/${NAME}-snapshot

# Exit if system was not booted by casper
grep -qs boot=casper /proc/cmdline || exit 0

# Exit if the system was booted from an ISO image rather than a physical CD
grep -qs find_iso= /proc/cmdline && exit 0

# Read configuration variable file if it is present
[ -r /etc/$NAME.conf ] && . /etc/$NAME.conf

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Try to cache everything we're likely to need after ejecting.  This
# is fragile and simple-minded, but our options are limited.
cache_path() {
    path="$1"

    if [ -d "$path" ]; then
        find "$path" -type f | xargs cat > /dev/null 2>&1
    elif [ -f "$path" ]; then
        if [ -x "$path" ]; then
            if file "$path" | grep -q 'dynamically linked'; then
                for lib in $(ldd "$path" | awk '{ print $3 }'); do
                    cache_path "$lib"
                done
            fi
        fi
        cat "$path" >/dev/null 2>&1
    fi
}

do_stop ()
{
    if [ ! -z "${ROOTSNAP}" ]; then
        $DO_SNAPSHOT --resync-string="${ROOTSNAP}"
    fi

    if [ ! -z "${HOMESNAP}" ]; then
        $DO_SNAPSHOT --resync-string="${HOMESNAP}"
    fi

**    # check for netboot**
    if [ ! -z "${NETBOOT}" ] || **grep -qs netboot /proc/cmdline** || grep -qsi root=/dev/nfs /proc/cmdline  || grep -qsi root=/dev/cifs /proc/cmdline ; then
        return 0
    fi

    # Don't prompt to eject the SD card on Babbage board, where we reuse it
    # as a quasi-boot-floppy. Technically this uses a bit of ubiquity
    # (archdetect), but since this is mostly only relevant for
    # installations, who cares ...
    if type archdetect >/dev/null 2>&1; then
	subarch="$(archdetect)"
	case $subarch in
	    arm*/imx51)
		return 0
		;;
	esac
    fi

    prompt=1
    if grep -qs noprompt /proc/cmdline; then
	prompt=
    fi

    for path in $(which halt) $(which reboot) /etc/rc?.d /etc/default $(which stty) /bin/plymouth /sbin/usplash_write; do
        cache_path "$path"
    done

    eject -p -m /cdrom >/dev/null 2>&1

    [ "$prompt" ] || return 0

    # XXX - i18n
    MSG="Please remove the disc and close the tray (if any) then press ENTER: "

    if [ -x /bin/plymouth ] && plymouth --ping; then
        plymouth message --text="$MSG"
        plymouth watch-keystroke > /dev/null
    else
        stty sane < /dev/console

        echo $MSG > /dev/console
        if [ -x /sbin/usplash_write ]; then
            /sbin/usplash_write "TIMEOUT 86400"
            /sbin/usplash_write "TEXT-URGENT Please remove the disc, close the tray (if any)"
            /sbin/usplash_write "TEXT-URGENT and press ENTER to continue"
        fi
        read x < /dev/console
    fi
}

case "$1" in
    restart|reload|force-reload|status)
        [ "$VERBOSE" != no ] && log_end_msg 0
        ;;
    # We normally run on start; stop is just for backwards compatibility.
    start|stop)
        log_begin_msg "${NAME} is resyncing snapshots and caching reboot files..."
        do_stop
        case "$?" in
            0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
            2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
    *)
        log_success_msg "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac
```

You can see the tests done for either command line strings or for architecture types, you may have to somehow munge something to avoid the eject code.

I would try adding the string "netboott" (deliberately misspelt) to the command line in the hope that it triggers the exit before the eject command without actually trying to do a netboot.

---

### Post by M8R-yap4c51 on 2010-09-02
Thank you very much, I will try it and report back.

---

### Post by M8R-yap4c51 on 2010-09-04
Ok, I have not been able to successfully get it to work.

In that case, how can I uninstall the cdrom from the system, so that the system does not try to eject it?

---

### Post by M8R-yap4c51 on 2010-09-10
anyone?

---

### Post by M8R-yap4c51 on 2010-09-22
bump

---

### Post by syswalla on 2010-09-29
I've been attempting to do the same thing for a 10.04 LiveCD generated by Remastersys. I've had success with the following on a VM, laptop and desktop. Not exactly extensive testing but so far so good. If this works for you be sure to make a backup file as an update may wipe out your changes.

Edit /etc/rc0.d/S89casper and comment out, add or modify the following lines as noted:
#    eject -p -m /cdrom >/dev/null 2>&1

#    [ "$prompt" ] || return 0
## Add the following line:
     return 0

#     XXX - i18n
#    MSG="Please remove the disc and close the tray (if any) then press ENTER: "

Modify the following line 
from
  /sbin/usplash_write "TIMEOUT 86400"
to
  /sbin/usplash_write "TIMEOUT 0"

---

