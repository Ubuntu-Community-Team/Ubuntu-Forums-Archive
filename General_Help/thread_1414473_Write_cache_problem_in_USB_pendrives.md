---
title: "Write cache problem in USB pendrives"
date: 2010-02-23
forum: General Help
---

### Post by Pi72 on 2010-02-23
Here's my problem: Whenever I plug-in my USB 8gb pendrive to copy a large file, it takes eons.

Using Ubuntu 9.10 for AMD64.

At first it copies a file at high speeds, because it's not actually writing to the USB but to the cache; at 500-700mb, the write cache is full and flushes, *while* still copying the rest of the file. Since the system is trying to access the USB in two different places at the same time, the transfer speed bunks down, often to 200-300kb/s. The final process, instead of taking 2 minutes, takes one hour. This continues until 1.4gb, when the cache finishes the flush, the copy can continue streamlined and the last 200-300mb are copied again at quicker speeds.

I've made a test, copying a 1.6gb file to the USB and waiting for the cache to get full. Once it happens, I copy another file of the same size to the USB at the same time, when it starts copying I cancel the previous copy - cancelling it could take 1-2 minutes, but once it's cancelled, the second copy goes amazingly quick since the pendrive doesn't have any access troubles anymore. However, that means for the trick to work that I can't copy four 1.6 files to the 8gb pendrive, but only three. The fourth one would need an hour unless I start copying it just before the first three finish so the write cache is still not in use or something like that.

So what I would want is that everytime I plug-in this specific USB drive (identified by its label or UUID), the automount parameters disable write caching for this drive. Is that feasible? Using fstab or how?

---

### Post by mörgæs on 2010-02-24
This is interesting. Maybe you could add your findings to 
[https://bugs.launchpad.net/ubuntu/+bug/197762?comments=all](https://bugs.launchpad.net/ubuntu/+bug/197762?comments=all)

It seems like a problem concerning a lot of people.

---

### Post by narcisgarcia on 2011-12-13
In the bug [197762]("https://bugs.launchpad.net/bugs/197762") is said that the problem is hardware-dependent, but I've been affected by the same low speed effect differently in the same computer: allright in an Ubuntu 11.04 (32bits) installation, but low speed effect in an Ubuntu 11.04 (64bits) installation.

Mainboard "Asus M4A785-M"

**sudo lshw -short**
```

H/W path           Device       Class       Description
=======================================================
                                system      System Product Name (To Be Filled By O.E.M.)
/0                              bus         M4A785-M
/0/0                            memory      64KiB BIOS
/0/4                            processor   AMD Phenom(tm) II X2 550 Processor
/0/4/5                          memory      256KiB L1 cache
/0/4/6                          memory      1MiB L2 cache
/0/4/7                          memory      6MiB L3 cache
/0/33                           memory      8GiB System Memory
/0/33/0                         memory      2GiB DIMM DDR2 Synchronous 667 MHz (1,5 ns)
/0/33/1                         memory      2GiB DIMM DDR2 Synchronous 667 MHz (1,5 ns)
/0/33/2                         memory      2GiB DIMM DDR2 Synchronous 667 MHz (1,5 ns)
/0/33/3                         memory      2GiB DIMM DDR2 Synchronous 667 MHz (1,5 ns)
/0/100                          bridge      RS880 Host Bridge
/0/100/1                        bridge      RS880 PCI to PCI bridge (int gfx)
/0/100/1/5                      display     RS880 [Radeon HD 4200]
/0/100/1/5.1                    multimedia  RS880 Audio Device [Radeon HD 4200]
/0/100/a                        bridge      RS780/RS880 PCI to PCI bridge (PCIE port 5)
/0/100/a/0         eth0         network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/11          scsi2        storage     SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
/0/100/11/0        /dev/sda     disk        320GB ST3320813AS
/0/100/11/0/1      /dev/sda1    volume      285MiB EXT4 volume
/0/100/11/0/2      /dev/sda2    volume      297GiB Linux raid autodetect partition
/0/100/11/1        /dev/cdrom3  disk        DVDRAM GH20LS15
/0/100/11/0.0.0    /dev/sdb     disk        320GB SAMSUNG HD321KJ
/0/100/11/0.0.0/1  /dev/sdb1    volume      285MiB EXT4 volume
/0/100/11/0.0.0/2  /dev/sdb2    volume      297GiB Linux raid autodetect partition
/0/100/12                       bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.1                     bus         SB7x0 USB OHCI1 Controller
/0/100/12.2                     bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                       bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.1                     bus         SB7x0 USB OHCI1 Controller
/0/100/13.2                     bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                       bus         SBx00 SMBus Controller
/0/100/14.1        scsi0        storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.1/0.0.0  /dev/cdrom   disk        DVD-RAM GH22LP20
/0/100/14.1/0.1.0  /dev/cdrom1  disk        CD/DVDW SH-S182M
/0/100/14.2                     multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                     bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                     bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/6                   multimedia  ES1371 [AudioPCI-97]
/0/100/14.5                     bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/101                          bridge      Family 10h Processor HyperTransport Configuration
/0/102                          bridge      Family 10h Processor Address Map
/0/103                          bridge      Family 10h Processor DRAM Controller
/0/104                          bridge      Family 10h Processor Miscellaneous Control
/0/105                          bridge      Family 10h Processor Link Control
/0/1               scsi17       storage     
/0/1/0.0.0         /dev/sdc     disk        1TB SCSI Disk
/0/1/0.0.0/1       /dev/sdc1    volume      931GiB EXT3 volume
/0/2               scsi7        storage     
/0/2/0.0.0         /dev/sdd     disk        4127MB SCSI Disk
/0/2/0.0.0/1       /dev/sdd1    volume      3933MiB Linux filesystem partition
```

**lspci**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
```

---

