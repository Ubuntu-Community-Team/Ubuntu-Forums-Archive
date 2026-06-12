---
title: "wifi setting problems with ipw2200 card"
date: 2006-03-28
forum: General Help
---

### Post by spastic_eye on 2006-03-28
hi all, this is my first post here but i've been using ubuntu quite a long time already, until i tried kubuntu (wich is my favourite distro now), getting everything configured unless wifi. so now i wanted to ask around for someone who had the same problem and got the wireless working. this post is just because i'm really desperate with my wifi...
so, my iwconfig output is:
```
eth1      radio off  ESSID:"HomeLab"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:D3:09:CB
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
everything is set right, but i can't turn the radio on. it says:
```
dami@valhalla:~$ sudo iwconfig eth1 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Operation not supported.
dami@valhalla:~$ sudo iwconfig eth1 power all
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Operation not permitted.

```
even in the kde network settings, if i switch to administrator mode and enable the eth1 device it immediately disables it by itself. in kwifimanager it is constantly powered off and if i set it to power on in administration mode nothing changes.
in kwifi radar i can start it just by root and it can't do anything. my wireless led on the notebook is also powered off and there isn't any power switch.
my last try was this script that i created:
```
#! /bin/sh
ifdown eth1
sleep 1
echo 'setting essid'
iwconfig eth1 essid "HomeLab"
echo 'Setting channel'
iwconfig eth1 channel 6
echo 'Setting mode'
iwconfig eth1 mode Managed
echo 'Setting ap'
iwconfig eth1 ap 00:0F:66:D3:09:CB
echo 'Setting rate'
iwconfig eth1 rate auto
echo 'Setting key s'
iwconfig eth1 key s:
echo 'Setting key open'
iwconfig eth1 key open
echo 'Setting txpower'
iwconfig eth1 txpower 14
echo 'Setting sense'
iwconfig eth1 sense 91
echo 'Setting power management'
iwconfig eth1 power all
echo 'iwconfig eth1 commit'
iwconfig eth1 commit
sleep 1
ifup eth1
echo 'Setting route'
route add default gw 192.168.1.1
```
and the output is:
```
dami@valhalla:~$ sudo sh /home/dami/Desktop/wifi.sh
ifdown: interface eth1 not configured
setting essid
Setting channel
Setting mode
Setting ap
Setting rate
Setting key s
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
Setting key open
Setting txpower
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Input/output error.
Setting sense
Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device eth1 ; Operation not supported.
Setting power management
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Operation not permitted.
iwconfig eth1 commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device eth1 ; Operation not supported.
There is already a pid file /var/run/dhclient.eth1.pid with pid 1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:15:00:3a:82:b6
Sending on   LPF/eth1/00:15:00:3a:82:b6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
```
my /etc/network/interfaces is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed

iface eth0 inet dhcp







auto eth1

```
please help me!

---

### Post by hizaguchi on 2006-03-31
KDE does that to me too, but it seems like it only happens when the card can't find a network.  For example, leaving ESSID set to "any" works fine everywhere but on my college campus, where I have to set the ESSID to "nomad" for the card to find the network.  So what I do is this:

```
sudo nano /etc/network/interfaces
```

Down below "wireless-mode managed" I have a line that says "wireless-essid any" in which I change "any" to "nomad" when I'm on campus.  Then:

```
sudo ifdown eth1
sudo ifup eth1
```

And it works perfectly.  Maybe the same will fix yours?

---

