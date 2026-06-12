---
title: "Newbie needs help with bluez problem."
date: 2009-07-06
forum: General Help
---

### Post by Sleestax on 2009-07-06
Hello,

I am exactly 1 day into my first foray into Ubuntu and I am having a problem trying to setup Ubuntu to work with my HTC-8900 phone in PAN.

I have followed the directions in this link:
[http://ubuntuforums.org/showthread.php?t=598890](http://ubuntuforums.org/showthread.php?t=598890)

But when I open my /etc/default/bluetooth file, there is no variable called "PAND_ENABLED=0" or anything else really. This is the entirety of my file:

> # Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=1
HID2HCI_UNDO=1In the process of trying to get things to work, I have downloaded, configured and ran the make and make install for the latest bluez-utils, but that didn't help anything. 

I also checked my /etc/init.d/bluetooth and, again, there is nothing in there about PAN. I am going to paste the contents of that file as well:

> #! /bin/sh
### BEGIN INIT INFO
# Provides: bluetooth
# Required-Start:    $local_fs $syslog $remote_fs dbus
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start bluetooth daemons
### END INIT INFO
#
# bluez    Bluetooth subsystem starting and stopping
#
# originally from bluez's scripts/bluetooth.init
#
# Edd Dumbill <ejad@debian.org>
# LSB 3.0 compilance and enhancements by Filippo Giunchedi <filippo@debian.org>
#
# Updated for bluez 4.7 by Mario Limonciello <mario_limonciello@dell.com>
#
# startup control over dund and pand can be changed by editing
# /etc/default/bluetooth

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC=bluetooth

DAEMON=/usr/sbin/bluetoothd
HCIATTACH=/usr/sbin/hciattach

HID2HCI=/usr/sbin/hid2hci
HID2HCI_ENABLED=1
HID2HCI_UNDO=1

UART_CONF=/etc/bluetooth/uart

RFCOMM=/usr/bin/rfcomm
RFCOMM_NAME=rfcomm
RFCOMM_CONF=/etc/bluetooth/rfcomm.conf
SDPTOOL=/usr/bin/sdptool

test -f /etc/default/bluetooth && . /etc/default/bluetooth
test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions

set -e

run_sdptool()
{
    test -x $SDPTOOL || return 1

    if ! test -z "$SDPTOOL_OPTIONS" ; then
        oldifs="$IFS"
        IFS=";"
        for o in $SDPTOOL_OPTIONS ; do
            #echo "execing $SDPTOOL $o"
            IFS=" "
            if [ "$VERBOSE" != "no" ]; then
                $SDPTOOL $o
            else
                $SDPTOOL $o >/dev/null 2>&1
            fi
        done
        IFS="$oldifs"
    fi

}

enable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_progress_msg "hid_devices"
               $HID2HCI --tohci
       else
               $HID2HCI --tohci >/dev/null 2>&1
       fi
}

disable_hci_input()
{
       if [ "$VERBOSE" != no ]; then
               log_progress_msg "hid_devices"
               $HID2HCI --tohid
       else
               $HID2HCI --tohid >/dev/null 2>&1
       fi
}

start_uarts()
{
    [ -f $HCIATTACH ] && [ -f $UART_CONF ] || return
    grep -v '^#' $UART_CONF | while read i; do
               if [ "$VERBOSE" != no ]; then
                       $HCIATTACH $i
               else
                       $HCIATTACH $i >/dev/null 2>&1
               fi
    done
}

stop_uarts()
{
    killall hciattach > /dev/null 2>&1 || true
}

start_rfcomm()
{
    if [ -x $RFCOMM ] && [ -f $RFCOMM_CONF ] ; then
        # rfcomm must always succeed for now: users
        # may not yet have an rfcomm-enabled kernel
                if [ "$VERBOSE" != no ]; then
                       log_progress_msg "rfcomm"
                       $RFCOMM -f $RFCOMM_CONF bind all || true
                else
                       $RFCOMM -f $RFCOMM_CONF bind all >/dev/null 2>&1 || true
                fi
    fi
}

stop_rfcomm()
{
    if [ -x $RFCOMM ] ; then
               if [ "$VERBOSE" != no ]; then
                       log_progress_msg "rfcomm"
                       $RFCOMM unbind all || true
               else
                       $RFCOMM unbind all >/dev/null 2>&1 || true
               fi
    fi
}

restart_rfcomm()
{
    if [ -x $RFCOMM ] && [ -f $RFCOMM_CONF ] ; then
               if [ "$VERBOSE" != no ]; then
                       log_progress_msg  "rfcomm"
                       $RFCOMM unbind all || true
                       $RFCOMM -f $RFCOMM_CONF bind all || true
               else
                       $RFCOMM unbind all >/dev/null 2>&1|| true
                       $RFCOMM -f $RFCOMM_CONF bind all >/dev/null 2>&1 || true
               fi
    fi
}

case "$1" in
  start)
    log_daemon_msg "Starting $DESC"

    if test "$BLUETOOTH_ENABLED" = "0"; then
        log_progress_msg "disabled. see /etc/default/bluetooth"
        log_end_msg 0
        exit 0
    fi

    start-stop-daemon --start --quiet --exec $DAEMON || true
    log_progress_msg "bluetoothd"

    run_sdptool || true

    start_uarts || true

    if test "$HID2HCI_ENABLED" = "1"; then
        enable_hci_input || true
    fi
    start_rfcomm || true
    log_end_msg 0
    ;;
  stop)
    log_daemon_msg "Stopping $DESC"
    if test "$BLUETOOTH_ENABLED" = "0"; then
        log_progress_msg "disabled."
        log_end_msg 0
        exit 0
    fi
    stop_rfcomm || true
    if test "$HID2HCI_UNDO" = "1"; then
        disable_hci_input || true
    fi
    start-stop-daemon --stop --quiet --exec $DAEMON || true
    log_progress_msg "bluetoothd"
    stop_uarts || true
    log_end_msg 0
    ;;
  restart|force-reload)
    $0 stop
    $0 start
    ;;
  status)
    status_of_proc "$DAEMON" "$DESC" && exit 0 || exit $?
    ;;
  *)
    N=/etc/init.d/bluetooth
    # echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2
    echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0

# vim:noetIf anyone can help me figure this out, I'd really appreciate it.

---

### Post by Sleestax on 2009-07-06
OK, so I left out this bit of information. I am able to successfully pair my phone with the laptop. It's just that I can not set-up PAN to work since the PAN entries that are supposed to be in the bluetooth file, are not there.

I've been scouring the net for a couple of hours, but can't find anything the will explain how to fix this.

Thanks in advance for any help.

---

### Post by michy99 on 2009-07-06
I am not familiar with these programs, but you probably simply need to add the lines to the files.

Also, you need to have root permissions to edit the files, so be sure to use sudo (or gksudo for graphical programs) to open them.```
gksudo gedit /etc/default/bluetooth
```

---

### Post by Sleestax on 2009-07-06
> **michy99 said:**
> I am not familiar with these programs, but you probably simply need to add the lines to the files.

Also, you need to have root permissions to edit the files, so be sure to use sudo (or gksudo for graphical programs) to open them.```
gksudo gedit /etc/default/bluetooth
```

Thanks. I did just add them. The instructions that are shown in the original link I posted don't work for me (yet), but I was able to manually start the bnep0 interface with the following:

sudo pand --listen -c 00:17:83:CD:5C:80 --role=PANU -n --persist
sudo ifconfig bnep0
sudo ifup bnep0

After doing that, an ifconfig shows that the interface is up and running:

> 
bnep0     Link encap:Ethernet  HWaddr 00:1a:6b:13:c0:7d  

          inet addr:192.168.0.68  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::21a:6bff:fe13:c07d/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:23 errors:0 dropped:0 overruns:0 frame:0

          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2413 (2.4 KB)  TX bytes:1277 (1.2 KB)




I had to uncheck "work offline" in Firefox to get it to realize I wasn't working offline, but now everything appears to be working with the manual method. I just need to figure out how to automate it so I don't have to type it in every time. Time to start learning how to script.

---

