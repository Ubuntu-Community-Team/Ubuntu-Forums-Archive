---
title: "Power settings won't stick"
date: 2011-12-04
forum: General Help
---

### Post by sirgad on 2011-12-04
Hi,

I'm using Ubuntu 11.10 64-bit Server with kernel 3.0.0-13-server (upgraded from -12-server with dist-upgrade two days ago).

I'm trying to configure power saving settings, but they don't seem to stick.  For example, I manually increased the VM Writeback Timeout to reduce writes to the HDD at least a week ago, but when I recently ran "sysctl -a", it revealed that the setting was back to its default.

PowerTop 1.97 is my main source of information regarding power drains.  On the "Tunables" tab, it offers the option of automatically changing various settings to improve power management.  However, changing any of these options from "bad" to "good" (ie. telling PowerTop to implement beneficial changes on my behalf) will not last beyond a server restart&#8212;when I go to the "Tunables" tab again, they're all back to "bad".

Here's the list of options I'd like to modify, according to PowerTop:

```
   Bad           Enable SATA link power management for /dev/sda                                                         
   Bad           VM writeback timeout
   Bad           Enable Audio codec power management
   Bad           Runtime PM for PCI Device Ricoh Co Ltd RL5c476 II
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3
   Bad           Runtime PM for PCI Device Intel Corporation Mobile 4 Series Chipset Memory Controller Hub
   Bad           Runtime PM for PCI Device Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2
   Bad           Runtime PM for PCI Device Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe
   Bad           Runtime PM for PCI Device Intel Corporation ICH9M/M-E SATA AHCI Controller
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) PCI Express Port 5
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) PCI Express Port 1
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) HD Audio Controller
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6
   Bad           Runtime PM for PCI Device Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
   Bad           Runtime PM for PCI Device Ricoh Co Ltd R5C832 IEEE 1394 Controller
   Bad           Runtime PM for PCI Device Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1

```
PowerTop only runs as root (ie. sudo powertop) so it's not a permissions issue. I'd really appreciate some help getting these settings implemented permanently, especially the audio codec power saving.  The audio chips have been running 100% since day one, which is pointless because my laptop is a server and needs to emit no sounds at all.

I've come across plenty of hints on manually modifying power settings, but they all suggest using "echo" to modify settings in /proc, which always results in a permissions error, even when running as root.  A chat on the #ubuntu channel eventually revealed that using "echo "<value>"|sudo touch &#8230;" forced the values to change&#8212;but this doesn't appear to be the expected way to modify values in procfs.  But now, even those settings in /proc have reverted to their defaults.

Help really would be much appreciated.

Much obliged,

S.

---

### Post by decomp on 2011-12-24
bump: Me too!

---

### Post by sirgad on 2011-12-27
I am no longer looking for an answer owing to the fact that I will shortly be replacing the Ubuntu machine with a Mac mini running Lion Server.

However, for the benefit of others (such as poor *decomp* above) please continue to respond to this thread.

Regards,

S.

---

### Post by sirgad on 2012-01-25
Turns out that PowerTOP is designed so that the "tunables" are reset on re-boot.  If you want them to be permanently applied you have to find some other way of applying the settings you want, or just get used to re-applying them every boot.

Discussion at PowerTOP mailing list:

[Tunables not surviving reboot]("http://bughost.org/pipermail/power/2012-January/date.html")

Hope this helps,

S.

---

