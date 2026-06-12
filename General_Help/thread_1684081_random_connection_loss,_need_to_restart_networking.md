---
title: "random connection loss, need to restart networking to fix, want to automate this"
date: 2011-02-08
forum: General Help
---

### Post by phazei on 2011-02-08
I have Ubuntu Server installed on a headless box and randomly it will loose the wireless network connection.
Sometimes it happens when I'm just sitting at the CLI, sometimes it happens when I load "startx | x11vnc -display :0" (i added xfce, not xubuntu).  Not all the time, just occasionally. It's a huge problem when I'm away from the box.

When it does happen, iwconfig doesn't even show a SSID.  But doing a "/etc/init.d/networking restart" always fixes the problem

I would like to have it automatically run "/etc/init.d/networking restart" if it detects it no longer has a connection, but I'm not sure how to go about that.  Would the "post-down" event in interfaces even be triggered if it's just losing connection?  Is there anything else that's triggered on network loss?  Would I need to run a cron every minute to test it or something?

Not sure the proper way to fix this, please advise.

Thanks.

---

### Post by phazei on 2011-02-09
Can anyone point me to a guide or something that will let me automate the network process so the machine can run autonomously and correct itself in the case of a networking issue?

I'd like the system to reboot itself if restarting networking didn't work after a few tries over a few minutes, keep track of how many times it's needed to restart, and give up after it's restarted a couple times and reset the network settings a few.

---

### Post by dino99 on 2011-02-09
if you can connect an other pc/laptop on the same wireless spot and into the same place, that let you know where to search: is it a bad wireless spot, are you logged too far from it, ...

are some logs usefull ? (xsession-errors, /var/log/)

---

### Post by phazei on 2011-02-09
It's definitely the box and not the spot.  It connects to my router running DD-WRT and is about 15 feet away.  My laptop which is next to the router has no issues with the connection.

The wireless USB NIC is a Zydas ZD1211.

I'll need to check the logs when I get home.  It also loses connection when I'm not running any xsession, so I'll check some of the other logs.  The last time it happened when I was in front of the box I tried to do a "dhclient wlan0" but it just kept trying to get a new ip and failed, but restarting networking got a new ip right away.

I know how to setup a cron job, but I'm not certain how to write a script that could count how many times it was run and how many times the computer was reset.  When the problem occurs I can't even ping the default gateway, so I suppose any script could attempt to ping it and in the case of a failure restart networking or reboot depending on the count of what it's already tried.  But I figure it would be better if a script would run with some trigger on losing internet connection rather than needing to 'poll' by pinging every 5 minutes or so.  Actually, I could easily write a PHP script to do that and store the counters in some serialized file.  I can run PHP in CLI mode.  How common is that to do?  Is it considered.. kosher ..to use PHP scripts rather than bash ones do perform system functions?  Also would there be any standard location for me to place the files?

---

### Post by phazei on 2011-02-09
The syslog has a lot of this in it:
> Feb  9 19:17:13 sunrise dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 192.168.1.1 port 67
Feb  9 19:18:28 sunrise dhclient: last message repeated 4 times
Feb  9 19:19:32 sunrise dhclient: last message repeated 5 times
Feb  9 19:20:32 sunrise dhclient: last message repeated 5 times
Feb  9 19:21:32 sunrise dhclient: last message repeated 3 times
Feb  9 19:22:32 sunrise dhclient: last message repeated 4 times
Feb  9 19:23:32 sunrise dhclient: last message repeated 4 times


Which isn't going to work because if I do iwconfig it gives this:
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

But restarting networking gives this and works right away:

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1631
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:02:xx:xx:xx:xx
Sending on   LPF/wlan0/00:02:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:02:xx:xx:xx:xx
Sending on   LPF/wlan0/00:02:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 34713 seconds.
ssh stop/waiting
ssh start/running, process 12701

```
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"yo-fu"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 32:46:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/100  Signal level=40/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

So it's not simply dropping the ip address, it's dropping all the settings for no reason.

The adapter also hasn't shown a link quality more than around 40/100.  I googled the adapter and seems people have been having that particular issue since 9.04.  But the signal has to be strong, I get speeds near 1,600k/s.  Though that issues doesn't seem to have anything to do with it losing the networking settings

---

### Post by phazei on 2011-02-10
Any ideas, anyone?

---

### Post by phazei on 2011-02-14
b. b. b... ump?

---

### Post by phazei on 2011-02-15
find . | xargs grep wlan0
```
./daemon.log:Feb 14 20:35:52 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:35:52 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:35:52 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
./daemon.log:Feb 14 20:35:55 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
./daemon.log:Feb 14 20:35:59 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
./daemon.log:Feb 14 20:35:59 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./daemon.log:Feb 14 20:37:57 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:37:57 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:37:57 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./daemon.log:Feb 14 20:37:59 phazei ntpd[1010]: unable to create socket on wlan0 (4) for fe80::202:72ff:fe5c:4c9f#123
./daemon.log:Feb 14 20:38:00 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./daemon.log:Feb 14 20:38:01 phazei ntpd[1273]: Listening on interface #2 wlan0, fe80::202:72ff:fe5c:4c9f#123 Enabled
./daemon.log:Feb 14 20:38:01 phazei ntpd[1273]: Listening on interface #5 wlan0, 192.168.1.101#123 Enabled
./syslog:Feb 14 20:35:52 phazei kernel: [   11.364262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
./syslog:Feb 14 20:35:52 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:35:52 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:35:52 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
./syslog:Feb 14 20:35:53 phazei kernel: [   12.427841] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
./syslog:Feb 14 20:35:53 phazei kernel: [   12.628020] wlan0: authenticate with 32:46:9a:67:c5:63 (try 2)
./syslog:Feb 14 20:35:53 phazei kernel: [   12.633578] wlan0: authenticated
./syslog:Feb 14 20:35:53 phazei kernel: [   12.636468] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
./syslog:Feb 14 20:35:53 phazei kernel: [   12.641574] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
./syslog:Feb 14 20:35:53 phazei kernel: [   12.644509] wlan0: associated
./syslog:Feb 14 20:35:53 phazei kernel: [   12.648645] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
./syslog:Feb 14 20:35:55 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
./syslog:Feb 14 20:35:59 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
./syslog:Feb 14 20:35:59 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./syslog:Feb 14 20:36:04 phazei kernel: [   23.312016] wlan0: no IPv6 routers present
./syslog:Feb 14 20:37:57 phazei kernel: [   11.203483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
./syslog:Feb 14 20:37:57 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:37:57 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:37:57 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./syslog:Feb 14 20:37:58 phazei kernel: [   12.344047] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
./syslog:Feb 14 20:37:58 phazei kernel: [   12.345700] wlan0: authenticated
./syslog:Feb 14 20:37:58 phazei kernel: [   12.361377] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
./syslog:Feb 14 20:37:58 phazei kernel: [   12.377237] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
./syslog:Feb 14 20:37:58 phazei kernel: [   12.377246] wlan0: associated
./syslog:Feb 14 20:37:58 phazei kernel: [   12.378689] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
./syslog:Feb 14 20:37:59 phazei ntpd[1010]: unable to create socket on wlan0 (4) for fe80::202:72ff:fe5c:4c9f#123
./syslog:Feb 14 20:38:00 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./syslog:Feb 14 20:38:01 phazei ntpd[1273]: Listening on interface #2 wlan0, fe80::202:72ff:fe5c:4c9f#123 Enabled
./syslog:Feb 14 20:38:01 phazei ntpd[1273]: Listening on interface #5 wlan0, 192.168.1.101#123 Enabled
./syslog:Feb 14 20:38:08 phazei kernel: [   22.408010] wlan0: no IPv6 routers present
./syslog:Feb 15 01:45:02 phazei kernel: [18436.034799] wlan0: deauthenticated from 32:46:9a:67:c5:63 (Reason: 7)
./udev:KERNEL[1297744676.399971] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0 (net)
./udev:DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0
./udev:INTERFACE=wlan0
./udev:KERNEL[1297744676.400038] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0/queues/rx-0 (queues)
./udev:DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0/queues/rx-0
./udev:UDEV  [1297744676.502905] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0 (net)
./udev:DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0
./udev:INTERFACE=wlan0
./udev:UDEV  [1297744676.507060] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0/queues/rx-0 (queues)
./udev:DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/net/wlan0/queues/rx-0
./messages:Feb 14 20:35:52 phazei kernel: [   11.364262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
./messages:Feb 14 20:35:53 phazei kernel: [   12.648645] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
./messages:Feb 14 20:37:57 phazei kernel: [   11.203483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
./messages:Feb 14 20:37:58 phazei kernel: [   12.378689] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
./debug:Feb 14 20:35:53 phazei kernel: [   12.427841] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
./debug:Feb 14 20:35:53 phazei kernel: [   12.628020] wlan0: authenticate with 32:46:9a:67:c5:63 (try 2)
./debug:Feb 14 20:35:53 phazei kernel: [   12.633578] wlan0: authenticated
./debug:Feb 14 20:35:53 phazei kernel: [   12.636468] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
./debug:Feb 14 20:35:53 phazei kernel: [   12.641574] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
./debug:Feb 14 20:35:53 phazei kernel: [   12.644509] wlan0: associated
./debug:Feb 14 20:36:04 phazei kernel: [   23.312016] wlan0: no IPv6 routers present
./debug:Feb 14 20:37:58 phazei kernel: [   12.344047] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
./debug:Feb 14 20:37:58 phazei kernel: [   12.345700] wlan0: authenticated
./debug:Feb 14 20:37:58 phazei kernel: [   12.361377] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
./debug:Feb 14 20:37:58 phazei kernel: [   12.377237] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
./debug:Feb 14 20:37:58 phazei kernel: [   12.377246] wlan0: associated
./debug:Feb 14 20:38:08 phazei kernel: [   22.408010] wlan0: no IPv6 routers present
./debug:Feb 15 01:45:02 phazei kernel: [18436.034799] wlan0: deauthenticated from 32:46:9a:67:c5:63 (Reason: 7)
./kern.log:Feb 14 20:35:52 phazei kernel: [   11.364262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.427841] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.628020] wlan0: authenticate with 32:46:9a:67:c5:63 (try 2)
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.633578] wlan0: authenticated
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.636468] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.641574] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.644509] wlan0: associated
./kern.log:Feb 14 20:35:53 phazei kernel: [   12.648645] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
./kern.log:Feb 14 20:36:04 phazei kernel: [   23.312016] wlan0: no IPv6 routers present
./kern.log:Feb 14 20:37:57 phazei kernel: [   11.203483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
./kern.log:Feb 14 20:37:58 phazei kernel: [   12.344047] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
./kern.log:Feb 14 20:37:58 phazei kernel: [   12.345700] wlan0: authenticated
./kern.log:Feb 14 20:37:58 phazei kernel: [   12.361377] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
./kern.log:Feb 14 20:37:58 phazei kernel: [   12.377237] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
./kern.log:Feb 14 20:37:58 phazei kernel: [   12.377246] wlan0: associated
./kern.log:Feb 14 20:37:58 phazei kernel: [   12.378689] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
./kern.log:Feb 14 20:38:08 phazei kernel: [   22.408010] wlan0: no IPv6 routers present
./kern.log:Feb 15 01:45:02 phazei kernel: [18436.034799] wlan0: deauthenticated from 32:46:9a:67:c5:63 (Reason: 7)
./dmesg:[   11.203483] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

find . | xargs grep dhclient
```
./daemon.log:Feb 14 20:35:50 phazei dhclient: Internet Systems Consortium DHCP Client V3.1.3
./daemon.log:Feb 14 20:35:50 phazei dhclient: Copyright 2004-2009 Internet Systems Consortium.
./daemon.log:Feb 14 20:35:50 phazei dhclient: All rights reserved.
./daemon.log:Feb 14 20:35:50 phazei dhclient: For info, please visit https://www.isc.org/software/dhcp/
./daemon.log:Feb 14 20:35:50 phazei dhclient:
./daemon.log:Feb 14 20:35:52 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:35:52 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:35:52 phazei dhclient: Sending on   Socket/fallback
./daemon.log:Feb 14 20:35:52 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
./daemon.log:Feb 14 20:35:55 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
./daemon.log:Feb 14 20:35:59 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
./daemon.log:Feb 14 20:35:59 phazei dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
./daemon.log:Feb 14 20:35:59 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./daemon.log:Feb 14 20:35:59 phazei dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
./daemon.log:Feb 14 20:35:59 phazei dhclient: bound to 192.168.1.101 -- renewal in 38086 seconds.
./daemon.log:Feb 14 20:37:56 phazei dhclient: Internet Systems Consortium DHCP Client V3.1.3
./daemon.log:Feb 14 20:37:56 phazei dhclient: Copyright 2004-2009 Internet Systems Consortium.
./daemon.log:Feb 14 20:37:56 phazei dhclient: All rights reserved.
./daemon.log:Feb 14 20:37:56 phazei dhclient: For info, please visit https://www.isc.org/software/dhcp/
./daemon.log:Feb 14 20:37:56 phazei dhclient:
./daemon.log:Feb 14 20:37:57 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:37:57 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./daemon.log:Feb 14 20:37:57 phazei dhclient: Sending on   Socket/fallback
./daemon.log:Feb 14 20:37:57 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./daemon.log:Feb 14 20:38:00 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./daemon.log:Feb 14 20:38:00 phazei dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
./daemon.log:Feb 14 20:38:00 phazei dhclient: bound to 192.168.1.101 -- renewal in 38778 seconds.
./syslog:Feb 14 20:35:50 phazei dhclient: Internet Systems Consortium DHCP Client V3.1.3
./syslog:Feb 14 20:35:50 phazei dhclient: Copyright 2004-2009 Internet Systems Consortium.
./syslog:Feb 14 20:35:50 phazei dhclient: All rights reserved.
./syslog:Feb 14 20:35:50 phazei dhclient: For info, please visit https://www.isc.org/software/dhcp/
./syslog:Feb 14 20:35:50 phazei dhclient:
./syslog:Feb 14 20:35:52 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:35:52 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:35:52 phazei dhclient: Sending on   Socket/fallback
./syslog:Feb 14 20:35:52 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
./syslog:Feb 14 20:35:55 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
./syslog:Feb 14 20:35:59 phazei dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
./syslog:Feb 14 20:35:59 phazei dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
./syslog:Feb 14 20:35:59 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./syslog:Feb 14 20:35:59 phazei dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
./syslog:Feb 14 20:35:59 phazei kernel: [   18.241006] Pid: 915, comm: dhclient-script Tainted: G      D     2.6.35-25-generic-pae #44-Ubuntu D865GLC                        /MIDWAY
./syslog:Feb 14 20:35:59 phazei kernel: [   18.241006] Process dhclient-script (pid: 915, ti=f5066000 task=f51d4c20 task.ti=f5066000)
./syslog:Feb 14 20:35:59 phazei dhclient: bound to 192.168.1.101 -- renewal in 38086 seconds.
./syslog:Feb 14 20:35:59 phazei kernel: [   18.353504] Pid: 787, comm: dhclient3 Tainted: G      D     2.6.35-25-generic-pae #44-Ubuntu D865GLC                        /MIDWAY
./syslog:Feb 14 20:35:59 phazei kernel: [   18.353504] Process dhclient3 (pid: 787, ti=f53da000 task=f55b6580 task.ti=f53da000)
./syslog:Feb 14 20:37:56 phazei dhclient: Internet Systems Consortium DHCP Client V3.1.3
./syslog:Feb 14 20:37:56 phazei dhclient: Copyright 2004-2009 Internet Systems Consortium.
./syslog:Feb 14 20:37:56 phazei dhclient: All rights reserved.
./syslog:Feb 14 20:37:56 phazei dhclient: For info, please visit https://www.isc.org/software/dhcp/
./syslog:Feb 14 20:37:56 phazei dhclient:
./syslog:Feb 14 20:37:57 phazei dhclient: Listening on LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:37:57 phazei dhclient: Sending on   LPF/wlan0/00:02:72:5c:4c:9f
./syslog:Feb 14 20:37:57 phazei dhclient: Sending on   Socket/fallback
./syslog:Feb 14 20:37:57 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./syslog:Feb 14 20:38:00 phazei dhclient: DHCPREQUEST of 192.168.1.101 on wlan0 to 255.255.255.255 port 67
./syslog:Feb 14 20:38:00 phazei dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
./syslog:Feb 14 20:38:00 phazei dhclient: bound to 192.168.1.101 -- renewal in 38778 seconds.
./messages:Feb 14 20:35:59 phazei kernel: [   18.241006] Pid: 915, comm: dhclient-script Tainted: G      D     2.6.35-25-generic-pae #44-Ubuntu D865GLC                        /MIDWAY
./messages:Feb 14 20:35:59 phazei kernel: [   18.353504] Pid: 787, comm: dhclient3 Tainted: G      D     2.6.35-25-generic-pae #44-Ubuntu D865GLC                        /MIDWAY
./kern.log:Feb 14 20:35:59 phazei kernel: [   18.241006] Pid: 915, comm: dhclient-script Tainted: G      D     2.6.35-25-generic-pae #44-Ubuntu D865GLC                        /MIDWAY
./kern.log:Feb 14 20:35:59 phazei kernel: [   18.241006] Process dhclient-script (pid: 915, ti=f5066000 task=f51d4c20 task.ti=f5066000)
./kern.log:Feb 14 20:35:59 phazei kernel: [   18.353504] Pid: 787, comm: dhclient3 Tainted: G      D     2.6.35-25-generic-pae #44-Ubuntu D865GLC                        /MIDWAY
./kern.log:Feb 14 20:35:59 phazei kernel: [   18.353504] Process dhclient3 (pid: 787, ti=f53da000 task=f55b6580 task.ti=f53da000)

```

Anything in that that suggests anything?  I cleared all the logs, rebooted, and waited for the issue to occur; I took those logs when the connection was down.  
networking restart fixes it.
Here's "dmesg | grep wlan0" after restarting networking while it's working:
```

[   12.344047] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
[   12.345700] wlan0: authenticated
[   12.361377] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
[   12.377237] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
[   12.377246] wlan0: associated
[   12.378689] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.408010] wlan0: no IPv6 routers present
[18436.034799] wlan0: deauthenticated from 32:46:9a:67:c5:63 (Reason: 7)
[21067.464528] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21068.511906] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
[21068.514132] wlan0: authenticated
[21068.514164] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
[21068.516266] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
[21068.516274] wlan0: associated
[21068.517164] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21078.720009] wlan0: no IPv6 routers present

```
And the entire dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-25-generic-pae (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 (Ubuntu 2.6.35-25.44-generic-pae 2.6.35.10)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ef30000 (usable)
[    0.000000]  BIOS-e820: 000000003ef30000 - 000000003ef40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ef40000 - 000000003eff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003eff0000 - 000000003f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ef30 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003ef30000 (usable)
[    0.000000]  modified: 000000003ef30000 - 000000003ef40000 (ACPI data)
[    0.000000]  modified: 000000003ef40000 - 000000003eff0000 (ACPI NVS)
[    0.000000]  modified: 000000003eff0000 - 000000003f000000 (reserved)
[    0.000000]  modified: 00000000fecf0000 - 00000000fecf1000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 2e968000 - 2f3a4000
[    0.000000] ACPI: RSDP 000f5a20 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ef30000 00034 (v01 GATEWA N2DTM019 20030801 MSFT 00000097)
[    0.000000] ACPI: FACP 3ef30200 00081 (v02 GATEWA N2DTM019 20030801 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ef30370 04161 (v01 GATEWA N2DTM019 00000001 MSFT 0100000D)
[    0.000000] ACPI: FACS 3ef40000 00040
[    0.000000] ACPI: APIC 3ef30300 00068 (v01 GATEWA N2DTM019 20030801 MSFT 00000097)
[    0.000000] ACPI: ASF! 3ef344e0 00099 (v16 LEGEND I865PASF 00000001 MSFT 0100000D)
[    0.000000] ACPI: WDDT 3ef34579 00040 (v01 INTEL  OEMWDDT  00000001 MSFT 0100000D)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 115MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003ef30
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ef30
[    0.000000] On node 0 totalpages: 257728
[    0.000000] free_area_init_node: node 0, pgdat c083ecc0, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 231 pages used for memmap
[    0.000000]   HighMem zone: 29259 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f000000 (gap: 3f000000:bfcf0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1800000 s39872 r0 d21568 u1048576
[    0.000000] pcpu-alloc: s39872 r0 d21568 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 255713
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=26c94650-0f6b-4d25-b89e-d8b3b7bd1287 ro quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5156780 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (48 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009fb65c]   TEXT DATA BSS
[    0.000000]   #3 [002e968000 - 002f3a4000]         RAMDISK
[    0.000000]   #4 [00009fc000 - 0000a03268]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000fc2c0]   BIOS reserved
[    0.000000]   #8 [00000fc400 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fc2c0 - 00000fc400]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 00017e1000]         BOOTMEM
[    0.000000]   #15 [00017e1000 - 00017e1004]         BOOTMEM
[    0.000000]   #16 [00017e1040 - 00017e1100]         BOOTMEM
[    0.000000]   #17 [00017e1100 - 00017e11a8]         BOOTMEM
[    0.000000]   #18 [00017e11c0 - 00017e41c0]         BOOTMEM
[    0.000000]   #19 [00017e41c0 - 00017e41d8]         BOOTMEM
[    0.000000]   #20 [00017e4200 - 00017e4800]         BOOTMEM
[    0.000000]   #21 [00017e4800 - 00017e482f]         BOOTMEM
[    0.000000]   #22 [00017e4840 - 00017e49f0]         BOOTMEM
[    0.000000]   #23 [00017e4a00 - 00017e4a40]         BOOTMEM
[    0.000000]   #24 [00017e4a40 - 00017e4a80]         BOOTMEM
[    0.000000]   #25 [00017e4a80 - 00017e4ac0]         BOOTMEM
[    0.000000]   #26 [00017e4ac0 - 00017e4b00]         BOOTMEM
[    0.000000]   #27 [00017e4b00 - 00017e4b40]         BOOTMEM
[    0.000000]   #28 [00017e4b40 - 00017e4b80]         BOOTMEM
[    0.000000]   #29 [00017e4b80 - 00017e4bc0]         BOOTMEM
[    0.000000]   #30 [00017e4bc0 - 00017e4c00]         BOOTMEM
[    0.000000]   #31 [00017e4c00 - 00017e4c40]         BOOTMEM
[    0.000000]   #32 [00017e4c40 - 00017e4c50]         BOOTMEM
[    0.000000]   #33 [00017e4c80 - 00017e4c90]         BOOTMEM
[    0.000000]   #34 [00017e4cc0 - 00017e4d27]         BOOTMEM
[    0.000000]   #35 [00017e4d40 - 00017e4da7]         BOOTMEM
[    0.000000]   #36 [0001800000 - 000180f000]         BOOTMEM
[    0.000000]   #37 [0001900000 - 000190f000]         BOOTMEM
[    0.000000]   #38 [00017e6dc0 - 00017e6dc4]         BOOTMEM
[    0.000000]   #39 [00017e6e00 - 00017e6e04]         BOOTMEM
[    0.000000]   #40 [00017e6e40 - 00017e6e48]         BOOTMEM
[    0.000000]   #41 [00017e6e80 - 00017e6e88]         BOOTMEM
[    0.000000]   #42 [00017e6ec0 - 00017e6f60]         BOOTMEM
[    0.000000]   #43 [00017e6f80 - 00017e6fc8]         BOOTMEM
[    0.000000]   #44 [00017e7000 - 00017eb000]         BOOTMEM
[    0.000000]   #45 [000180f000 - 000188f000]         BOOTMEM
[    0.000000]   #46 [000188f000 - 00018cf000]         BOOTMEM
[    0.000000]   #47 [000190f000 - 0001df9fac]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003ef30)
[    0.000000] Memory: 997144k/1031360k available (5090k kernel code, 33768k reserved, 2427k data, 708k init, 117960k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc0858000 - 0xc0909000   ( 708 kB)
[    0.000000]       .data : 0xc05f8a1a - 0xc0857908   (2427 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f8a1a   (5090 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2393.589 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4787.17 BogoMIPS (lpj=9574356)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004042] Security Framework initialized
[    0.004070] AppArmor: AppArmor initialized
[    0.004074] Yama: becoming mindful.
[    0.004157] Mount-cache hash table entries: 512
[    0.004353] Initializing cgroup subsys ns
[    0.004361] Initializing cgroup subsys cpuacct
[    0.004369] Initializing cgroup subsys memory
[    0.004385] Initializing cgroup subsys devices
[    0.004390] Initializing cgroup subsys freezer
[    0.004395] Initializing cgroup subsys net_cls
[    0.004437] CPU: Physical Processor ID: 0
[    0.004441] CPU: Processor Core ID: 0
[    0.004447] mce: CPU supports 4 MCE banks
[    0.004461] CPU0: Thermal monitoring enabled (TM1)
[    0.004473] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.004484] ... version:                0
[    0.004488] ... bit width:              40
[    0.004493] ... generic registers:      18
[    0.004497] ... value mask:             000000ffffffffff
[    0.004502] ... max period:             0000007fffffffff
[    0.004506] ... fixed-purpose events:   0
[    0.004510] ... event mask:             000000000003ffff
[    0.009602] ACPI: Core revision 20100428
[    0.017376] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.017383] ftrace: allocating 22392 entries in 44 pages
[    0.020084] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020392] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061359] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
[    0.064000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.152026] Brought up 2 CPUs
[    0.152034] Total of 2 processors activated (9575.56 BogoMIPS).
[    0.152368] devtmpfs: initialized
[    0.153720] regulator: core version 0.5
[    0.153747] Time:  4:37:46  Date: 02/15/11
[    0.153814] NET: Registered protocol family 16
[    0.153867] Trying to unpack rootfs image as initramfs...
[    0.154125] EISA bus registered
[    0.154145] ACPI: bus type pci registered
[    0.156857] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.156863] PCI: Using configuration type 1 for base access
[    0.159575] bio: create slab <bio-0> at 0
[    0.162674] ACPI: EC: Look up EC in DSDT
[    0.166067] ACPI: Executed 3 blocks of module-level executable AML code
[    0.175759] ACPI: Interpreter enabled
[    0.175775] ACPI: (supports S0 S1 S3 S4 S5)
[    0.175837] ACPI: Using IOAPIC for interrupt routing
[    0.191463] ACPI: Power Resource [URP1] (off)
[    0.191536] ACPI: Power Resource [FDDP] (off)
[    0.191603] ACPI: Power Resource [LPTP] (off)
[    0.192066] ACPI: No dock devices found.
[    0.192079] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.192327] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.192820] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.192829] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.192837] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.192845] pci_root PNP0A03:00: host bridge window [mem 0x3f000000-0xffffffff] (ignored)
[    0.192871] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.192888] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.192979] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
[    0.192991] pci 0000:00:02.0: reg 14: [mem 0xffa80000-0xffafffff]
[    0.193003] pci 0000:00:02.0: reg 18: [io  0xec00-0xec07]
[    0.193081] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.193208] pci 0000:00:1d.0: reg 20: [io  0xc400-0xc41f]
[    0.193283] pci 0000:00:1d.1: reg 20: [io  0xc800-0xc81f]
[    0.193358] pci 0000:00:1d.2: reg 20: [io  0xcc00-0xcc1f]
[    0.193433] pci 0000:00:1d.3: reg 20: [io  0xd000-0xd01f]
[    0.193508] pci 0000:00:1d.7: reg 10: [mem 0xffa7f400-0xffa7f7ff]
[    0.193586] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.193597] pci 0000:00:1d.7: PME# disabled
[    0.193720] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.193733] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH4 ACPI/GPIO/TCO
[    0.193744] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH4 GPIO
[    0.193780] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.193793] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.193806] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.193819] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.193832] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.193846] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.193892] pci 0000:00:1f.2: reg 10: [io  0xe800-0xe807]
[    0.193905] pci 0000:00:1f.2: reg 14: [io  0xe400-0xe403]
[    0.193917] pci 0000:00:1f.2: reg 18: [io  0xe000-0xe007]
[    0.193930] pci 0000:00:1f.2: reg 1c: [io  0xdc00-0xdc03]
[    0.193942] pci 0000:00:1f.2: reg 20: [io  0xd800-0xd80f]
[    0.194016] pci 0000:00:1f.3: reg 20: [io  0xd400-0xd41f]
[    0.194088] pci 0000:00:1f.5: reg 18: [mem 0xffa7fc00-0xffa7fdff]
[    0.194101] pci 0000:00:1f.5: reg 1c: [mem 0xffa7f800-0xffa7f8ff]
[    0.194146] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.194155] pci 0000:00:1f.5: PME# disabled
[    0.194223] pci 0000:01:01.0: reg 10: [io  0xb800-0xb83f]
[    0.194290] pci 0000:01:01.0: supports D1 D2
[    0.194338] pci 0000:01:01.2: reg 10: [mem 0xff8fe800-0xff8fefff]
[    0.194352] pci 0000:01:01.2: reg 14: [mem 0xff8f8000-0xff8fbfff]
[    0.194409] pci 0000:01:01.2: supports D1 D2
[    0.194416] pci 0000:01:01.2: PME# supported from D0 D1 D2 D3hot
[    0.194425] pci 0000:01:01.2: PME# disabled
[    0.194485] pci 0000:01:08.0: reg 10: [mem 0xff8ff000-0xff8fffff]
[    0.194498] pci 0000:01:08.0: reg 14: [io  0xbc00-0xbc3f]
[    0.194552] pci 0000:01:08.0: supports D1 D2
[    0.194558] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194567] pci 0000:01:08.0: PME# disabled
[    0.194618] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.194628] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.194639] pci 0000:00:1e.0:   bridge window [mem 0xff800000-0xff8fffff]
[    0.194649] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.194657] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.194665] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[    0.194683] pci_bus 0000:00: on NUMA node 0
[    0.194697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.194916] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.202488] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.202771] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.203059] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.203332] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.203819] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.204133] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.204405] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.204693] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.204835] HEST: Table is not found!
[    0.205010] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.205046] vgaarb: loaded
[    0.205454] SCSI subsystem initialized
[    0.205618] libata version 3.00 loaded.
[    0.205745] usbcore: registered new interface driver usbfs
[    0.205779] usbcore: registered new interface driver hub
[    0.205839] usbcore: registered new device driver usb
[    0.206180] ACPI: WMI: Mapper loaded
[    0.206187] PCI: Using ACPI for IRQ routing
[    0.206198] PCI: pci_cache_line_size set to 64 bytes
[    0.206358] reserve RAM buffer: 0000000000002000 - 000000000000ffff
[    0.206366] reserve RAM buffer: 000000000009fc00 - 000000000009ffff
[    0.206373] reserve RAM buffer: 000000003ef30000 - 000000003fffffff
[    0.206599] NetLabel: Initializing
[    0.206605] NetLabel:  domain hash size = 128
[    0.206610] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.206638] NetLabel:  unlabeled traffic allowed by default
[    0.206828] hpet clockevent registered
[    0.206835] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.206845] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.206859] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.216064] Switching to clocksource tsc
[    0.242883] AppArmor: AppArmor Filesystem Enabled
[    0.242912] pnp: PnP ACPI init
[    0.242953] ACPI: bus type pnp registered
[    0.250277] pnp: PnP ACPI: found 11 devices
[    0.250284] ACPI: ACPI bus type pnp unregistered
[    0.250294] PnPBIOS: Disabled by ACPI PNP
[    0.250327] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.250344] system 00:09: [io  0x0400-0x047f] has been reserved
[    0.250353] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.250361] system 00:09: [io  0x0500-0x053f] has been reserved
[    0.250372] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.250381] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.250389] system 00:09: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.250406] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.250415] system 00:0a: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.250424] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.250433] system 00:0a: [mem 0x00100000-0x3effffff] could not be reserved
[    0.289401] pci 0000:00:1f.1: BAR 5: assigned [mem 0x40000000-0x400003ff]
[    0.289416] pci 0000:00:1f.1: BAR 5: set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff]
[    0.289425] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.289435] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.289447] pci 0000:00:1e.0:   bridge window [mem 0xff800000-0xff8fffff]
[    0.289456] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.289481] pci 0000:00:1e.0: setting latency timer to 64
[    0.289492] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.289499] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    0.289507] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.289515] pci_bus 0000:01: resource 1 [mem 0xff800000-0xff8fffff]
[    0.289521] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.289528] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    0.289607] NET: Registered protocol family 2
[    0.289760] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.290384] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.291170] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.291707] TCP: Hash tables configured (established 131072 bind 65536)
[    0.291715] TCP reno registered
[    0.291726] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.291746] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.291945] NET: Registered protocol family 1
[    0.291981] pci 0000:00:02.0: Boot video device
[    0.292155] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.292168] PCI: CLS 32 bytes, default 64
[    0.292438] cpufreq-nforce2: No nForce2 chipset.
[    0.292513] Scanning for low memory corruption every 60 seconds
[    0.292798] audit: initializing netlink socket (disabled)
[    0.292819] type=2000 audit(1297744666.288:1): initialized
[    0.308243] highmem bounce pool size: 64 pages
[    0.308257] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.311853] VFS: Disk quotas dquot_6.5.2
[    0.312013] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.313522] fuse init (API version 7.14)
[    0.313742] msgmni has been set to 1717
[    0.314654] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.314663] io scheduler noop registered
[    0.314668] io scheduler deadline registered
[    0.314702] io scheduler cfq registered (default)
[    0.315003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.315059] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.315553] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.315572] ACPI: Sleep Button [SLPB]
[    0.315685] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.315695] ACPI: Power Button [PWRF]
[    0.316017] ACPI: acpi_idle registered with cpuidle
[    0.319641] ERST: Table is not found!
[    0.320018] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.320172] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.320790] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.323956] brd: module loaded
[    0.325392] loop: module loaded
[    0.325940] ata_piix 0000:00:1f.1: version 2.13
[    0.325961] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.325975]   alloc irq_desc for 18 on node -1
[    0.325981]   alloc kstat_irqs on node -1
[    0.325996] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.326067] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.326199] isapnp: Scanning for PnP cards...
[    0.375336] scsi0 : ata_piix
[    0.419158] scsi1 : ata_piix
[    0.422630] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.422641] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.422718] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.422729] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.422809] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.447364] scsi2 : ata_piix
[    0.455307] scsi3 : ata_piix
[    0.457179] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 18
[    0.457187] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 18
[    0.457989] Fixed MDIO Bus: probed
[    0.458073] PPP generic driver version 2.4.2
[    0.458187] tun: Universal TUN/TAP device driver, 1.6
[    0.458192] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.458401] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.458442]   alloc irq_desc for 23 on node -1
[    0.458447]   alloc kstat_irqs on node -1
[    0.458460] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.458489] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.458496] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.458573] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.458614] ehci_hcd 0000:00:1d.7: debug port 1
[    0.462494] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.462526] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa7f400
[    0.487522] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.487825] hub 1-0:1.0: USB hub found
[    0.487836] hub 1-0:1.0: 8 ports detected
[    0.488015] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.488052] uhci_hcd: USB Universal Host Controller Interface driver
[    0.488116]   alloc irq_desc for 16 on node -1
[    0.488121]   alloc kstat_irqs on node -1
[    0.488134] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.488149] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.488156] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.488237] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.488287] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c400
[    0.488542] hub 2-0:1.0: USB hub found
[    0.488552] hub 2-0:1.0: 2 ports detected
[    0.488679]   alloc irq_desc for 19 on node -1
[    0.488684]   alloc kstat_irqs on node -1
[    0.488695] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.488707] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.488714] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.488795] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.488840] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    0.489093] hub 3-0:1.0: USB hub found
[    0.489103] hub 3-0:1.0: 2 ports detected
[    0.489248] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.489259] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.489266] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.489341] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.489371] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000cc00
[    0.489618] hub 4-0:1.0: USB hub found
[    0.489628] hub 4-0:1.0: 2 ports detected
[    0.489748] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.489759] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.489765] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.489839] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.489869] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d000
[    0.490115] hub 5-0:1.0: USB hub found
[    0.490125] hub 5-0:1.0: 2 ports detected
[    0.490380] PNP: No PS/2 controller found. Probing ports directly.
[    0.500552] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.500570] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.500740] mice: PS/2 mouse device common for all mice
[    0.500968] rtc_cmos 00:02: RTC can wake from S4
[    0.501055] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.501087] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.501323] device-mapper: uevent: version 1.0.3
[    0.501547] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.597714] device-mapper: multipath: version 1.1.1 loaded
[    0.597724] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.641557] EISA: Probing bus 0 at eisa.0
[    0.641615] EISA: Detected 0 cards.
[    0.648575] Freeing initrd memory: 10480k freed
[    0.658819] cpuidle: using governor ladder
[    0.658826] cpuidle: using governor menu
[    0.659614] TCP cubic registered
[    0.659908] NET: Registered protocol family 10
[    0.660777] lo: Disabled Privacy Extensions
[    0.661364] NET: Registered protocol family 17
[    0.661459] Using IPI No-Shortcut mode
[    0.661654] PM: Resume from disk failed.
[    0.661685] registered taskstats version 1
[    0.661982]   Magic number: 15:104:616
[    0.662087] rtc_cmos 00:02: setting system clock to 2011-02-15 04:37:46 UTC (1297744666)
[    0.662094] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.662099] EDD information not available.
[    0.662233] ata1.00: ATA-7: Maxtor 6L100P0, BAJ41G20, max UDMA/133
[    0.662240] ata1.00: 195813072 sectors, multi 16: LBA
[    0.662303] ata1.01: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB04, max UDMA/33
[    0.677038] ata1.00: configured for UDMA/100
[    0.685274] isapnp: No Plug & Play device found
[    0.691545] ata1.01: configured for UDMA/33
[    0.692811] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L100P0   BAJ4 PQ: 0 ANSI: 5
[    0.693054] sd 0:0:0:0: [sda] 195813072 512-byte logical blocks: (100 GB/93.3 GiB)
[    0.693143] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.693209] sd 0:0:0:0: [sda] Write Protect is off
[    0.693217] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.693286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.694236] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB04 PQ: 0 ANSI: 5
[    0.701322] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.701330] Uniform CD-ROM driver Revision: 3.20
[    0.701419]  sda:
[    0.701556] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    0.701663] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.718151]  sda1 sda2
[    0.735433] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.766170] Freeing unused kernel memory: 708k freed
[    0.766985] Write protecting the kernel text: 5092k
[    0.767150] Write protecting the kernel read-only data: 2012k
[    0.803365] udev[83]: starting version 163
[    0.919590] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.093717]   alloc irq_desc for 21 on node -1
[    1.093726]   alloc kstat_irqs on node -1
[    1.093742] firewire_ohci 0000:01:01.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.113723] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.113730] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.148547] firewire_ohci: Added fw-ohci device 0000:01:01.2, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x0
[    1.148637]   alloc irq_desc for 20 on node -1
[    1.148644]   alloc kstat_irqs on node -1
[    1.148659] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.166607] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.166617] EXT4-fs (sda1): write access will be enabled during recovery
[    1.172843] e100 0000:01:08.0: PME# disabled
[    1.174018] e100 0000:01:08.0: eth0: addr 0xff8ff000, irq 20, MAC addr 00:07:e9:48:d9:42
[    1.208258] EXT4-fs (sda1): orphan cleanup on readonly fs
[    1.208272] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179775
[    1.208323] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179774
[    1.208342] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179772
[    1.208361] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179771
[    1.208381] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1179770
[    1.208398] EXT4-fs (sda1): 5 orphan inodes deleted
[    1.208405] EXT4-fs (sda1): recovery complete
[    1.284029] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.436991] hub 3-2:1.0: USB hub found
[    1.438905] hub 3-2:1.0: 4 ports detected
[    1.640207] firewire_core: created device fw0: GUID 00023c00f100ca30, S400
[    1.725901] usb 3-2.2: new full speed USB device using uhci_hcd and address 3
[    1.745078] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.965910] usb 3-2.3: new low speed USB device using uhci_hcd and address 4
[    8.769313] Adding 2996116k swap on /dev/sda2.  Priority:-1 extents:1 across:2996116k
[    8.813981] udev[294]: starting version 163
[    9.024214] Intel 82802 RNG detected
[    9.029323] lp: driver loaded but no devices found
[    9.088929] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.220851] Linux agpgart interface v0.103
[    9.247993] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.429504] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    9.429993] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[    9.485652] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    9.683619] parport_pc 00:06: reported by Plug and Play ACPI
[    9.683679] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.716583] usbcore: registered new interface driver hiddev
[    9.720425] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input2
[    9.720637] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[    9.727082] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input3
[    9.727450] generic-usb 0003:046D:C52B.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[    9.750234] generic-usb 0003:046D:C52B.0003: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[    9.754068] usbcore: registered new interface driver usbhid
[    9.754074] usbhid: USB HID core driver
[    9.784606] ppdev: user-space parallel port driver
[    9.788431] lp0: using parport0 (interrupt-driven).
[    9.823111] cfg80211: Calling CRDA to update world regulatory domain
[    9.850803] input: Microsoft NaturalÂ® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.3/3-2.3:1.0/input/input4
[    9.852527] microsoft 0003:045E:00DB.0004: input,hidraw3: USB HID v1.11 Keyboard [Microsoft NaturalÂ® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-2.3/input0
[    9.880674] input: Microsoft NaturalÂ® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.3/3-2.3:1.1/input/input5
[    9.881138] microsoft 0003:045E:00DB.0005: input,hidraw4: USB HID v1.11 Device [Microsoft NaturalÂ® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-2.3/input1
[    9.895728] input: Microsoft NaturalÂ® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.3/3-2.3:1.2/input/input6
[    9.896075] microsoft 0003:045E:00DB.0006: input,hidraw5: USB HID v1.10 Mouse [Microsoft NaturalÂ® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-2.3/input2
[    9.940227] cfg80211: World regulatory domain updated:
[    9.940235]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.940243]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.940250]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.940258]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.940265]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.940272]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.017399] [drm] Initialized drm 1.1.0 20060810
[   10.238545] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.238557] i915 0000:00:02.0: setting latency timer to 64
[   10.241347] usb 1-5: reset high speed USB device using ehci_hcd and address 3
[   10.347859] [drm] set up 15M of stolen space
[   10.474550] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.475199]   alloc irq_desc for 22 on node -1
[   10.475205]   alloc kstat_irqs on node -1
[   10.475231] EMU10K1_Audigy 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.475279] [drm] initialized overlay support
[   10.478931] Installing spdif_bug patch: SB Audigy 2 [Unknown]
[   10.559921] phy0: Selected rate control algorithm 'minstrel'
[   10.561532] zd1211rw 1-5:1.0: phy0
[   10.561588] usbcore: registered new interface driver zd1211rw
[   10.827663] Console: switching to colour frame buffer device 210x65
[   10.835805] fb0: inteldrmfb frame buffer device
[   10.835810] drm: registered panic notifier
[   10.835820] Slow work thread pool: Starting up
[   10.835982] Slow work thread pool: Ready
[   10.836035] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.836688]   alloc irq_desc for 17 on node -1
[   10.836697]   alloc kstat_irqs on node -1
[   10.836716] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.836785] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   11.123553] zd1211rw 1-5:1.0: firmware version 4725
[   11.163605] zd1211rw 1-5:1.0: zd1211b chip 0ace:1215 v4810 high 00-02-72 AL2230_RF pa0 g--NS
[   11.168506] cfg80211: Calling CRDA for country: US
[   11.190041] cfg80211: Regulatory domain changed to country: US
[   11.190050]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.190058]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   11.190068]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   11.190078]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.190086]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.190096]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.190105]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   11.203483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.264057] intel8x0_measure_ac97_clock: measured 53656 usecs (2585 samples)
[   11.264066] intel8x0: clocking to 48000
[   12.344047] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
[   12.345700] wlan0: authenticated
[   12.361377] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
[   12.377237] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
[   12.377246] wlan0: associated
[   12.378689] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.143663] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.408010] wlan0: no IPv6 routers present
[   55.872292] usb 3-2.2: USB disconnect, address 3
[   91.418643] usb 3-2.2: new full speed USB device using uhci_hcd and address 5
[   91.573994] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input7
[   91.574272] generic-usb 0003:046D:C52B.0007: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[   91.578998] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input8
[   91.579527] generic-usb 0003:046D:C52B.0008: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[   91.594943] generic-usb 0003:046D:C52B.0009: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[  283.821884] usb 3-2.2: USB disconnect, address 5
[  323.189427] usb 3-2.2: new full speed USB device using uhci_hcd and address 6
[  323.346000] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input9
[  323.346295] generic-usb 0003:046D:C52B.000A: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[  323.351720] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input10
[  323.352269] generic-usb 0003:046D:C52B.000B: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[  323.366442] generic-usb 0003:046D:C52B.000C: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[  370.675959] render error detected, EIR: 0x00000010
[  370.675969] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[  370.675992] render error detected, EIR: 0x00000010
[  377.468931] lo: Disabled Privacy Extensions
[  427.033501] lo: Disabled Privacy Extensions
[  440.219267] xfce4-panel[2042]: segfault at d ip 00a9e11f sp bfed618c error 4 in libc-2.12.1.so[a2f000+157000]
[  446.712168] lo: Disabled Privacy Extensions
[  456.228663] xfce4-panel[2255]: segfault at d ip 00a6b11f sp bfd74528 error 4 in libc-2.12.1.so[9fc000+157000]
[  472.100216] lo: Disabled Privacy Extensions
[  819.879633] usb 3-2.2: USB disconnect, address 6
[  835.093528] lo: Disabled Privacy Extensions
[  845.170339] usb 3-2.2: new full speed USB device using uhci_hcd and address 7
[  845.323735] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input11
[  845.324042] generic-usb 0003:046D:C52B.000D: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[  845.330638] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input12
[  845.331182] generic-usb 0003:046D:C52B.000E: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[  845.347751] generic-usb 0003:046D:C52B.000F: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[  898.982709] usb 3-2.2: USB disconnect, address 7
[  913.163082] lo: Disabled Privacy Extensions
[  921.965263] usb 3-2.2: new full speed USB device using uhci_hcd and address 8
[  922.120392] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input13
[  922.123434] generic-usb 0003:046D:C52B.0010: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[  922.130691] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input14
[  922.133511] generic-usb 0003:046D:C52B.0011: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[  922.145773] generic-usb 0003:046D:C52B.0012: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[  940.194877] usb 3-2.2: USB disconnect, address 8
[  983.027067] lo: Disabled Privacy Extensions
[ 1105.353354] usb 3-2.2: new full speed USB device using uhci_hcd and address 9
[ 1105.507988] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input15
[ 1105.508784] generic-usb 0003:046D:C52B.0013: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[ 1105.515229] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input16
[ 1105.515769] generic-usb 0003:046D:C52B.0014: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[ 1105.524555] generic-usb 0003:046D:C52B.0015: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[ 1117.567184] usb 3-2.2: USB disconnect, address 9
[11234.424769] handle_rx_packet: invalid, small RX packet : 1
[11508.583332] handle_rx_packet: invalid, small RX packet : 1
[12053.369842] handle_rx_packet: invalid, small RX packet : 1
[12725.720862] handle_rx_packet: invalid, small RX packet : 1
[13198.384120] handle_rx_packet: invalid, small RX packet : 1
[13203.235510] handle_rx_packet: invalid, small RX packet : 1
[13259.181128] handle_rx_packet: invalid, small RX packet : 1
[13702.453599] handle_rx_packet: invalid, small RX packet : 1
[13731.429201] handle_rx_packet: invalid, small RX packet : 1
[13790.992976] handle_rx_packet: invalid, small RX packet : 1
[14238.468370] handle_rx_packet: invalid, small RX packet : 1
[14847.567852] handle_rx_packet: invalid, small RX packet : 1
[16208.801188] handle_rx_packet: invalid, small RX packet : 1
[16264.704938] handle_rx_packet: invalid, small RX packet : 1
[16562.909556] handle_rx_packet: invalid, small RX packet : 1
[17167.430225] handle_rx_packet: invalid, small RX packet : 1
[17333.558546] handle_rx_packet: invalid, small RX packet : 1
[17546.611510] handle_rx_packet: invalid, small RX packet : 1
[17564.361208] handle_rx_packet: invalid, small RX packet : 1
[17699.611184] handle_rx_packet: invalid, small RX packet : 1
[18436.034799] wlan0: deauthenticated from 32:46:9a:67:c5:63 (Reason: 7)
[18436.068057] cfg80211: All devices are disconnected, going to restore regulatory settings
[18436.068066] cfg80211: Restoring regulatory settings
[18436.068071] cfg80211: Calling CRDA to update world regulatory domain
[18436.075155] cfg80211: World regulatory domain updated:
[18436.075160]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[18436.075166]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18436.075170]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[18436.075175]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[18436.075180]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18436.075184]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[20393.389991] usb 3-2.2: new full speed USB device using uhci_hcd and address 10
[20393.549150] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input17
[20393.552310] generic-usb 0003:046D:C52B.0016: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[20393.559657] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input18
[20393.572470] generic-usb 0003:046D:C52B.0017: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[20393.587284] generic-usb 0003:046D:C52B.0018: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[20400.869076] usb 3-2.2: USB disconnect, address 10
[20583.701773] usb 3-2.2: new full speed USB device using uhci_hcd and address 11
[20583.861801] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.0/input/input19
[20583.864143] generic-usb 0003:046D:C52B.0019: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input0
[20583.872361] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2.2/3-2.2:1.1/input/input20
[20583.874572] generic-usb 0003:046D:C52B.001A: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input1
[20583.884847] generic-usb 0003:046D:C52B.001B: hiddev97,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2.2/input2
[21067.464528] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[21068.511906] wlan0: authenticate with 32:46:9a:67:c5:63 (try 1)
[21068.514132] wlan0: authenticated
[21068.514164] wlan0: associate with 32:46:9a:67:c5:63 (try 1)
[21068.516266] wlan0: RX AssocResp from 32:46:9a:67:c5:63 (capab=0x411 status=0 aid=1)
[21068.516274] wlan0: associated
[21068.517164] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[21078.720009] wlan0: no IPv6 routers present
[21084.039928] usb 3-2.2: USB disconnect, address 11

```
Oh and this is in my interfaces:
```

# ZyDAS zd1201 usb network adapter
auto wlan0
iface wlan0 inet dhcp
wireless-essid wtfyo
wireless-key 123456789X
wireless-mode managed
# post-up dhclient wlan0

```

The system is on a usb KVM until the kinks are worked out.  When I switch back and forth on the KVM it re-detects the usb keyboard and mouse each time.  Doubt that would interfere with the usb nic.

---

### Post by phazei on 2011-02-16
hi ):P ...

:|

:cry:

---

