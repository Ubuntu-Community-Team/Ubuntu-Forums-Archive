---
title: "dm1z : bluetooth not discoverable"
date: 2011-06-05
forum: General Help
---

### Post by Redblade20XX on 2011-06-05
Hi everyone,

I've gotten everything working on this laptop but bluetooth on a 10.10 setup. I know that the system detects that there is an internal bluetooth adapter but isn't correctly configuring or using it. Here is some background, the dm1z comes with an Ralink wifi / Motorola BC8 3.0+ Adapter for bluetooth. This combo wasn't detected by the system on fresh install but I've managed to confgure the wifi driver but the bluetooth is another thing. The problem I have with the dm1z internal bluetooth is not turning on the bluetooth but discovering something.:confused: Here is some feedback from the bluez stack.

```

$ hciconfig -a
hci0:   Type: BR/EDR  Bus: USB
        BD Address: 90:00:4E:A4:63:EC  ACL MTU: 310:10  SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:1579 acl:0 sco:0 events:45 errors:0
        TX bytes:1874 acl:0 sco:0 commands:43 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'user-HP-dm1z-0'
        Class: 0x580100
        Service Classes: Capturing, Object Transfer, Telephony
        Device Class: Computer, Uncategorized
        HCI Version: 3.0 (0x5)  Revision: 0x1aa1
        LMP Version: 3.0 (0x5)  Subversion: 0x1aa1
        Manufacturer: Cambridge Silicon Radio (10)


```

```

$ hcitool dev
Devices:
        hci0    90:00:4E:A4:63:EC

```

```

$ hcitool info 90:00:4E:A4:63:EC
Device is not available or not connected.

```

```

$ hcitool name 90:00:4E:A4:63:EC 
Device is not available.

```

```

$ hcitool scan 
Scanning ...
$

```

Which leads me to believe that the bluez stack can't configure the combo wifi/bluetooth driver. So does anyone have a similar problem or a fix? Thanks for any responses!!! :)

-Red

---

### Post by faydrus on 2011-06-14
I think I've found a fix for it, based on information from a bug registered for Meego at:  [https://bugs.meego.com/show_bug.cgi?id=3498]("https://bugs.meego.com/show_bug.cgi?id=3498")

The solution is to execute the following command (needs to be executed as sudo):
**bccmd psset -s 0x0000 0x028c 0x0001**

Doing this allows for the BT adapter to actually see other devices by turning on the radio, as it appears that the BT device is active, but the radio is not.  This setting appears to stay in the device as long as it remains powered on.  In order to avoid having to manually input this command every time I power on the machine, I embedded the command within the **init.d** script for the bluetooth daemon, which is at **/etc/init.d/bluetooth**.  I'm running Ubuntu 11.04 64-bit, and here's what the script looks like now (the modification is right below the comment containing "RALink"):

[B]#! /bin/sh
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
# Note: older daemons like dund pand hidd are now shipped inside the
# bluez-compat package

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC=bluetooth

DAEMON=/usr/sbin/bluetoothd

test -f /usr/sbin/bluetoothd || exit 0

test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions

set -e

case "$1" in
  start)
	#currently this init script exists only because of what appears to be
	#an egg and chicken problem
	#  bluetoothd normally starts up by udev rules.  it needs dbus to function,
	#  but dbus doesn't start up until after udev finishes triggering
	#
	log_daemon_msg "Starting $DESC"

	# This powers on the Bluetooth radio.  It is needed by the
	# RALink Bluetooth facilities in order to work properly.
	bccmd psset -s 0x0000 0x028c 0x0001


	if [ ! -f /sbin/udevadm.upgrade ]; then
		udevadm trigger --subsystem-match=bluetooth --action=add
		log_progress_msg "bluetoothd"
	fi

	log_end_msg 0
  ;;
  stop)
	log_daemon_msg "Stopping $DESC"
	pkill -TERM bluetoothd || true
	log_progress_msg "bluetoothd"
	log_end_msg 0
  ;;
  restart|force-reload)
	$0 stop
	sleep 1
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

# vim:noet[/B]

---

### Post by Redblade20XX on 2011-06-14
> **faydrus said:**
> I think I've found a fix for it, based on information from a bug registered for Meego at:  [https://bugs.meego.com/show_bug.cgi?id=3498]("https://bugs.meego.com/show_bug.cgi?id=3498")

The solution is to execute the following command (needs to be executed as sudo):
**bccmd psset -s 0x0000 0x028c 0x0001**

Doing this allows for the BT adapter to actually see other devices by turning on the radio, as it appears that the BT device is active, but the radio is not.  This setting appears to stay in the device as long as it remains powered on.  In order to avoid having to manually input this command every time I power on the machine, I embedded the command within the **init.d** script for the bluetooth daemon, which is at **/etc/init.d/bluetooth**.  I'm running Ubuntu 11.04 64-bit, and here's what the script looks like now (the modification is right below the comment containing "RALink"):

[B]#! /bin/sh
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
# Note: older daemons like dund pand hidd are now shipped inside the
# bluez-compat package

PATH=/sbin:/bin:/usr/sbin:/usr/bin
DESC=bluetooth

DAEMON=/usr/sbin/bluetoothd

test -f /usr/sbin/bluetoothd || exit 0

test -f /etc/default/rcS && . /etc/default/rcS

. /lib/lsb/init-functions

set -e

case "$1" in
  start)
	#currently this init script exists only because of what appears to be
	#an egg and chicken problem
	#  bluetoothd normally starts up by udev rules.  it needs dbus to function,
	#  but dbus doesn't start up until after udev finishes triggering
	#
	log_daemon_msg "Starting $DESC"

	# This powers on the Bluetooth radio.  It is needed by the
	# RALink Bluetooth facilities in order to work properly.
	bccmd psset -s 0x0000 0x028c 0x0001


	if [ ! -f /sbin/udevadm.upgrade ]; then
		udevadm trigger --subsystem-match=bluetooth --action=add
		log_progress_msg "bluetoothd"
	fi

	log_end_msg 0
  ;;
  stop)
	log_daemon_msg "Stopping $DESC"
	pkill -TERM bluetoothd || true
	log_progress_msg "bluetoothd"
	log_end_msg 0
  ;;
  restart|force-reload)
	$0 stop
	sleep 1
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

# vim:noet[/B]

Can you post your bluez version?

---

### Post by Redblade20XX on 2011-07-08
Confirmed fix for bluetooth!

```
                     Originally Posted by **XEMD38**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11020393#post11020393")                 
[I]With Ralink FAE, we found that the radio is OFF and the following command has to be executed to turn ON the device again: 

***sudo bccmd psset -s 0x0000 0x028c 0x0001***

+ reboot

and after that bluetooth work fine (enable and disable in same time with wifi)


Tested on HP DV7-6090EF (Ralink RT5390 Combo Wifi/bluetooth) Driver ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) ) V2.4.0.4  Ubuntu Natty 11.04 64 bits

Source : [https://bugs.meego.com/show_bug.cgi?id=3498](https://bugs.meego.com/show_bug.cgi?id=3498)[/I]

```

---

