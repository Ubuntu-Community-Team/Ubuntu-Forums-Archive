---
title: "wired connection"
date: 2012-01-15
forum: General Help
---

### Post by Harry Z on 2012-01-15
Hi, all, :)

I've installed an ubuntu 11.10 on my laptop and connected it to my router. But the network does not work. Has anybody encountered the same problem?

Best regards,
Harry

---

### Post by corrytonapple on 2012-01-15
Is it Wireless or Wired that does not work?
What are the specs of your laptop?
We can help you once you supply this.

---

### Post by Harry Z on 2012-01-15
Hello, thank you for your reply.
          
My computer is HP tx2000. And this is a WIRED connection problem.

Here please find my config:

dina@ubuntu:~/Desktop$ ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:1e:68:be:f7:46  
          inet6 addr: fe80::21e:68ff:febe:f746/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:22498 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8006 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:10626889 (10.6 MB)  TX bytes:1299334 (1.2 MB) 
          Interrupt:43 

And at the connection port, the orange light is not on. 

Best regards,
Harry

---

### Post by bluexrider on 2012-01-15
lets take a look at your hardware configuration 
Please post the print of 

```
sudo lshw -C network
```

may give us a clue

---

### Post by corrytonapple on 2012-01-15
Off the top of my head, and its been a while, you may want to try installing additional drivers.  Go to (Assuming Unity) Ubuntu Logo, click it, and search "additional drivers".  Have it check if you need any.  
If reports come back negative, then try launching a terminal, same as last time, just type "Terminal".  Then type:
```
sudo apt-get install firmware-realtek
```
It will not show the password as you enter it.

It is assumed you have realtek Wired/WiFi cards, and the audio is realtek too.  Nothing wrong with finding out.

---

### Post by Harry Z on 2012-01-16
Dear Blue,

Here please find the result of SUDO:


dina@ubuntu:~/Desktop$ sudo lshw -C network 
[sudo] password for dina: 
PCI (sysfs)  
  *-network               
       description: Network controller 
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:d1100000-d1103fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1e:68:be:f7:46 
       size: 100Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=MII speed=100Mbit/s 
       resources: irq:43 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:21:00:44:1f:9f 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg 

Best regards,
Harry

---

### Post by Harry Z on 2012-01-16
Dear Apple,

Could you please explain a little about what does " Go to (Assuming Unity) Ubuntu Logo, click it, and search "additional drivers"" mean. I'm confused. 

Thank you very much.
Best regards,
Harry

---

### Post by corrytonapple on 2012-01-16
What version of Ubuntu are you on?
If you are using the one that has the "Applications, Places, and System" menu, then you need to go to **Applications > Accessories > Terminal**.

If you are on the Ubuntu that has the Side Panel, then you need to go to the Ubuntu logo in the top left hand corner, then click it, and it will bring up a search box.  Type "Terminal".  Then type in the above commands and restart.
That is, *after* trying opening up "Additional Drivers".  It is done, if you have the Applications, System, and Places menu at the top (This is called GNOME 2), by clicking **System > Administration > Additional Drivers**.  Enable whatever drivers it brings up.
If using the one with the side panel (This is called Unity), then click the Ubuntu Logo in the top left hand corner, type in "additional drivers" and then enable whatever drivers need to be enabled.

---

### Post by Harry Z on 2012-01-16
Dear Apple,

I cannot install drivers in this way because neither wired and wireless work on my pc now. Because the wireless active button on my laptop doesn't work, I cannot use it.

If I active a driver, the system says: 

Failed, please have a look at the log file for details. 

Harry

---

### Post by corrytonapple on 2012-01-16
In ```
 tags, please post the output of (in the Terminal):
[code]sudo gedit /var/log/debug
```
What version of  Ubuntu are you using?

---

### Post by varunendra on 2012-01-18
Hello Harry, and welcome to the forums!

First off, you can't install another driver for your Ethernet interface, because it already has the one Ubuntu has to offer. However, an update may do the trick but for that you need to get connected to internet first.

As per your *lshw *output, you are using **RTL8111/8168B** chip with **r8169 **driver. This combination has a known bug causing such problems, but seems to have been fixed in newer kernels. Also, it generally causes intermittent, slow or unstable connections, while you seem to have no connection at all. Accordingly, please try:
```
sudo dhclient
```
then try to browse to see if you are connected. If not, then (give a 15-20 sec. pause between each command):
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient
```


If none of the above work, we need to dig further. Accordingly, please post the outputs of:
```
uname -rm
ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces
```

..and please answer these:

[LIST]
[*]Do you know if your router/modem has DHCP enabled or not?
[*]Do you know what the LAN IP of your router is? (mostly it is 192.168.1.1, but may differ in certain cases).
[/LIST]
Also, make sure the cable you are connecting with is not defective and the ports it is being plugged-in are clean. Try replacing it if you have a spare one.


As for your wireless connectivity problem:
> **Harry Z said:**
> ..neither wired and wireless work on my pc now. Because the wireless active button on my laptop doesn't work, I cannot use it.What do you mean by "doesn't work"? Is it physically broken or just stopped working AFTER installing Ubuntu.

If it's just with Ubuntu, then it is much easier to fix. Please follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
(you will have to implement STA- No internet method: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access))

---

