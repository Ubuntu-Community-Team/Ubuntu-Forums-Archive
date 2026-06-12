---
title: "strategy for wireless connection"
date: 2006-03-29
forum: General Help
---

### Post by damu on 2006-03-29
Ok guys, I really need your help. 

We have 2 offices here which have been reorganised last week, and it's pretty messy right now with collegue in my desk so that he can use  a wired connection, sitting on the floor, and more and more grumppy... :???: 

Computers are all Ubuntu/kubuntu based.The modem router has been moved from one office to the other. It implies that a laptop with Kubuntu Hoary needs now to be wirelessly connected.  We don't use yet any wep or wap. Just unprotected dhcp...
The 3com usb dongle, a 3crusb10075, has been tested and installed succesfully from Hoary to Dapper by different Ubuntu users. Our dongle has been tested ok with Win XP
It seems my newbie level just doesn't allow me to sort this by myself...

My deadline to sort this out together was Monday evening. I since spent nearly all my time trying to sort this problem, reading threads, trying different ways...
The conclusion is that I just can't do it with your support,and that I am more and more out of schedule.

On this laptop, Firestarter and different files including etc/network/interfaces have been tweaked to allow  a connection on a previous configuration nearly a year ago. I will put a copy of this different files in that thread.
Another weird point is that the dongle is powered up with or without ndiswrapper drivers installed (the first led of the dongle is on all the time).

I think of 3 options to sort it out :

_1) on hoary, using ndiswrapper._
Following the ndiswrapper wiki, I manage to install the driver,but when I  tail /var/log/messages

I get

> mamta@do:~$ tail /var/log/messages
Mar 29 09:54:25 localhost kernel: Inbound IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:                     11:d8:a9:be:be:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x10 PREC=0x00                      TTL=64 ID=0 PROTO=UDP SPT=68 DPT=67 LEN=308
Mar 29 10:09:13 localhost -- MARK --
Mar 29 10:29:13 localhost -- MARK --
Mar 29 10:49:13 localhost -- MARK --
Mar 29 10:49:42 localhost kernel: ndiswrapper version 1.0rc2 loaded (preempt=yes                     ,smp=no)
Mar 29 10:49:42 localhost loadndisdriver: loadndisdriver: main(462): version 1.0                     rc2 started
Mar 29 10:49:42 localhost kernel:
Mar 29 10:49:42 localhost kernel: zd1211u: probe of 1-1:1.0 failed with error -2                     2
Mar 29 10:49:42 localhost kernel: usbcore: registered new driver zd1211u
Mar 29 10:49:42 localhost kernel: ndiswrapper: driver zd1211u (3COM Corporation,                     10/06/2004,2.12.1006.2004) added

In despair, late last night, I tried adding some lines in /networking/interfaces  to manually create a wlan0 connection.It obviously didn't work. Here are the details :

etc/network/interfaces

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
 script grep
 map eth0
 map wlan0

iface eth0 inet dhcp
iface wlan0 inet dhcp

auto eth0
auto wlan0


etc/network/options

> ip_forward=no
spoofprotect=yes
syncookies=no

etc/network/ifstate

> eth0=eth0
lo=lo

_2) on Hoary, using the zydas linux driver following the "WifiDocs/Driver/zydas zd1211" wiki_

I can
aptitude install linux-headers-$(uname -r) build-essential
wget [http://zd1211.ath.cx/download/zd1211-driver-r52.tgz](http://zd1211.ath.cx/download/zd1211-driver-r52.tgz)
tar -xvzf zd1211-driver-r52.tgz

but when I
cd zd1211 

I get something like
> No such file or directory


_3) Upgrading to Dapper_

A thread said that the needed drivers were included in Dapper. I downloaded dapper i386 and installed it on a spare computer to test.
After modprobe zd1211, the dongle was powered up (first led on) and a wlan0 created in /networking.  ;)
When I activate it (with the same parameters than with another wirelessly connected computer - ie essid = 3Com and DHCP), the second led of the dongle blinks  twice, showing that it tries to create a connection to the router, and then nothing. The wlan0 is active but I don't have access to the net, and the second led of the dongle is off.

I am ready to backup everything, to try an upgrade to dapper (is an upgrade from Hoary to Dapper feasible?) but it has to be worth it for wireless...

---

### Post by alamba on 2006-03-29
I could try to help you out with option 3. Upgrade is possible with dist-upgrade. Not too familiar with ndiswrapper. Once you boot into dapper, get into system>>admin>>networking. Then select wlan0 and click properties and put in the SSID, etc details. Then click activate. What do you get? Post your ifconfig post this step.

A

---

### Post by damu on 2006-03-29
ok, so here is the part of ifconfig concerning the wlan0 on the "**test computer"** on which I installed Ubuntu Dapper (I hope if we can sort it out on this "test computer" it will out the same way on the "kubuntu laptop" after upgrade to kubuntu dapper). I had to type it as I have no way to transfer the file from one computer to the other and :

if config

wlan0 Link encap:Ethernet HWaddr 00:14:7C:66:D4:B1
         inet addr :192.168.1.6 Bcast: 192.168.1.255 Mask : 255.255.255.0
         ipnet6 addr: fr80::214::7cff:fe66:d4b1/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:l
         RX packets:22 errors:0 dropped:0 overruns:0 frame:0
         TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:2423 (2.3 KiB) TX bytes:1488 (1.4 KiB)

---

### Post by damu on 2006-03-29
I really don't know how to go much further without your help... :-k

---

### Post by damu on 2006-03-29
I just finished the backup of my datas to an external HD and I am about to upgrade to Dapper. Still have to sort out a problem with the sources.list.

I would really appreciate more comments about the core of my problem though: wireless connection and the best option to take...

---

### Post by OfficeLinebacker on 2006-03-29
I agree with the upgrade to Dapper.

---

### Post by alamba on 2006-03-30
damu: You're almost there buddy. ifconfig tells me that you get an IP. Which means that your hardware is recognized and you're getting an IP. It should be no problem getting online with your wireless connection now. Here are a few things to check:

1. Go into system>admin>networking, just cross check that both the wireless and wireline interfaces are not active, if they are disable the wireline

2. vi /etc/resolv.conf check if this has a entry like nameserver <yourdnsserverip>

3. ping <your_gateway_ip>

4. ping oracle.com

Post incase any of the above fails.

A

---

### Post by damu on 2006-03-31
Thanks for your help.

Here is where I am. The laptop to be upgraded gives me a bit of sorrow with kinaptic freezing, kate freezing in sudo, borken package and so on, so I think to do a fresh install of Dapper, which will be the opprotunity to create a dedicated partition for the home folder.

I installed Kubuntu Dapper on the "test computer" (which previously had Ubuntu dapper installed). 
I wanted to make sure that the drivers for my 3com usb dongle (zd1211) were not only in Ubuntu Dapper, but also in Kubuntu Dapper.

Well, it seemq there are not. When I > modprobe zd1211 , nothing happens. No Wlan0 created, the led of the dongle doesn't turn on, as it did on Ubuntu Dapper.

Back to step1 :confused: 

The whole point of going to Dapper is the ease for wireless conectionas mentionned in [this thread ]("http://www.ubuntuforums.org/showthread.php?t=145677&highlight=3crusb10075")

What should I do?

---

### Post by alamba on 2006-04-01
Sorry buddy. Getting the hardware detected is beyond my skillset. Once it's detected I could help you set it up to go online. Maybe someone else on here could help you, or else, use Ubuntu rather than Kbuntu.

A

---

