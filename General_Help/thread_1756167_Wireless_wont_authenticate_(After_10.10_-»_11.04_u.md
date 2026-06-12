---
title: "Wireless wont authenticate (After 10.10 -» 11.04 upgrade)"
date: 2011-05-11
forum: General Help
---

### Post by OpPoSiTe on 2011-05-11
Greets,
I've been surfing the forums and beyond trying to find an answer to this problem, and it seems this time i cannot find an answer by my own. 

My wireless setup was working perfectly in 10.10 but after the upgrade to 11.04 all went wrong, i can see the device yes, and i can see the networks but when i try to connect it asks to reinput the password. And if i try with Wicd it says "bad password" the thing is, the password is the same i was using in 10.10 and it cant connect to an open network either.

Im a bit new at all this, but as far as i know i was using p54 drivers in 10.10. in order to make the dongle work i hat to install "linux-firmware-nonfree"... 
tryed to reinstall it, but the same result. Tried windows drivers too with ndiswrapper, and the same result again.

Im out of ideas.

lsusb:

Bus 001 Device 007: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle


Thanks in advance.
Op

---

### Post by deonis on 2011-05-11
Hi, is your your network has a wpa security? please type in terminal: service --status-all and check for process: wpa-ifupdown. Is it off? thanks

---

### Post by OpPoSiTe on 2011-05-11
yes, i use WPA

[SIZE=1]Security:[/SIZE][SIZE=1]WPA-PSK[/SIZE] [SIZE=1][IMG]http://192.168.1.254/images/spacer.gif[/IMG][/SIZE]   [SIZE=1]Encription WPA-PSK:[/SIZE][SIZE=1]TKIP&AES[/SIZE] [SIZE=1][IMG]http://192.168.1.254/images/spacer.gif[/IMG][/SIZE] [SIZE=1]Version WPA-PSK:[/SIZE][SIZE=1]WPA&WPA2[/SIZE]

and there is no "wpa-ifupdown" entry in the "service --status-all" list.

Thanks
Op

---

### Post by OpPoSiTe on 2011-05-12
Just another piece of information:
Wireless connection works fine if i use a windows box or a 10.04 box.
In 11.04 the only way to have an active connection is with ethernet cable plugged on router because of this authentication problem :sad:

---

### Post by NattyUser on 2011-05-12
Hi,

can you actualy see the wifi network?. I mean, if you type: iwlist wlan0 scan, do you get the list of available networks?

I'm just asking because i have the same usb dongle and since i upgrade to natty i can't see the netwoks!

My thread -> [http://ubuntuforums.org/showthread.php?t=1744901&highlight=121g](http://ubuntuforums.org/showthread.php?t=1744901&highlight=121g)

---

### Post by deonis on 2011-05-12
try to check is the package wpasupplicant instaled on your system if not install it and restart your network.

---

### Post by OpPoSiTe on 2011-05-12
> Hi,

can you actualy see the wifi network?. I mean, if you type: iwlist wlan0 scan, do you get the list of available networks?

I'm just asking because i have the same usb dongle and since i upgrade to natty i can't see the netwoks!
Yes, i can see the networks and i can see them in network manager and wicd.

> try to check is the package wpasupplicant instaled on your system if not install it and restart your network.Yes, it was installed. i tried a reinstall followed by a reboot. same result.

Thanks
Op

---

### Post by deonis on 2011-05-12
well everything seems alright, except wpa-ifupdown, you will need to run it. type the following in terminal: 
1) sudo /etc/init.d/dbus restart
2) chkconfig wpa-ifupdown
or service --status-all

and please let me know if you'll see wpa-ifupdown with ? running


also you should have wpa-ifupdown script in /etc/int.d/

---

### Post by OpPoSiTe on 2011-05-12
> type the following in terminal: 
1) sudo /etc/init.d/dbus restart
2) chkconfig wpa-ifupdown
or service --status-all
and please let me know if you'll see wpa-ifupdown with ? running
also you should have wpa-ifupdown script in /etc/int.d/-» service --status-all
there is no "wpa-ifupdown" on the output

-» chkconfig wpa-ifupdown
wpa-ifupdown: unknown service

and there is no script with that name on that folder :-k
Tried to reinstall wpa-suplicant... it reinstalled, but still the same.

Op

---

### Post by deonis on 2011-05-12
here is the script:

---

### Post by deonis on 2011-05-12
sorry 

```
#!/bin/sh

### BEGIN INIT INFO
# Provides:             wpa-ifupdown
# Required-Start:       $network
# Required-Stop:        $network $remote_fs
# Should-Start:
# Should-Stop:
# Default-Start:
# Default-Stop:         0 6
# Short-Description:    Stop wpa_supplicant processes started via ifupdown
# Description:          Run ifdown on interfaces authenticated via
#                       wpa_supplicant. Sendsigs terminates wpa_supplicant
#                       processes before networking is stopped causing each
#                       network interface authenticated via a wpa_supplicant
#                       daemon to be terminated abrubtly.
#                       Since initscripts package version 2.86.ds1-48 an
#                       interface exists to omit process id's from sendsigs. If
#                       this interface is present this script is a no-op.
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin

test -d /var/run || exit 0

test -x /sbin/ifdown || exit 0

. /lib/lsb/init-functions

stop_wpa_action () {
	test -x /sbin/wpa_action || return 0
	IFACES=$(find /var/run -maxdepth 1 -type f -name 'wpa_action.*.pid' -printf '%P\n' | \
		cut -d'.' -f2 2>/dev/null)
	if test -n "$IFACES"; then
		log_daemon_msg "Stopping wpa_action roaming interfaces"
		for iface in $IFACES; do
			log_progress_msg "$iface"
			# wpa_action executes /sbin/ifdown
			wpa_action "$iface" stop >/dev/null 2>&1
		done
		log_end_msg 0
	fi
}

stop_wpa_supplicant () {
	IFACES=$(find /var/run -maxdepth 1 -type f -name 'wpa_supplicant.*.pid' -printf '%P\n' | \
		grep -v wpa_supplicant.dbus.pid | cut -d'.' -f2 2>/dev/null)
	if test -n "$IFACES"; then
		log_daemon_msg "Stopping wpa_supplicant interfaces"
		for iface in $IFACES; do
			log_progress_msg "$iface"
			ifdown "$iface" >/dev/null 2>&1
		done
		log_end_msg 0
	fi
}

sendsigs_omission_support () {
	if [ -d /lib/init/rw/sendsigs.omit.d/ ]; then
		# Debian
		return 0
	elif [ -d /var/run/sendsigs.omit.d/ ]; then
		# Ubuntu, cf. https://bugs.launchpad.net/bugs/181541
		return 0
	fi

	return 1
}

case "$1" in
	start|restart|force-reload)
		# No-op
		;;
	stop)
		if sendsigs_omission_support; then
			stop_wpa_action
		else
			stop_wpa_action
			stop_wpa_supplicant
		fi
		;;
	*)
		echo "Usage: $0 {start|stop|restart|force-reload}" >&2
		exit 3
		;;
esac

exit 0
```

---

### Post by deonis on 2011-05-12
and now again:

sudo /etc/init.d/dbus restart

---

### Post by OpPoSiTe on 2011-05-12
Done it.

:~$ chkconfig wpa-ifupdown
wpa-ifupdown  off

and in 

:~$ service --status-all
 [ ? ]  wpa-ifupdown


But still cant connect :-?

---

### Post by deonis on 2011-05-12
did you try to restart your computer? :)

---

### Post by OpPoSiTe on 2011-05-12
yes, i did. 
Still the same ](*,)

---

### Post by deonis on 2011-05-12
do you have access to the router ? please change security to wep... and try again. sorry I am clueless

---

### Post by OpPoSiTe on 2011-05-12
Yes i do have access to the router, and no, it doesn't work on WEP or even without security.

Thanks for your help deonis. it may not have solved the problem but at least i learned a bit more :rolleyes:


Any1 out there? feel free to jump in...

---

### Post by deonis on 2011-05-12
try wicd manager instead of network manager (you will need to remove it) it might help - but clearly something is terribly wrong happen with your system :). Good luck - you will need it :)

---

### Post by OpPoSiTe on 2011-05-13
Today i tryed to reinstall ubuntu 11.04 from scratch, all went well except for the wireless issue.

So i installed "linux-firmware-nonfree" in order to get my 1st dongle to work (Thomson SpeedTouch 121g) and it started to find networks... but it cannot associate/authenticate. 

Then i decided to test with my second dongle (SMC 2862W-G EU) had to install the windows drivers with ndiswrapper. it started to work and found the networks...

But it still cant connect :confused: im really out of ideas.

---

### Post by DiomedesLost on 2011-05-21
Im having the same issue, and i havent been able to find any solution either. Its so bad its making me want to use windows. yikes.

---

### Post by jan_valentin on 2011-05-21
I am also having the same issue. Right now, I can only connect via my ethernet cable plugged into the router. I have tried a lot (if not all) of the things in this thread without success and I am seriously thinking about moving back to Windows. I have a disk of Win7 ready to go at this point.

Addendum: Maybe I'll switch to 10.10 (this was clean install of Kubuntu 11.04) but that seems wrong and backwards to me.

---

### Post by OpPoSiTe on 2011-05-25
yep, im still trying to solve this. nothing yet ](*,)

---

### Post by fede.pont on 2011-05-29
Ok, I have solved my problem, but I think it is not the same.

First the  facts:

Ubuntu NAtty 11.04 (Upgraded from 10.04)

product: BCM4313 802.11b/g/n Wireless LAN Controller (For all of you who have read forums on wireless connectivity, this broadcom model always gives a headache. Now it works with generic brcm80211 driver that comes with natty 11.04.)

configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic 

The problem: 

Starting my computer without a cable modem connected I was unable to see wireless networks. But the module driver was running and the Network Manager shows the possibility of wireless connectivity. Forcing a hidden network connect, the logging keep asking the password over and over.

Here is the strange behavior. When I connect a cable from the router, the connection works fine and gives me access through wireless!, yes I unplug the cable and was able to stay wireless connected!

I used the script given in post #11 for the  wpa-ifupdown. Now, in a fresh reboot the wireless is not available, but i can load the module manually and it works fine. I have tried to put the module in /etc/modules file but doesn't work (?).

I hope this problems to be solved in the next actualization, since I have the same problems with 10.04 and then magically fixed with one actualiz.

---

