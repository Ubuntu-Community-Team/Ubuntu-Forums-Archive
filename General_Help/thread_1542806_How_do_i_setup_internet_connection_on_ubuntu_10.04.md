---
title: "How do i setup internet connection on ubuntu 10.04"
date: 2010-07-31
forum: General Help
---

### Post by Rhye on 2010-07-31
Well I installed ubuntu, a fresh install.

And where the connection thing is on the top bar it had a red "!" And it wasn't connectin to the internet... Its weird because in the livecd I was in "try ubuntu" and it auto connected to my internet...

I deleted "auto eth0" to see if it fixed but it didn't

I want to know how to connect to my wired internet adsl?

---

### Post by alenn on 2010-07-31
I have the same problem but see if this help [http://ubuntuforums.org/showthread.php?t=1533554]("http://ubuntuforums.org/showthread.php?t=1533554")

---

### Post by Rhye on 2010-07-31
I've tried

sudo restart network-manager

It restarts it and the little wifi icon has waves through it and then the exclamation mark comes back up /:

---

### Post by Rhye on 2010-07-31
Please help

---

### Post by Rhye on 2010-07-31
Bump

---

### Post by Quackers on 2010-07-31
If you click on the icon do any networks show up?

---

### Post by Rhye on 2010-07-31
Umm no... Nothing comes up

---

### Post by Quackers on 2010-07-31
Which wireless card do you have?

---

### Post by Rhye on 2010-07-31
No wireless card

I'm trying to connect to adsl, all my cables are in..

When I had xp on this pc I had to install drivers for my ethernet(lan adapter)

But also I've ran ubuntu without any drivers and it has workled...

I have my drivers on a disk but its an installer cd with gui and everything is in .exe's

---

### Post by dineshs on 2010-07-31
please post the results of
```
ifconfig -a
``````
cat /etc/network/interfaces
```and```
sudo lshw -C network
```[COLOR="Blue"]when your modem is connected and is ON[/COLOR]

---

### Post by Rhye on 2010-07-31
I'm just about to eat dinner so be sure to leave a tab open on this.

Be back in 15-30 minutes :) please be here to help

---

### Post by Rhye on 2010-07-31
Ifconfig -a

rhye@rhye-desktop:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:16:fa:96  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:26 Base address:0x6000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:344 errors:0 dropped:0 overruns:0 frame:0

          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:28288 (28.2 KB)  TX bytes:28288 (28.2 KB)



cat /etc/network/interfaces

rhye@rhye-desktop:~$ cat /etc/network/interfaces

auto lo

iface lo inet loopback


sudo lshw -c network


rhye@rhye-desktop:~$ sudo lshw -c network

  *-network               

       description: Ethernet interface

       product: RTL8111/8168B PCI Express Gigabit Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 03

       serial: 6c:f0:49:16:fa:96

       size: 10MB/s

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s

       resources: irq:26 ioport:de00(size=256) memory:fdbff000-fdbfffff(prefetchable) memory:fdbf8000-fdbfbfff(prefetchable) memory:fdb00000-fdb1ffff(prefetchable)

---

### Post by dineshs on 2010-07-31
From the results I understand that the card is RTL8111/8168B but driver loaded is driver=r8169
So the reason can be a wrong driver loaded(I am not sure)
pl refer this
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)
before trying the solution given in that link please run this command in a terminal and see if you are getting an IP```
sudo dhclient
```(ifconfig -a will show)

---

### Post by Abstra on 2010-07-31
Could not get wireless to work after new install of Ubuntu.

My answer on another thread may help others.  Worth a try!



OK mines fixed.  Now remember my problem is exactly the same as yours so do what I did and it should work.

For some barmy reason even though the computer knows the hubs name ie  BTINternetHOmeHub**** etc it wants you to manually type it into the SSID  box.

System-Preferences-Network Connections   Now click on wireless tab      Click on your device in window   Yeap it knows its yours I know   It  will now open new window.   now type in exactly same name in SSID box  and apply.  Bingo.


Let me know what happens

---

