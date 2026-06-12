---
title: "3G modem don't like suspend"
date: 2009-08-10
forum: General Help
---

### Post by azzid on 2009-08-10
Hi,

this is a rather flaky post since it regards a problem I can only intermittently reproduce, but here is my issue:

I have a Asus eee 901 with Ubuntu 9.04 NBR.
It has an integrated 3G modem, which mostly works fine.
But just before the last reboot it just disappeared, the Network-Manager applet removed the option to connect to my ppp-connection after the computer recovered from suspend.

lsusb gives:```
Bus 001 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```

and did so even when Network-Manager did not acknowledge the existance of the device.

I have a two idéas to work around this issue:
1. Could I add a disconnection from the ppp-connection as part of the suspension/hibernation routine? (this only seem to happen when the modem is connected)
2. Could I somehow reinitialize the usb-device after restoring the computer without rebooting? (plugging in and out is not an option since the device is integrated)
 
What do you think? Is there some other, better, way to approach this?

Sincerely,
Mattias

---

### Post by bodyharvester on 2009-08-10
> **azzid said:**
> Hi,

this is a rather flaky post since it regards a problem I can only intermittently reproduce, but here is my issue:

I have a Asus eee 901 with Ubuntu 9.04 NBR.
It has an integrated 3G modem, which mostly works fine.
But just before the last reboot it just disappeared, the Network-Manager applet removed the option to connect to my ppp-connection after the computer recovered from suspend.

lsusb gives:```
Bus 001 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
```and did so even when Network-Manager did not acknowledge the existance of the device.

I have a two idéas to work around this issue:
1. Could I add a disconnection from the ppp-connection as part of the suspension/hibernation routine? (this only seem to happen when the modem is connected)
2. Could I somehow reinitialize the usb-device after restoring the computer without rebooting? (plugging in and out is not an option since the device is integrated)
 
What do you think? Is there some other, better, way to approach this?

Sincerely,
Mattias

hi, try a live cd of another distro, download em or get them in a linux magazine, if its still not detected it could be a problem with the modem itself

---

### Post by azzid on 2009-08-13
Oh, the problem is that the card stops working if I suspend the computer with the connection running, not that the system is unable to detect it.

I'm using the same very connection to write this, but if I close the lid of my laptop now it will send the computer to hibernation, after that it is likely that I will be unable to reconnect to the internet when the computer awakes.

What I think I need is to be able to do the software eqvivalent of removing and replugging the integrated usb device.

---

### Post by GeorgeVita on 2009-08-19
Hi **azzid**, to determine what is happening you can do the following:

Reboot, connect, disconnect as usual.
See the system activity on ttyUSBx ports created for your modem: ```
dmesg | grep tty
```Suspend, resume, try again above command. Compare results and note driver used (usually is **option**).
Then try to 'unload' option driver and 'reload hardware drivers': ```
sudo modprobe -r option
sudo /etc/init.d/udev refresh-devices
```

At any time the **dmesg | grep tty** will show you the creation/disconnection of the communication ports.

Regards,
George

---

### Post by azzid on 2009-08-19
> **GeorgeVita said:**
> 
Reboot, connect, disconnect as usual.
See the system activity on ttyUSBx ports created for your modem: ```
dmesg | grep tty
```Suspend, resume, try again above command. 


```

#dmesg | grep tty
[ 5844.173654] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 5844.173794] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 5844.173925] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 5849.333344] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[ 5849.333658] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[ 5849.333927] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2

```

> **GeorgeVita said:**
> 
Compare results and note driver used (usually is **option**).
Then try to 'unload' option driver and 'reload hardware drivers': ```
sudo modprobe -r option
sudo /etc/init.d/udev refresh-devices
```


```
#sudo modprobe -r option1
FATAL: Module option1 not found.
```

In this particular case the connection was off and I had another problem than the one initially described, I was namely able to manage the device from network manager this time, but the initial connection failed to apply the dns-settings from the dhcp, I had to disconnect and reconnect for that to work.

My initial problem was a total loss of communication between network-manager and the 3G-module. That particular problem I have been unable to reproduce.

```
sudo /etc/init.d/udev refresh-devices
 * Loading additional hardware drivers...                                                                             [ OK ] 

```

This command confused network-manager quite a bit, after running it I had dual network devices of every kind (two 3G-modules, two wired and two wlan connections), it still worked however.

```
#sudo modprobe -r option

```

In the above case the modprobe worked and cleaned up most of the extra network devices, the 3G-model representation did not work however.

```
#sudo /etc/init.d/udev refresh-devices
 * Loading additional hardware drivers...                                                                             [ OK ] 

```

After running this command I once again had multiple instances of all the network devices in network-manager, but atleast some of them worked. ;)

The cleanest solution that springs to my mind right now would probably be to append a disconnect from the 3G-connection to the suspend/hibernate-routine. What do you think about that?

---

### Post by GeorgeVita on 2009-08-19
Hi **azzid**,
before answering to a post I am trying to 'simulate' the problem to my PC using my 3G modems. In your case the problem appeared as a 'lock' on /dev/ttyUSB0 (default port used by network manager to connect) and after resume (sometimes) I had a 'shift' on the /dev/ttyUSBx ports (1-2-3 instead of 0-1-2). Another time the modem did not appeared at all (ports not created), possibly caused by a 'bad timing' on reset at modem and/or USB subsystem. Also note the behavior of the power supply is different when plugged into mains outlet, USB ports are powered just in case of charging an external peripheral.

Your idea is good (disconnect first and then suspend) but this is the way it MUST be. All programs/peripherals must go to idle state.

About the dual appearance of the 'modem/wifi/...' we must check man pages for a parameter forcing 'reload' and not 'add'!

Regards,
George

---

### Post by azzid on 2009-08-20
Today the module was even more lost in itself, I had to reboot three times before I could get online with it. One of those times the computer froze so hard upon initial connection (not to 3G but wlan) that I had to force it down holding the power button.

Onwards to your post though!

> **GeorgeVita said:**
> 
before answering to a post I am trying to 'simulate' the problem to my PC using my 3G modems. In your case the problem appeared as a 'lock' on /dev/ttyUSB0 (default port used by network manager to connect) and after resume (sometimes) I had a 'shift' on the /dev/ttyUSBx ports (1-2-3 instead of 0-1-2). Another time the modem did not appeared at all (ports not created), possibly caused by a 'bad timing' on reset at modem and/or USB subsystem. Also note the behavior of the power supply is different when plugged into mains outlet, USB ports are powered just in case of charging an external peripheral.


This lock, how did you identify it? I seem to get all three /dev/ttyUSBx ports attached to the modem, or am I reading this wrong? (My call is based solely on the output of dmesg.)

> **GeorgeVita said:**
> 
Your idea is good (disconnect first and then suspend) but this is the way it MUST be. All programs/peripherals must go to idle state.


So, what you're saying is that a extra 'disconnect' to the suspension-script would add no functionality?

> **GeorgeVita said:**
> 
About the dual appearance of the 'modem/wifi/...' we must check man pages for a parameter forcing 'reload' and not 'add'!


I started looking for the correct manual and ended up reading the init script for udev, the part doing the refresh looks like this:
```
    **refresh-devices)**
        cp -au /lib/udev/devices/* /dev

        log_begin_msg "Loading additional hardware drivers..."
        /sbin/udevadm trigger
        if /sbin/udevadm settle; then
            log_end_msg 0
        else
            log_end_msg $?
        fi
        ;;

```
I do not really understand the cp in the beginning, but I guess udev manages its own set of device files?

After that the command **/sbin/udevadm trigger** is the only thing I can see that actually does something, so I started reading the manual for udevadm. It gave me nothing, but I tried running the 'udevadm trigger' command separately on the machine and once again I had the duality issue.

During my tests today the problems with the connection, as I mentioned it in the beginning keep coming back, getting online is really hard, the network manager just fails.

Could we've broken something with the things we did yesterday? Seems unlikely...

I figured out that network-manager logs its activities to /var/log/daemon.log, so I had a look there doing a few operations.

This is what I get in the log when network manager fail to connect:
```
Aug 20 11:49:17 computername NetworkManager: <info>  Activation (ttyUSB0) starting connection '3 (Mobilt Bredband)' 
Aug 20 11:49:17 computername NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Aug 20 11:49:17 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 20 11:49:17 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Aug 20 11:49:17 computername NetworkManager: <debug> [1250761757.783417] nm_serial_device_open(): (ttyUSB0) opening device... 
Aug 20 11:49:17 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Aug 20 11:49:18 computername NetworkManager: <info>  (ttyUSB0): powering up... 
Aug 20 11:49:18 computername NetworkManager: <info>  Registered on Roaming network 
Aug 20 11:49:18 computername NetworkManager: <info>  Associated with network: +COPS: 0,2,"24004",2 
Aug 20 11:49:18 computername NetworkManager: <info>  Connected, Woo! 
Aug 20 11:49:18 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 20 11:49:18 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Aug 20 11:49:18 computername NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Aug 20 11:49:18 computername NetworkManager: <info>  Starting pppd connection 
Aug 20 11:49:18 computername NetworkManager: <debug> [1250761758.233531] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Aug 20 11:49:18 computername NetworkManager: <debug> [1250761758.267066] nm_ppp_manager_start(): ppp started with pid 3495 
Aug 20 11:49:18 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Aug 20 11:49:34 computername NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module 
Aug 20 11:49:34 computername NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9 
Aug 20 11:49:34 computername NetworkManager: <debug> [1250761774.002550] nm_serial_device_close(): Closing device 'ttyUSB0' 
Aug 20 11:49:34 computername NetworkManager: <info>  Marking connection '3 (Mobilt Bredband)' invalid. 
Aug 20 11:49:34 computername NetworkManager: <info>  Activation (ttyUSB0) failed. 
Aug 20 11:49:34 computername NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Aug 20 11:49:34 computername NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Aug 20 11:49:34 computername NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Aug 20 11:49:34 computername NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Aug 20 11:49:36 computername NetworkManager: <debug> [1250761776.002676] ensure_killed(): waiting for ppp pid 3495 to exit 
Aug 20 11:49:36 computername NetworkManager: <debug> [1250761776.002991] ensure_killed(): ppp pid 3495 cleaned up 

```

And this is what gets logged during 'udevadm trigger':
```
Aug 20 11:41:37 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_23_54_8f_0d_36_0, iface: eth0): not well known
Aug 20 11:41:37 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_43_56_fe_3b_2, iface: wlan0): not well known
Aug 20 11:41:38 computername NetworkManager: <info>  (eth0): new Ethernet device (driver: 'ATL1E') 
Aug 20 11:41:38 computername NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_23_54_8f_0d_36_0 
Aug 20 11:41:38 computername NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Aug 20 11:41:38 computername NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k_pci') 
Aug 20 11:41:38 computername NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_22_43_56_fe_3b_2 
Aug 20 11:41:38 computername NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties 
Aug 20 11:41:38 computername NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Aug 20 11:41:40 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_noserial_0_if0_serial_usb_0, iface: (null)): iface not found
Aug 20 11:41:40 computername NetworkManager: <info>  (ttyUSB0): found serial port (udev:GSM  hal:GSM) 
Aug 20 11:41:40 computername NetworkManager: <info>  (ttyUSB0): new Modem device (driver: 'option') 
Aug 20 11:41:40 computername NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_12d1_1001_noserial_0_if0_serial_usb_0 
Aug 20 11:41:43 computername NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 20 11:41:43 computername NetworkManager: <info>  (eth0): preparing device. 
Aug 20 11:41:43 computername NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 20 11:41:43 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 11:41:43 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 11:41:43 computername NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Aug 20 11:41:43 computername NetworkManager: <info>  (wlan0): bringing up device. 
Aug 20 11:41:43 computername NetworkManager: <info>  (wlan0): preparing device. 
Aug 20 11:41:43 computername NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Aug 20 11:41:43 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 11:41:43 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 11:41:44 computername avahi-daemon[2716]: Registering new address record for fe80::222:43ff:fe56:fe3b on wlan0.*.
Aug 20 11:41:45 computername NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 
Aug 20 11:41:45 computername NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2). 
Aug 20 11:41:45 computername NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Aug 20 11:41:45 computername NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Aug 20 11:41:45 computername NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 

```

Since adding this I have not been able to connect using 3G even once. I will try booting a live image and see if the issue persists.

---

### Post by azzid on 2009-08-20
I figured out my newfound connection issue, it was due to this **[bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/371291")**.

Problem was I was tailing daemon.log from a root shell, exit that shell and connection worked again.

I was able to get a log of a successful connection attempt:
```
Aug 20 12:42:51 computername NetworkManager: <info>  Activation (ttyUSB0) starting connection '3 (Mobilt Bredband)' 
Aug 20 12:42:51 computername NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Aug 20 12:42:51 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 20 12:42:51 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Aug 20 12:42:51 computername NetworkManager: <debug> [1250764971.052658] nm_serial_device_open(): (ttyUSB0) opening device... 
Aug 20 12:42:51 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Aug 20 12:42:52 computername NetworkManager: <info>  (ttyUSB0): powering up... 
Aug 20 12:42:52 computername NetworkManager: <info>  Registered on Roaming network 
Aug 20 12:42:52 computername NetworkManager: <info>  Associated with network: +COPS: 0,2,"24004",2 
Aug 20 12:42:52 computername NetworkManager: <info>  Connected, Woo! 
Aug 20 12:42:52 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 20 12:42:52 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Aug 20 12:42:52 computername NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Aug 20 12:42:52 computername NetworkManager: <info>  Starting pppd connection 
Aug 20 12:42:52 computername NetworkManager: <debug> [1250764972.324709] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Aug 20 12:42:52 computername NetworkManager: <debug> [1250764972.327924] nm_ppp_manager_start(): ppp started with pid 4441 
Aug 20 12:42:52 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Aug 20 12:42:52 computername NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6 
Aug 20 12:42:52 computername NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Aug 20 12:42:54 computername NetworkManager: <info>  PPP manager(IP Config Get) reply received. 
Aug 20 12:42:54 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 20 12:42:54 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) started... 
Aug 20 12:42:54 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 20 12:42:54 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 20 12:42:54 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 20 12:42:55 computername NetworkManager: <info>  Policy set 'Auto Pinpoint' (wlan0) as default for routing and DNS. 
Aug 20 12:42:55 computername NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 
Aug 20 12:42:55 computername NetworkManager: <info>  Activation (ttyUSB0) successful, device activated. 
Aug 20 12:42:55 computername NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.
```

---

### Post by azzid on 2009-08-20
Also I kept experimenting with suspend/hibernate until I was able to get the computer in a state where it had once again lost contact with the 3G-module.

This time the ```
sudo modprobe -r option
sudo /etc/init.d/udev refresh-devices
``` did not help, I only got duplicate wlan/lan, but no 3G.

The following had been added to daemon.log when I got back after the hibernation and the module wasn't working:```
Aug 20 13:08:17 computername acpid: client 2725[0:0] has disconnected 
Aug 20 13:08:17 computername NetworkManager: <debug> [1250766497.417806] ensure_killed(): waiting for ppp pid 7145 to exit 
Aug 20 13:08:17 computername NetworkManager: <debug> [1250766497.418013] ensure_killed(): ppp pid 7145 cleaned up 
Aug 20 13:08:17 computername nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_noserial_if0_serial_usb_0)
Aug 20 13:08:24 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_noserial_if0_serial_usb_0, iface: (null)): iface not found
Aug 20 13:08:49 computername acpid: client connected from 2725[0:0] 
Aug 20 13:08:49 computername NetworkManager: <info>  Waking up... 
Aug 20 13:08:49 computername NetworkManager: <info>  (eth0): now managed 
Aug 20 13:08:49 computername NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 20 13:08:49 computername NetworkManager: <info>  (eth0): bringing up device. 
Aug 20 13:08:49 computername NetworkManager: <info>  (eth0): preparing device. 
Aug 20 13:08:49 computername NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 20 13:08:49 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 13:08:49 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 13:08:49 computername NetworkManager: <info>  (wlan0): now managed 
Aug 20 13:08:49 computername NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Aug 20 13:08:49 computername NetworkManager: <info>  (wlan0): bringing up device. 
Aug 20 13:08:49 computername NetworkManager: <info>  (wlan0): preparing device. 
Aug 20 13:08:49 computername NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Aug 20 13:08:49 computername NetworkManager: <info>  (ttyUSB0): found serial port (udev:  hal:GSM) 
Aug 20 13:08:49 computername NetworkManager: <info>  (ttyUSB0): ignoring due to lack of probed mobile broadband capabilties 
Aug 20 13:08:49 computername NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties 
Aug 20 13:08:49 computername NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Aug 20 13:08:51 computername avahi-daemon[2767]: Registering new address record for fe80::222:43ff:fe56:fe3b on wlan0.*.
Aug 20 13:10:37 computername nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_noserial_if0_serial_usb_0)
Aug 20 13:11:19 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_23_54_8f_0d_36_0, iface: eth0): not well known
Aug 20 13:11:20 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_22_43_56_fe_3b_2, iface: wlan0): not well known
Aug 20 13:11:20 computername NetworkManager: <info>  (eth0): new Ethernet device (driver: 'ATL1E') 
Aug 20 13:11:20 computername NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_23_54_8f_0d_36_0 
Aug 20 13:11:21 computername NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
Aug 20 13:11:21 computername NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k_pci') 
Aug 20 13:11:21 computername NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_22_43_56_fe_3b_2 
Aug 20 13:11:21 computername NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties 
Aug 20 13:11:21 computername NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties 
Aug 20 13:11:24 computername NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 20 13:11:24 computername NetworkManager: <info>  (eth0): preparing device. 
Aug 20 13:11:24 computername NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 20 13:11:25 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 13:11:25 computername NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Aug 20 13:11:25 computername NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Aug 20 13:11:25 computername NetworkManager: <info>  (wlan0): preparing device. 
Aug 20 13:11:25 computername NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Aug 20 13:11:27 computername nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001_noserial_0_if0_serial_usb_0, iface: (null)): iface not found
Aug 20 13:11:27 computername NetworkManager: <info>  (ttyUSB0): found serial port (udev:  hal:GSM) 
Aug 20 13:11:27 computername NetworkManager: <info>  (ttyUSB0): ignoring due to lack of probed mobile broadband capabilties 

```

---

### Post by GeorgeVita on 2009-08-20
Hi **azzid**, note that I am also trying to test 9.10 where some programs are 'floating' and many things are changing including suspend, 3G support, new front end for network manager and new version of network manager...

The 'lock' of /dev/ttyUSB0 appeared to me as recreation of /dev/ttyUSB1-2-3 (instead of 0-1-2) after udev refresh-devices.

I will try again my 9.04 installation with Huawei E169 attached and connected to internet doing some suspends, and I will come back later...

---

### Post by GeorgeVita on 2009-08-20
Below is a good behaviour from my 9.04 installation (running from SDHC on EeePC1000H) before suspend, connected:```
g@sd:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[   13.632346] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[   13.632532] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[   13.632716] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB2
g@sd:~$ ps -A | grep -i modem
g@sd:~$ ps -A | grep -i manager
 3226 ?        00:00:00 NetworkManager
g@sd:~$ ps -A | grep -i ppp
 3875 ?        00:00:00 pppd
g@sd:~$ ps -A | grep -i firefox
 4030 ?        00:00:15 firefox
```

After resume (auto disconnected from suspend):
```
g@sd:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[   13.632346] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[   13.632532] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[   13.632716] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB2
[  226.833665] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  226.833806] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  226.833942] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  231.137640] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[  231.137927] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[  231.138207] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB2
g@sd:~$ ps -A | grep -i modem
g@sd:~$ ps -A | grep -i manager
 3226 ?        00:00:00 NetworkManager
g@sd:~$ ps -A | grep -i ppp
```

I used only **dmesg** and **ps** commands for simplicity.
Note that my modem was always powered! I will check again and i will remove modem during suspend just to simulate the case your internal modem is switched off. Then I will attach it some seconds before the resume. If the result is the same (good) I will edit this post and report it, else I will make a new post with new data.

**>>> EDIT: Same good behaviour with physical removal during suspend.**

**>>> New EDIT: I can confirm** that 'sudo /etc/init.d/udev refresh-devices' creates multiple entries at n.m. icon. Trying various commands and trying to connect once the 'mobile broadband connection' disappeared without updating dmesg! Restored with '... udev refresh-devices' adding more ethernet/wifi connections. But now the 'mobile' connection worked.

I suppose above is better with 9.10 (I'll check it again).

Regards,
George

---

### Post by azzid on 2009-08-20
I get the same result, before suspend:
```
user@computer:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[    6.134215] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[    6.134412] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[    6.134969] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
user@computer:~$ ps -A | grep -i modem
user@computer:~$ ps -A | grep -i manager
 2745 ?        00:00:00 NetworkManager
user@computer:~$ ps -A | grep -i ppp
 3465 ?        00:00:00 pppd

```

After suspend/resume:
```
user@computer:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[    6.134215] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[    6.134412] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[    6.134969] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[  122.224328] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  122.224470] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  122.224601] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  127.538000] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[  127.539112] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[  127.540129] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
user@computer:~$ ps -A | grep -i modem
user@computer:~$ ps -A | grep -i manager
 2745 ?        00:00:00 NetworkManager
user@computer:~$ ps -A | grep -i ppp

```

But in this particular case the connection worked (more or less, I had to push 'connect' twice).

I think I have been confusing a few terms though.

When I used the 'close lid' to **suspend** the computer I had issues when I forgot to disconnecct the 3G, but that was mostly that Netwok-Manager failed to fetch dns-servers for the connection.

Now that I have switched to **hibernation** the other problem appeared where the 3G module isn't recognized by Network-Manager at all.

Hence it might be two completely separate issues... Sorry for being confusing.

---

### Post by GeorgeVita on 2009-08-20
Hi **azzid**, I cannot try hibernation on my 9.04 as it runs from SDHC. Behaviour of 'sudo /etc/init.d/udev refresh-devices' is fine on 9.10 (no extra lines on n.m. icon) but hibernation is just catastrophic!

After resuming hibernation and cannot connect try the following:

1. check the ports:
```
dmesg | grep tty
```

2. remove and add again **option** driver:
```
sudo modprobe -r option
sudo modprobe option
```

In my tests the ports are disconnected/created again without the problems on eth/wifi.

Regards,
George

---

### Post by azzid on 2009-08-21
Every time I do the
```
#sudo modprobe -r option
#sudo modprobe option
```

I get 6 new lines added to the output of ```
#dmesg | grep tty
```

So that seems to be working, but the 3G option is still missing from the nm-applet.

This time when I managed to lose the 3G i also realized that the wlan was having some issues, it could not connect to the network, just kept asking me to unlock the keyring.

I did this to get the wlan running again:```

#ps -edaf | grep -i network
root      3369     1  0 Aug19 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      3394     1  0 Aug19 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root     23829 23535  0 12:52 pts/0    00:00:00 grep -i network

#sudo kill 3369
#sudo /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid

```

That got Network-Manager handling wlan as it should again, but the 3G is still lost.

Then I went a little further with the same trick and broke it again, but I still think maybe the whole thing is more isolated to Networkmanager than the underlying system?

---

