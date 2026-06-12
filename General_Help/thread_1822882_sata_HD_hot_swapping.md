---
title: "sata HD hot swapping"
date: 2011-08-11
forum: General Help
---

### Post by bwv539 on 2011-08-11
I am using Ubuntu 10.04, 64 bits.
I need to swap sata hard drives (they are installed in drawers). 
If I umount and remove a disk, and then put the same drive in it's place, I can mount it again with no problems. 
If I put another disk in place of the original, it says:
mount: special device /dev/sdc1 does not exist.
If I reboot, the new disk is mounted correctly (sdc1 is in fstab).
What am I doing wrong?

---

### Post by Kira_Belka on 2011-08-11
do you use any external sata raid controllers? or embedded?.. so post result lspci plz

---

### Post by bwv539 on 2011-08-11
> **Kira_Belka said:**
> do you use any external sata raid controllers? or embedded?.. so post result lspci plz
No raid controller. Hard disks connected to sata controller embedded in mobo.
Here is lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection

```

---

### Post by mcduck on 2011-08-11
> **bwv539 said:**
> I am using Ubuntu 10.04, 64 bits.
I need to swap sata hard drives (they are installed in drawers). 
If I umount and remove a disk, and then put the same drive in it's place, I can mount it again with no problems. 
If I put another disk in place of the original, it says:
mount: special device /dev/sdc1 does not exist.
If I reboot, the new disk is mounted correctly (sdc1 is in fstab).
What am I doing wrong?

Make sure the device node for the new drive really is /dev/sdc. The drive naming isn't based on the connector you plug a drive in, but instead on the order in which the drives are detected. So it's more than likely that when you replace a drive with another one, the new one gets a new device name as well.

You can easily check the device name for the drive if you run "tail -f /var/log/syslog", then plug in the dive, and check the terminal for information about how the drive is detected.

If you need to configure any automatic stuff for the drives you should use UUID or label instead of the device name.

---

### Post by bwv539 on 2011-08-11
> **mcduck said:**
> Make sure the device node for the new drive really is /dev/sdc. The drive naming isn't based on the connector you plug a drive in, but instead on the order in which the drives are detected. So it's more than likely that when you replace a drive with another one, the new one gets a new device name as well.

I don't think this is the problem. I tried also the next letters available (/dev/sdd, etc) with no luck. Even if I go to System->Administration->Disk Utility the disk il not listed.
> **mcduck said:**
> 
You can easily check the device name for the drive if you run "tail -f /var/log/syslog", then plug in the dive, and check the terminal for information about how the drive is detected.

I tried: nothing happens when I plug the disk. This is strange because if leave the disk in place and reboot the disk is mounted after rebooting.

---

