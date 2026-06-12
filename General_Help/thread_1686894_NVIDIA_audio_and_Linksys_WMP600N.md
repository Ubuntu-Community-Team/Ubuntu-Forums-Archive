---
title: "NVIDIA audio and Linksys WMP600N"
date: 2011-02-13
forum: General Help
---

### Post by rabih_aa on 2011-02-13
Hello,
I have been a windows user for a long time now. I tried out ubuntu and I was beyond impressed with this OS. I decided it was time to do a complete migration to ubuntu. I installed Ubuntu 10.10 on my HP laptop and everything went great. It detected all the drivers and my laptop is working in tip top shape. I decided to install ubuntu on a custom PC I recently bought (used for Java development), and that is when I started to run into problems. These are the specs on my custom pc:

CPU: Intel® Core™ i7-950 3.06 GHz
HDD: 128 GB Kingston 2.5 inch SATA Gaming MLC Solid State Disk
HDD2: 1TB SATA-III 6.0Gb/s 64MB Cache 7200RPM HDD
MEMORY: 12GB DDR3/1600MHz
MOTHERBOARD: (3-Way SLI Support) MSI X58A-GD45 Intel X58 Chipset SLI/CrossFireX Triple-Channel DDR3 ATX Mainboard w/ 7.1 Audio, eSATA, GbLAN, USB3.0, SATA-III, RAID, IEEE1394a, 3 Gen2 PCIe, 3 PCIe X1 & 1 PCI
VIDEO: NVIDIA GeForce GTS 450 1GB 16X PCIe Video Card
WIFI: Linksys WMP600N Wireless-N Dual-Band Adapter

I am using Ubuntu 10.10 64-bit edition on the system.
First problem I am having is there is no audio on my system. For this card I'm using an HDMI cable to connect it to my screen. I installed the NVIDIA proprietary drivers and there was no audio. I reverted back to drivers I found on the NVIDIA website and still there is no audio. 
Second problem I am having is attributed to the wifi card I am using (I think). I keep getting this message on boot after post (and on the terminal after I switch off the X server by stopping gdm):

[ 3.890588] Too many connections
[ 4.167613] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[ 4.168188] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[ 4.168749] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[ 4.188995] phy0 -> rt2x00pci_mcu_status: Error - MCU request failed, no response from hardware

However, after the system boots I can connect to the internet. 

I was wondering if anyone can help, or at least point me in a direction where I can get results. I have been researching these issues and nothing worked so far. I would really appreciate any help I can get as this is getting very frustrating.

Thank youi.

---

### Post by Hippytaff on 2011-02-13
The above post looks like spam.

It's always worth checking logs when you encounter issues. they can be found in
```

cd /var/log

```

do ls -a to list them all.

Also dmesg is helpful
```

dmesg | tail

```
tail restricts what is returned to the last few entries.

Sorry I can't offer anything specific

---

