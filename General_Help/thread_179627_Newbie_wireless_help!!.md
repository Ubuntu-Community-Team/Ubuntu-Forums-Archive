---
title: "Newbie wireless help!!"
date: 2006-05-20
forum: General Help
---

### Post by mr.digwell on 2006-05-20
hi
After a few problems installing I think i've got my wireless card in my laptop working, my windows laptop can ping my ubuntu laptop fine over the ad-hoc network, but ubuntu cannot connect to the windows machine. 
I am using wifiradar to scan for networks and at the bottom it comes up "connected to thecurryhouse **(ip 127.0.0.1)**" I cant use the gnome wireless applet as it brings up an error after login. does anyone know what the problem may be?

---

### Post by Ramses de Norre on 2006-05-20
IP 127.0.0.1 is the loopback connection a connection inside the os which links back to your own machine.

Can you ping the windows machine from ubuntu? What's the output of ```
iwconfig
ifconfig
```

---

### Post by mr.digwell on 2006-05-20
cant ping the windows box at all.

ah@TwirlyTop:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

Warning: Driver for device eth0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

eth0      IEEE 802.11g  ESSID:"TheCurryHouse"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:13:CE:00:02:4D
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=-21 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by mr.digwell on 2006-05-20
ah@TwirlyTop:/etc/init.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0E:35:E0:F5:E5
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:25807 (25.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8000 Memory:fceff000-fcefffff

eth1      Link encap:Ethernet  HWaddr 00:0E:7B:CF:B7:6E
          inet addr:192.168.0.53  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:7bff:fecf:b76e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9497812 (9.0 MiB)  TX bytes:867583 (847.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44299 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4028396 (3.8 MiB)  TX bytes:4028396 (3.8 MiB)

---

### Post by Ramses de Norre on 2006-05-20
Did you configure it properly? eth0 doesn't seem to have an IP adress, at which ip do you ping it from windows?
What's the content of /etc/network/interfaces?

---

### Post by mr.digwell on 2006-05-20
I think I have configured it properly, still very new to linux! from windows xp (192.168.1.10) i can ping ubuntu (192.168.1.20) fine. windows wzc finds & connects to network no problem.

/etc/network/interface:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
auto eth1
iface eth1 inet dhcp



auto eth0

iface eth0 inet static
wireless-essid TheCurryHouse
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.10

---

