---
title: "All versions of Ubuntu freeze on Boot Screen"
date: 2010-12-20
forum: General Help
---

### Post by thisisdrob on 2010-12-20
Hello, I am new to linux and ubuntu but i am very interested in trying it.  I have tried many different versions of ubuntu, 10.10 x32 and x64, 10.04 x32 and x64, 9.10 x32 and i have tried mint 10 julia and mint 9.  Every version seems to freeze on the purple screen with the dots underneath for 10.04/10.10 (or the equivalent screen for other versions), or before that when it is loading the os.

I am running Windows 7 professional x64.

I have an Asus M4a88TD-V Evo USB 3 MOBO, 8 gb of ddr3 ocz ram, and a 1 gb sapphire ati video card.

Any help would be greatly appreciated.

Thank you.

---

### Post by amsterdamharu on 2010-12-20
If you boot from the Mint 9 CD there is a menu option called: "Start Linux Mint (compatibility mode)"

It has [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computing%29") arguments like xforcevesa noapic noapci nosplash irqpoll. Did you try that?

A kernel argument is some command given to the kernel that tells it to support some hardware functions. If it doesn't support some functions it is more unlikely to crash.

---

### Post by Quackers on 2010-12-20
Tap the F6 key at boot and get the boot prompt options. The nomodeset one may work for you.

---

### Post by thisisdrob on 2010-12-21
I tried both... The nomodeset boot resulted in the same freeze.  Booting Linux mint 9 in compatibility mode gave me 2 errors:
 (EE) VESA: kernel modesetting driver in use, refusing to load
(EE) no devices detected 

It let me boot Linux mint in low graphics mode... Is there anyway to install it so I wouldn't have to run it in compatibility mode?

---

### Post by thisisdrob on 2010-12-21
I tried to install Linux mint side by side the windows operating system andit said it installed successfully.  When I tried to run Linux from the hdd, it went directly to a black screen.  When I tried to boot in recovery mood it went to the black screen with all of the text and just stopped part way through and the cursor was just blinking.  What do I do to get this running?

---

### Post by amsterdamharu on 2010-12-21
xforcevesa is good, it forces to go to vesa (low graphics) mode. If it wouldn't it would crash.

I assume that if you are in the desktop for about 5 minutes it would not alert you to drivers that are available for your videocard?

If there are drivers available please install them but you cannot reboot (live session runs out of memory and would just delete all the changes).
Instead log out -> press control + alt + F1 -> type the following commands:
```
sudo service gdm stop
sudo service gdm start
```

Can you post the output of
```
sudo lshw
```
Or at least the part under display or pci that is your videocard.

If the card is not detected you might try to manually install the drivers for it, I be back in an hour or so to check this thread and can advice you then.

---

### Post by theasprint on 2010-12-21
Hi,

For installing Ubuntu, do you want to try the Alternate iso file?

The Alternate version is different from the LiveCD version because it gives better suppotr for unsupported systems. I think your system may be unsupported.

The Alternate should also produce a quicker installation time than the LiveCD version.

---

### Post by amsterdamharu on 2010-12-21
Alternate won't help, the op already had a desktop on the live cd using save mode. From there you can install.

Alternate is the same as the normal but doesn't use a gui for low memory systems or unsupported cards that give no desktop at all in the live CD or some other hardware that gives problem. After installing you end up with the same system anyway.

To OP, if you want to boot your installed system in save mode you can hold down shift to see the boot menu (if you didn't see that already). Highlight the Mint 9 option and look arround for the edit key. When you edit it replace "quiet splash" with xforcevesa that should boot you in low graphics mode. From there you can try to install the drivers and see if that works but I need to know what graphics card you have exactly hence request for posting the output of "sudo lshw" earlier.

---

### Post by thisisdrob on 2010-12-21
So after running compatibility mode again, I installed the video card driver and i went to enter the commands.  After i enter the "sudo service gdm start" code my computer goes to a black screen and freezes.  So I went back to compatibility mode and downloaded the driver again. then i went to the terminal and entered the "sudo lshw" code.

This is the output i recieved:

             ```
width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge Alternate
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:c000(size=4096) memory:fe800000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV770 [Radeon HD 4850]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:30 memory:d0000000-dfffffff(prefetchable) memory:fe8f0000-fe8fffff ioport:c000(size=256) memory:fe8c0000-fe8dffff(prefetchable)
           *-multimedia
                description: Audio device
                product: HD48x0 audio
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:9 memory:fe8ec000-fe8effff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 4)
             vendor: Advanced Micro Devices [AMD]
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:d000(size=4096) memory:fe900000-fe9fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:11 memory:fe9ff800-fe9fffff ioport:d800(size=256)
           *-ide
                description: IDE interface
                product: PATA IDE Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: scsi1
                version: a0
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list rom emulated
                configuration: driver=pata_via latency=0
                resources: irq:11 ioport:dc00(size=8) ioport:d480(size=4) ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=16) memory:fe9e0000-fe9effff(prefetchable)
              *-cdrom
                   description: DVD reader
                   physical id: 0.0.0
                   bus info: scsi@1:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   capabilities: audio dvd
                   configuration: status=nodisc
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:fea00000-feafffff
           *-usb
                description: USB Controller
                product: NEC Corporation
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:10 memory:feafe000-feafffff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:9 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fe7ffc00-fe7fffff
           *-disk
                description: ATA Disk
                product: WDC WD1001FALS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMATV2853039
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e8ebe5da
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 106e-059d
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-12-16 07:39:54 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 281624c8-6c63-954d-a685-00bbf9a5b862
                   size: 860GiB
                   capacity: 860GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-12-16 07:40:05 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@4:0.0.0,3
                   logical name: /dev/sda3
                   size: 70GiB
                   capacity: 70GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 67GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2993MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:10 memory:fe7fe000-fe7fefff
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:fe7ff800-fe7ff8ff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:10 memory:fe7fd000-fe7fdfff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:fe7ff400-fe7ff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi6
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22LS40
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@6:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                logical name: /cdrom
                version: LL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:5 memory:fe7f8000-fe7fbfff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:4
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:10 memory:fe7fc000-fe7fcfff
        *-pci:4
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27
        *-pci:5
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 06
                serial: 48:5b:39:ca:12:4e
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.128 latency=0 link=yes multicast=yes port=MII speed=1GB/s
                resources: irq:29 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febf0000-febfffff(prefetchable)
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:10 memory:fe7f7000-fe7f7fff
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:11 memory:fe7ff000-fe7ff0ff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@3:1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE-6
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
             version: 9740
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE-6
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdc
             version: 9740
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE-6
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@8:0.0.2
             logical name: /dev/sdd
             version: 9740
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE-6
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@8:0.0.3
             logical name: /dev/sde
             version: 9740
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
mint@mint ~ $ 
```Thank you for all of the help.

---

### Post by amsterdamharu on 2010-12-21
> I installed the video card driver
Is that the driver that was found by Mint 9 (actually is Ubuntu 10.04 with "enhancements")?

---

### Post by thisisdrob on 2010-12-21
Yes

---

### Post by thisisdrob on 2010-12-21
I also tried replacing "quiet splash" with "xforcevesa" and it boots to a black screen.

I really appreciate the help.

---

### Post by thisisdrob on 2010-12-21
I got the installed mint 9 to boot by replacing "quiet splash" with "xforcevesa noacip noacpi".  Am i going to have to do this everytime i want to boot Mint?

---

### Post by amsterdamharu on 2010-12-21
You are lucky.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
> All these Radeon(HD) cards and derivatives have good 3D acceleration support 
Yours is RV770

It should work, I don't see the need to go with the xorg-edgers drivers they can be unstable.
Can you boot normal and press control + alt + F1 when the screen turns black to see if you can get into a terminal?
If no then press control + alt + delete to reboot a live CD
Then when in the live CD check your ubuntu partition for the following file:
/var/log/Xorg.0.log
And post it please. You are stuck to try and install it manually because you have no screen. I will look into what to do if this is the case.

If yes then execute the following command:
```
lsmod | grep agp
```
What is the output of that? (should be one or 2 lines)
You can try to manually re install the driver giving the following command:
```
sudo apt-get install --reinstall xserver-xorg-video-radeon
sudo rm /etc/X11/xorg.conf
```
Note that the X in X11 is upper case. Now press control + alt + delete to reboot.

---

### Post by amsterdamharu on 2010-12-21
Just read your reply, interesting that xforcevesa alone doesn't do anything. This suggest that noacip noacpi would be the solution.

Boot with those options (no xforcevesa) and see if you can get better video support if it does I can tell you how to add these parameters permanently.

---

### Post by thisisdrob on 2010-12-21
Mint will only boot with those three options (xforcevesa noapic noapci).  Mint also says that the proprietary drivers for the radeon hd4800 is installed and active. I also installed all of the updates available. 

Am i always going to have to boot with xforcevesa?

---

### Post by amsterdamharu on 2010-12-21
So you are saying that it doesn't boot if you only add "xforcevesa" and it doesn't boot if you only add "noacip noacpi" and control + alt + F1 doesn't give you a terminal login screen?

If you add "" to the "recovery mode" menu, will it boot you into text only?
If it does you can try the following command and reboot.

```
sudo dpkg-reconfigure xorg
```

---

### Post by amsterdamharu on 2010-12-21
You could try to all these 3 parameters and boot normally but I can't figure out what's going on here, according to ubuntu help your card is supported so it should work.

"noacip noacpi nomodeset"

---

### Post by thisisdrob on 2010-12-21
> Boot with those options (no xforcevesa) and see if you can get better video support if it does I can tell you how to add these parameters permanently.I booted with those options (noapic noapci) without using xforcevesa.  How do i get better video support and also how would i go about adding that permanently so i wouldn't have to type that in everytime?

Thank you for being so patient and helping.

---

### Post by amsterdamharu on 2010-12-21
[http://ubuntuforums.org/showpost.php?p=10263571&postcount=16](http://ubuntuforums.org/showpost.php?p=10263571&postcount=16)
The 2 options "noapic noapci" leaves you with a black screen I assume.

[http://ubuntuforums.org/showpost.php?p=10263672&postcount=18](http://ubuntuforums.org/showpost.php?p=10263672&postcount=18)
I assume that didn't get you in a higher graphic desktop as well

If you add "[COLOR=Red]noapic noapci xforcevesa[/COLOR]" to the "recovery mode" menu, will it boot you into text only?
If it does you can try the following command and reboot.

```
sudo dpkg-reconfigure xorg
```

Sorry forgot to add the red text in my previous post.

At this point it is not a good idea to add xforcevesa permanently because it will allways boot in low graphics mode but you're trying to get better graphics. Any reboot will get you low graphics with that parameter permanently there and there be no way of seeing if any changes worked.

---

### Post by thisisdrob on 2010-12-21
I am not using the xforcevesa parameter... It boots with only using noapci noapic, I don't have to use xforcevesa.

EDIT:
Mint is booting using only the noacpi parameter.  how can i permanently add that parameter so i don't have to type it all of the time?

thanks for all of the help.  I greatly appreciate it.

EDIT AGAIN:
I read about how to edit the grub to automatically include the noapic parameter.  Thanks again for all of the help.

So now it seems that mint boots flawlessly.

---

