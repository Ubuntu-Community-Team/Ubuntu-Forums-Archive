---
title: "Intel PRO wireless 2200bg does not work"
date: 2011-10-02
forum: General Help
---

### Post by glinskyc on 2011-10-02
Okay, so I've finally surrendered to the forum for help specific to my problem.  I've tried to solve this by following help from many other threads and nothing has worked.  I really appreciate any help I can get.

Here are copies of my Terminal output for various commands:

chad@chad-TravelMate-290:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

*************************************************

chad@chad-TravelMate-290:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:18:ef:87
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.21 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:a000(size=256) memory:d0001000-d00010ff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:17:c2:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=128 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:d0000000-d0000fff

---

### Post by plucky on 2011-10-03
> chad@chad-TravelMate-290:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: no
**Hard blocked: yes**

Do you have a hardware switch for your wireless on the laptop?

---

### Post by glinskyc on 2011-10-03
Yes, I do have a hardware switch for wifi and its always worked fine when I had winXP.  I will note that I believe the switch was turned off when i did the Ubuntu 11.04 install, not sure if that matters.

---

### Post by plucky on 2011-10-03
Is your laptop an Acer Travelmate?

I have an old Fujitsu-Siemens laptop with the same wireless NIC and it has a switch to turn on and off the wireless interface.I had to install a driver to get the wireless to work.

The command I used was ```
sudo modprobe wistron_btns
``` this loads the driver into the kernel (temporarily) and my laptop switch was then able to turn on the wireless NIC.

Give it a try and see if it works.

If it does,you then have to load the driver on every reboot by putting it into /etc/modules.

Good Luck

---

### Post by glinskyc on 2011-10-03
> **plucky said:**
> Is your laptop an Acer Travelmate?

I have an old Fujitsu-Siemens laptop with the same wireless NIC and it has a switch to turn on and off the wireless interface.I had to install a driver to get the wireless to work.

The command I used was ```
sudo modprobe wistron_btns
``` this loads the driver into the kernel (temporarily) and my laptop switch was then able to turn on the wireless NIC.

Give it a try and see if it works.

If it does,you then have to load the driver on every reboot by putting it into /etc/modules.

Good Luck

Yeah, it's an acer TravelMate 290.

Unfortunately, I tried the wistron_btns code and got this:


chad@chad-TravelMate-290:~$ sudo modprobe wistron_btns
FATAL: Error inserting wistron_btns (/lib/modules/2.6.38-11-generic/kernel/drivers/input/misc/wistron_btns.ko): No such device

Anywhere to go from here?  Thanks

---

### Post by plucky on 2011-10-04
> Anywhere to go from here? Thanks 

There is a package call acer_wmi which should do the same thing as the wistron package.You could try ```
sudo modprobe acer_wmi
``` and see if you can now turn on the wireless.


Good Luck

---

### Post by glinskyc on 2011-10-04
I tried acer_wmi and that also gives the error.  Here's the output:


chad@chad-TravelMate-290:~$ sudo modprobe acer_wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device


I was trying various things to fix my problem prior to starting this thread, is it possible I may have changed/uninstalled something I needed for the acer_wmi or wistron_btns commands to work?

---

### Post by plucky on 2011-10-05
> **glinskyc said:**
> I tried acer_wmi and that also gives the error.  Here's the output:


chad@chad-TravelMate-290:~$ sudo modprobe acer_wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device


I was trying various things to fix my problem prior to starting this thread, is it possible I may have changed/uninstalled something I needed for the acer_wmi or wistron_btns commands to work?

I get the same error when I try the command on my desktop.It is probably not finding the relevant hardware.You probably need to find the right driver for your hardware.

There might be a way to enable the wireless in the BIOS which bypasses the switch (just a thought).


Good Luck

---

### Post by glinskyc on 2011-10-07
> **plucky said:**
> I get the same error when I try the command on my desktop.It is probably not finding the relevant hardware.You probably need to find the right driver for your hardware.

There might be a way to enable the wireless in the BIOS which bypasses the switch (just a thought).


Any ideas on how to get such a driver?  My understanding was that Ubuntu 11.04 kernel comes with the ipw2200 driver included (see code of my first post where it indicates the ipw2200).  This driver is supposed to work for my Intel PRO Wireless 2200bg setup, but something clearly isn't right.

---

### Post by glinskyc on 2011-10-25
Bump.  Still stuck with this problem.  Any additional help is highly appreciated.  Thanks.

---

### Post by glinskyc on 2011-12-23
Bump

---

### Post by bilderbuchi on 2012-07-21
so glinskyc, have you solved this problem in the end? I have the exact same problem i fear. :-(

---

### Post by bilderbuchi on 2012-07-21
I found a solution! You have to get the acerhk module to install and load. See [http://askubuntu.com/a/166331/11069](http://askubuntu.com/a/166331/11069)

---

