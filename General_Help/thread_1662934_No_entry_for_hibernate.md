---
title: "No entry for hibernate"
date: 2011-01-08
forum: General Help
---

### Post by vacco on 2011-01-08
When I click on the "shutdown, logout, suspend etc."-button in the upper right corner there is no option to hibernate my machine. I've got suspend, reboot and shut down, but no hibernate. What would be the reason for this?

If it should tell anyone anything, my computer is a Packard Bell TJ71 laptop with the following lspci output:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by ZebaSz on 2011-01-08
Make sure your swap is bigger than or equal to your RAM. Hibernation stores everything in swap, if I'm not wrong.

---

### Post by vacco on 2011-01-08
My swap partition is 4.03 GiB according to Gparted. That should be just enough (with the smallest possible margin) since I have 4 GiB of RAM. In fact I might even have less considering the fact that I have shared video memory (up to 256 MiB I think).

---

### Post by dcstar on 2011-01-09
> **vacco said:**
> My swap partition is 4.03 GiB according to Gparted. That should be just enough (with the smallest possible margin) since I have 4 GiB of RAM. In fact I might even have less considering the fact that I have shared video memory (up to 256 MiB I think).

[LIST=1]
[*]The swap is still too small
[*]Or the swap is not enabled: ```
man swapon
```
[/LIST]

---

### Post by vacco on 2011-01-09
Seems there might be some problems with swapon:
```
swapon -s
Filename				Type		Size	Used	Priority

```
No devices there.


```
swapon -a
swapon: cannot find the device for UUID=c6cd4dc1-cfa5-46f2-9bf7-4dd91fc1baeb
```
swapon -a does not work either, but I can right click the swap partition in Gparted and select swapon. After doing that, swapon -a gives the same error whereas swapon -s return this:
```
swapon -s
Filename				Type		Size	Used	Priority
/dev/sda8                               partition	4227068	0	-1

```
This entry is however gone after a reboot.


My guess is that this might have something to do with the Slackware system I installed on my drive which I set to use the same swap partition already used by Ubuntu.

---

### Post by efflandt on 2011-01-09
If Slackware recreated your swap partition, maybe it now has a different UUID.

Do: **sudo blkid** and see what the UUID is for the swap partition.  Then use gksu gedit /etc/fstab (or sudo nano) to fix the UUID for your swap partion if it is different.

Also you have to be careful about how applications count sizes, because some may use decimal units of 1000 and some may use binary based units of 1024, or formatted size may be smaller than amount of space it uses on the disk.

---

### Post by vacco on 2011-01-09
This is what I get for my swap partitio:
```
/dev/sda8: UUID="bac99b00-3241-4faf-94d9-197c94cfd94d" TYPE="swap" 

```
I have no idea what the UUID should be though.


On different counting schemes: 1 gibibyte (GiB) = 1024 mebibytes (MiB) while 1 gigabyte (GB) = 1000 megabytes (MB) according to [http://en.wikipedia.org/wiki/Mebibyte](http://en.wikipedia.org/wiki/Mebibyte).
My swap partition is 4.03 GiB (Gparted uses GiB).

---

### Post by vacco on 2011-01-09
One more indicator to support these theories about Slackware and UUID: /dev/sda8 appears at once when running swapon -s as root in Slackware.

---

### Post by vacco on 2011-01-14
Solved. See [http://ubuntuforums.org/showthread.php?t=1667432](http://ubuntuforums.org/showthread.php?t=1667432) for final solution.

---

