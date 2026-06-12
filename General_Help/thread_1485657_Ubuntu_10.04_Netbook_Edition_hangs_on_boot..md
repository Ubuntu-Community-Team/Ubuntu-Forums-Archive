---
title: "Ubuntu 10.04 Netbook Edition hangs on boot."
date: 2010-05-17
forum: General Help
---

### Post by groach45 on 2010-05-17
I have an Acer Aspire One D250 with Ubuntu 10.04 Netbook Edition installed. The system hangs the majority of boots at the exact same place. 

Here is what I see when system hangs:
```

udev: starting version 151
usb 1-2: configuration #1 chosen from 1 choice
ACPI: Battery Slot [BAT0] (battery present)
b43-pci-bridge 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
b43-pci-bridge 0000:01:00.0: setting latency timer to 64
ahci 0000:00:1f.2: version 3.0
ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
alloc irq_desc for 28 on node -1
alloc kstat_irqs on node -1
ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
ahci: SSS flag set, parallel bus scan disabled
ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part
ahci 0000:00:1f.2: setting latency timer to 64
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 28
ata2: DUMMY
ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 28
ata4: DUMMY

```The system hangs at this ata4: Dummy line every time it hangs. Every once in a while it will boot up corectly. 
On a successfull boot the next few lines are as follows:
```

ssb: Sonics Silicon Backplane found on PCI device 0000:01:00.0
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40C, max UDMA/133
ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
ata1.00: configured for UDMA/133
scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
sd 0:0:0:0: Attached scsi generic sg0 type 0
sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sda: sda1 sda2 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk

```I will also attach the entire dmesg file from a successful boot.
Any advice for a fix or a possible reason for this hang would be greatly appreciated.

---

### Post by JohnCraickkciarc on 2010-05-17
I have a very similar Acer machine (sold by the Coles supermarkets with slightly different branding). I have identical screen messages and hang up behaviour.

I have found that bootup is 100% reliable with a network cable attached so I'm now looking further into the network side of things. I'll post here if I have any success either by experiment or off the net. I had a similar problem on a much earlier Ubunu and a different wireless laptop. I never solved the problem : it just went away one day when I applied some updates.

It looks like the system is waiting for a response from the wireless networking and hanging up when it doesn't get one. But occasionally there is a response and the boot proceeds. That suggest a timing problem.

My next trick will be to give the wlan card a permanent ip address rather than one off DHCP. That has fixed similar problems in the past

Good luck

John C

---

### Post by JohnCraickkciarc on 2010-05-17
I may have found a fix for this. It works on my system & maybe on yours as well.

For the Broadcom b43 wlan device I changed back from the open source driver that I'd originally installed to the proprietary driver. In the System - Administration part of 10.04 NBR there is an applet called Hardware Drivers which allows you to do this. The driver is called the "Broadcom STA wireless driver".

If you look in the /var/log directory there's a set of files from the dmesg system, "dmesg.0", "dmesg.1" etc. Some of these are from unsuccessful boot sessions and they mostly end just at the point where the system is trying to load the wireless hardware driver. Successful boots don't end at that point.  

So far the "fix" has worked consistently for 4 or 5 successive reboots so it's looking good. We'll see what happens when the system has cooled down overnight.

Good luck with it.

JohnC

---

### Post by groach45 on 2010-05-17
Thank You for your responses.
 
1. As for having an ethernet cable plugged in while booting that solution does not work for me.
 
2. I will look into switching to the sta driver when I get home. The only problem I can foresee with that is the sta driver does not support packet injection, which I use in conjuction with my backtrack VMimage. I will give it a try though as well as look into those other dmesg files to determine if that driver is the problem. I will post back this evening with my findings.

---

### Post by groach45 on 2010-05-17
Ok, removing the b43 driver and using the sta driver does stop the system from hanging. I too now have had 4 or 5 successful consecutive reboots. This is a huge problem for me as I really need to use the b43 driver. Does anyone have any suggestions on how to do so? Thanks again to John C. for figuring this out.

---

### Post by irvie on 2010-06-21
Any updates on this? 

I am experiencing the same behaviour.

Cheers

---

### Post by jbowen7 on 2010-08-18
I also have this same exact problem on an the same computer (Acer Aspire One D250). The computer is dual booting xp and 10.04, and I kept thinking my MBR was out of whack. I've been checking md5sums and grub settings till I found this thread. 

I'm going to boot to liveusb and chroot the mounted partition to read some log files, I'll post my findings.

Any chance that you guys ( JohnCraickkciarc, groach45, irvie) installed with a usb, or are dual booting? 

I don't want to use the STA driver either, so I'll continue to work on this.

---

### Post by wildman4god on 2010-08-28
Ditto with this problem, not sure if this helps, but editing grub and deleting the quite splash parameter causes it to boot, though once and a while it still hangs.

---

### Post by mbok on 2010-09-02
I've had this on a friend's netbook. Check [http://ubuntuforums.org/showpost.php?p=9303013&postcount=7](http://ubuntuforums.org/showpost.php?p=9303013&postcount=7)

"""
finally got the booting sorted out with this:

gksudo gedit /etc/default/grub
add it to the GRUB_CMDLINE_LINUX_DEFAULT line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"
save the file then run
sudo update-grub
"""

Haven't checked yet why this helps or what effects it might have, but it never hangs anymore.

---

### Post by oliviagj on 2010-09-07
> **mbok said:**
> I've had this on a friend's netbook. Check [http://ubuntuforums.org/showpost.php?p=9303013&postcount=7](http://ubuntuforums.org/showpost.php?p=9303013&postcount=7)

"""
finally got the booting sorted out with this:

gksudo gedit /etc/default/grub
add it to the GRUB_CMDLINE_LINUX_DEFAULT line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"
save the file then run
sudo update-grub
"""

Haven't checked yet why this helps or what effects it might have, but it never hangs anymore.
same computer, same model, this solution worked just fine for me. thanks!

---

### Post by ILRzz on 2010-12-11
> **oliviagj said:**
> same computer, same model, this solution worked just fine for me. thanks!
I'm using a Toshiba NB200 netbook with Xubuntu 10.10, and it worked here too. I'm not sure yet if it's forcing HPET or disabling LAPIC that did the trick, or if both are required but the Atom processors in these netbooks are generally single-cores so I'd guess it's LAPIC that's been causing the problems.

The original symptoms were odd. If I booted up the computer and left it alone, it would freeze after a few moments and eventually stop waiting for the boot sequence to continue when the timer eclipsed. However, as long as I pressed a key or scrolled the touchpad, the HDD light would flicker and the boot sequence would continue. So in order to get the OS up and running, I'd have to hold the spacebar until I had gotten to the desktop. Launching new applications would then again require some activity on the keyboard or touchpad.

---

