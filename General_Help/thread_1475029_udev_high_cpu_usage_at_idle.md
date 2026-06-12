---
title: "udev high cpu usage at idle"
date: 2010-05-06
forum: General Help
---

### Post by wolas on 2010-05-06
So wanted to try ubuntu 10.04 and gived it a try i installed ubuntu 32bit version and noticed that mine cpu is never idle that sux a bit i thought :guitar:

After few "kills" or almost masacre :popcorn: i found out that **udev** was the bad guy and caused my poor cpu to waste his cycles.[-X So ./udev stop solves things but no automounting is bad too. Same thing is in debian testing which i use as my primary OS that one is 64bit. Maybe it is hardware problem i dont know. It would be nice to have it fixed but i m not very experienced at figuring out it by myself so i come here for help :)  ):P

Top causes for wakeups:
   0.0% (  0.0)D  udevd
  37.6% (531.0)   [ahci] <interrupt>
  33.2% (469.7)   [kernel scheduler] Load balancing tick
  10.6% (149.9)   [Rescheduling interrupts] <kernel IPI>
   3.3% ( 46.2)   firefox-bin
   2.6% ( 36.1)   [eth0] <interrupt>
   2.2% ( 30.9)   rhythmbox
   2.0% ( 28.2)   [ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb7] <interrupt>
   1.7% ( 24.5)   USB device  1-2 : USB2.0-CRW (Generic)
   1.3% ( 17.8)   USB device  7-1 : Razer Diamondback 3G (Razer)
   1.2% ( 16.5)   [iwlagn] <interrupt>
   1.0% ( 14.0)   pulseaudio
   0.6% (  9.1)   compiz
   0.6% (  8.0)   [kernel core] usb_hcd_poll_rh_status (rh_timer_func)
   0.4% (  6.2)   gkrellm
   0.4% (  5.0)   syndaemon
   0.3% (  4.9)   [TLB shootdowns] <kernel IPI>
   0.1% (  2.1)   gnome-terminal
   0.1% (  1.5)   [kernel core] timer_action (ehci_watchdog)
   0.1% (  1.0)   [uhci_hcd:usb3, nvidia] <interrupt>
   0.1% (  1.0)   [HDA Intel] <interrupt>
   0.1% (  1.0)   [kernel core] nv_kern_rc_timer (nv_kern_rc_timer)
   0.1% (  1.0)   [kernel core] inc_rt_group (sched_rt_period_timer)
   0.1% (  1.0)   events/0
   0.1% (  1.0)   gvfs-afc-volume
   0.1% (  1.0)   hald-addon-stor
   0.0% (  0.6)   udisks-daemon
   0.0% (  0.4)   [acpi] <interrupt>
   0.0% (  0.4)   update-notifier
   0.0% (  0.4)   gvfsd-http
   0.0% (  0.3)   gnome-panel
   0.0% (  0.3)   nautilus
   0.0% (  0.2)   rtkit-daemon
   0.0% (  0.2)   scsi_id
   0.0% (  0.2)   clock-applet
   0.0% (  0.2)   gnome-settings-

after kiling udev :popcorn::guitar:

  32.8% (185.6)   [kernel scheduler] Load balancing tick
   8.8% ( 49.6)   [Rescheduling interrupts] <kernel IPI>
   8.4% ( 47.3)   [extra timer interrupt]
   7.5% ( 42.4)   [eth0] <interrupt>
   6.7% ( 37.7)   [ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb7] <interrupt>
   6.4% ( 36.4)   firefox-bin
   5.6% ( 31.5)   USB device  7-1 : Razer Diamondback 3G (Razer)
   5.1% ( 28.9)   rhythmbox
   3.7% ( 21.0)   USB device  1-2 : USB2.0-CRW (Generic)
   2.5% ( 14.0)   pulseaudio
   2.5% ( 13.9)   [iwlagn] <interrupt>
   2.1% ( 11.7)   compiz
   1.4% (  8.0)   [kernel core] usb_hcd

I have acer 6930 GT

root@N1:/etc/init.d# lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
root@N1:/etc/init.d# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0b38:0003  
Bus 007 Device 002: ID 1532:000d Razer USA, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 147e:1000 Upek 
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 064e:a103 Suyin Corp. 
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 07ca:a310 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

anything else just say

---

### Post by wolas on 2010-05-09
pyp :confused:

---

### Post by MsKK on 2010-05-10
I also have the same problem but in may case it was not udev. I am seriously thinking on downgrading because of the power consumption issue.

---

### Post by wolas on 2010-05-15
:confused:

also created bug report...

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578180](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578180)

---

### Post by wolas on 2010-05-18
bu bub bump
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=581791](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=581791)
bump

---

### Post by koala2000 on 2010-05-30
I had same problem before. But I finally solved it. In my case it was because of something about my DVD-RW's firmware. After I upgraded my DVD-RW's firmware, 'sudo udevadm monitor' never send out any mass information again, it only sent out the message when I insert/eject CD. But at before, it always send out tons of message something like something change of sr0. Below is how I solve this problem.

In terminal, input 'cdrecord -scanbus'
It'll list all the optical devices that connected to your system. And you can see the module number and firmware version here.

Googling and download the latest version of the firmware, then upgrade your optical device.

---

