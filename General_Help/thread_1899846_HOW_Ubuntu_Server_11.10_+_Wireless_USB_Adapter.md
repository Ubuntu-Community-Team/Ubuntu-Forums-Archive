---
title: "HOW? Ubuntu Server 11.10 + Wireless USB Adapter"
date: 2011-12-24
forum: General Help
---

### Post by micael3000 on 2011-12-24
Hello there,

I am just installing Ubuntu Server on my old desktop, in order to make some tests...
However, recently we moved the whole "wired system" to wireless, each computer having its USB adapter.
I am having trouble making Ubuntu Server 11.10 recognize and connect to the wireless network...

Does anyone know what I must do in order to get this working?
(I am not an expert, so, please use simple language and instructions) :(

Thanks in advance.

---

### Post by btindie on 2011-12-24
For servers your better of using a wired connection as it's far more reliable and there's more bandwidth available. But if you want to give a wireless connection ago...

Where information is requested below then please enclose it in CODE tags to make it more readable.

Boot the computer with the USB device disconnected, once it's booted plug it in and type
```
dmesg | tail
```and paste the result.

Also run the following and include the result
```
ifconfig -a | egrep -v ^\([\ ]\|\$\|lo\)
```You should have a wlan0, it may be called something else, if it's correctly detected the USB device.

---

### Post by micael3000 on 2011-12-24
Hello,

Yes, the device is detected (i checked its mac adress and its also correct)

dmesg | tail:
```
[    9.252044] drm: registered panic notifier
[    9.252053] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[    9.256189] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[    9.691824] type=1400 audit(1324762891.041:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=757 comm="apparmor_parser"
[    9.692309] type=1400 audit(1324762891.045:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=757 comm="apparmor_parser"
[    9.692604] type=1400 audit(1324762891.045:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=757 comm="apparmor_parser"
[    9.739488] type=1400 audit(1324762891.089:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=758 comm="apparmor_parser"
[    9.788257] init: failsafe main process (718) killed by TERM signal
[    9.789430] init: apport pre-start process (786) terminated with status 1
[    9.796734] init: apport post-stop process (805) terminated with status 1
```

ifconfig (...):
```
eth0      Link encap:Ethernet  HWaddr MAC_ADRESS_REMOVED
wlan0     Link encap:Ethernet  HWaddr MAC_ADRESS_REMOVED
```

I was trying this things:

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid MY_WIRELESS_NETWORK_NAME
sudo dhclient wlan0

But then it got stuck on dhclient (it never finishes and no logs are printed)... My wireless network runs on WPA2, and I don't know how can I point the password in order to it start working.

Thanks! :)

---

### Post by btindie on 2011-12-24
Well at least it's detected it...

All you need to do is the modify the system configuration file (/etc/network/interfaces) to configure the interface.

See
> man interfaces
man wireless
man ifupand [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) along with [http://blinker.net/2010/06/20/mac-mini-g4-homeserver-with-ubuntu-linux-10-04-wpa2/](http://blinker.net/2010/06/20/mac-mini-g4-homeserver-with-ubuntu-linux-10-04-wpa2/) for WPA2 configuration.

---

### Post by micael3000 on 2011-12-24
Hello,

Thanks! I did it all and yet things weren't working as I wish.
I am now using a wired connection instead of a wireless one.

I believe it doesn't worth trying anymore because wireless connection seems to be pretty unstable (and that is not acceptable for a server)...

Thank you for your help! :D

---

