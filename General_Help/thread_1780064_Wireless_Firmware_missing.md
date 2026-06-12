---
title: "Wireless Firmware missing???"
date: 2011-06-11
forum: General Help
---

### Post by Graemzy on 2011-06-11
Hey. im brand new to ubuntu and need some help, i know windows but im just tryin to fix a mates laptop running this.

the problem is the wireless isnt workin, he just got a new version of ubuntu installed and when it came came back the wireless had stopped working. it was workin  before with an older version of ubuntu.

on the network connection at the top when i scroll over the wireless connection it just says "device not ready (firmware missing)"

my question is, how do i find out what nic is in the the lap top and how do i go about installing the firmware for it?

thanks!

---

### Post by gandaran on 2011-06-11
find out the wireless chipset first, type in terminal and post the results
```
lspci
```
or for usb
```
lsusb
```
edit:
you may try connecting the laptop to wired internet and update software package list
```
sudo apt-get update
```
then look in additional drivers, if any wireless driver there just enable it.

---

### Post by Graemzy on 2011-06-11
ok qell here is the first result from the cmd

nemotime@nemotime-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


i dont know how to makeit out maybe it makes ence to you. :D

any ideas from there. might try that auto update cmd ya gave me too, :D

---

### Post by Graemzy on 2011-06-11
also i cant find "additional drivers" its not under system > admin. do ya know where i can find it?

---

### Post by gandaran on 2011-06-11
> 04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
have you looked in system » administration » additional drivers after updating the package list using wired internet? your broadcom driver should be there ready for enabling,

---

### Post by gandaran on 2011-06-11
> **Graemzy said:**
> also i cant find "additional drivers" its not under system > admin. do ya know where i can find it?

what version  of ubuntu? maybe system » administration » hardware drivers

---

### Post by Graemzy on 2011-06-11
when i entered that update line into the cmd prompt/terminal it asks for a nemotime password.  i have the laptop connected using the RJ-45 now and i can get online no problem.

also im using Ubuntu 10.10 and there is nothing about drivers under system > admin,  there is an update manager but all that shows for update is a flash player update.

---

### Post by gandaran on 2011-06-11
> **Graemzy said:**
> when i entered that update line into the cmd prompt/terminal it asks for a nemotime password.  i have the laptop connected using the RJ-45 now and i can get online no problem.

also im using Ubuntu 10.10 and there is nothing about drivers under system > admin,  there is an update manager but all that shows for update is a flash player update.
about the password, type the administrator password, you don't actually see it typing then press enter.
there should be system » administration » additional drivers on ubuntu 10.10, if not check in system » preferences » main menu for the same option and enable.
you can also use synaptic package manager to install the driver but see if you can do it from additional drivers first.

---

