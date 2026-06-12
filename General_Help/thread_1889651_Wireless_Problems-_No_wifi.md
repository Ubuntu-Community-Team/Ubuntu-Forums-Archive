---
title: "Wireless Problems- No wifi"
date: 2011-12-01
forum: General Help
---

### Post by ernestj on 2011-12-01
I am having wireless problems ever since I installed 11.10. My wifi worked just fine in 11.04. Please see the following outputs for info about system:


ernest@ernest-U56E:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
03:00.0 USB Controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
ernest@ernest-U56E:~$ 

ernest@ernest-U56E:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 


ernest@ernest-U56E:~$ uname -a
Linux ernest-U56E 2.6.38-02063808-generic #201106040910 SMP Sat Jun 4 09:13:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

ernest@ernest-U56E:~$ dmesg | grep -ie wlan -ie err
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    1.228030] ACPI: Using IOAPIC for interrupt routing
[    1.261024] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.261208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.261242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.261279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.261316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.265734] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    1.265783] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    1.265828] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    1.265873] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    1.265919] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    1.265964] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    1.266009] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    1.266053] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
[    1.547861] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.547883] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    1.547885] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.547907] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.547909] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.547930] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
[    1.547932] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[   19.913260] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   27.254452] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600
[   28.782252] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600
[  420.731036] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  422.978271] wlan0: authenticate with 00:30:44:06:8f:3b (try 1)
[  422.980070] wlan0: authenticated
[  422.986034] wlan0: associate with 00:30:44:06:8f:3b (try 1)
[  422.989600] wlan0: RX AssocResp from 00:30:44:06:8f:3b (capab=0x421 status=0 aid=3)
[  422.989613] wlan0: associated
[  422.994210] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  433.117549] wlan0: no IPv6 routers present
[ 1171.048910] evince[2271]: segfault at 2c0 ip 00007f1b206e98f4 sp 00007fff9d7ff0c8 error 4 in libc-2.13.so[7f1b205cb000+195000]
[ 6132.774087] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[ 6132.811948] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
[ 6132.811966] ata3: SError: { PHYRdyChg CommWake }
[ 6132.812005]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)


ernest@ernest-U56E:~$ sudo iwlist scan
[sudo] password for ernest: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:30:44:06:8F:3B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"MBR-f3b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004c7e4587c2
                    Extra: Last beacon: 250ms ago
                    IE: Unknown: 00074D42522D663362
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1A6C101EFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C334C101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD710050F204104A0001101044000101103B000103104700104CAD1C9388A43A7CB01585F5095B28E31021000B437261646C65506F696E74102300084D42522D31303030102400024131104200046E6F6E651054000800060050F20400011011000B4D42522047617465776179100800020004


ernest@ernest-U56E:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:3f:46:d4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-02063808-generic firmware=41.28.5.1 build 33926 ip=192.168.10.192 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:25:6c:d0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


I ran the commands in order that were requested.
Thank you for all of your help.
Ernie

---

### Post by pytheas22 on 2011-12-01
Thanks for the information.  Your wireless chipset is an Intel 6150 card with PCI ID 8086:0885, using the driver iwlagn.  Normally that driver works very well in Linux, but it appears to be a known issue that it won't connect in Ubuntu 11.10 using the Linux 3.x kernel.  There's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/876147") and a forum thread [here]("http://ubuntuforums.org/showthread.php?t=1862484&page=5").

Unfortunately, from what I've read, it doesn't seem that anyone has found a solution yet other than to downgrade to a 2.6.x kernel.  As I recall you've already done that, but in case you need to do it again there are instructions in post #42 of [this thread]("http://ubuntuforums.org/showthread.php?t=1862484&page=5").

So it seems that right now there's not going to be a better fix than just downgrading the kernel.  You could try using ndiswrapper with the Windows driver to get the card working, but I think ndiswrapper doesn't work with the newer Intel wireless cards.

With luck there will be a real solution soon--I would keep my eye on the bug report and thread linked above.  In the meantime, running Ubuntu 11.10 with a slightly older kernel should not really make much of a difference.  You can still use all the updated 11.10 apps; you just won't have the behind-the-scenes features of the newer kernel, but honestly these are much less exciting than the bump up to version 3.0 would suggest.  (You can read about the new stuff in the 3.0 kernel [here]("http://kernelnewbies.org/Linux_3.0"); most of it doesn't even affect desktop users.)

---

### Post by ernestj on 2011-12-01
Thank you for your help. I did download the alpha 1 of 12.04 with the kernel 3.2(?). Still has a problem. I am to the point of selling my laptop on ebay and getting a different machine.

The main thing that I am missing is the two-finger scroll. 

Thank you again,

ernie

---

### Post by pytheas22 on 2011-12-01
Yeah, unfortunately I wouldn't expect the problem to be fixed in a newer version of Ubuntu either because it seems to be an issue affecting all iterations of the 3.x kernel, not just the particular one in Ubuntu 11.10.  Hopefully someone will sort it out soon; it's kind of embarrassing for Intel wireless chips not to work since traditionally they have had rock-solid performance on Linux.

---

