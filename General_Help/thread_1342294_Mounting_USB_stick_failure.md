---
title: "Mounting USB stick failure"
date: 2009-11-30
forum: General Help
---

### Post by Sooda on 2009-11-30
Hello, I am trying to get working my USB stick on Ubuntu, long time ago (with older kernel) USB stick was even auto-
detected if it was connected when I turned on computer. I would like to get automatic mounting working, manual mounting is
only partial solution though helps also much.

I have made sure that USB stick works perfectly fine on MS Windows XP SP3, I connected it, browsed USB stick properties and
played music file which is on pen drive.

Sorry for wall of text, I want this problem solved and give as much useful information as it is needed to solve it. I check after some days, so take your time. I have myself put this USB stick problem many times aside and waited "better times".
Looks like it has lastly arrived.

USB stick specifications:

Kingston 4GB DataTraveler 101  2.0 USB (manufacturer code: DT101C/4GB)
Windows "code": Kingston DT 101 II USB Device
Its file system is FAT32 (used space 1.13 GB, free 2.59 GB, total 3.72 GB).

My operating system (OS) is Ubuntu 9.04 Jaunty Jackalope (KDM), uname -a gives:

tonis@tonis-desktop:~$ uname -a
Linux tonis-desktop 2.6.28-16-generic #57-Ubuntu SMP Wed Nov 11 09:47:24 UTC 2009 i686 GNU/Linux



lsusb (without USB stick)

tonis@tonis-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tonis@tonis-desktop:~$ 

dmesg | tail (without USB stick)

tonis@tonis-desktop:~$ dmesg | tail
[  221.507647] type=1505 audit(1259609749.590:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3934
[  233.884779] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  233.884787] Bluetooth: BNEP filters: protocol multicast
[  234.017696] Bridge firewalling registered
[  240.517778] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[  240.517813] agpgart-via 0000:00:00.0: putting AGP V2 device into 2x mode
[  240.517863] nvidia 0000:01:00.0: putting AGP V2 device into 2x mode
[  241.009073] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[  251.356041] eth2: no IPv6 routers present
[ 2790.664107] usb 1-1: USB disconnect, address 2
tonis@tonis-desktop:~$ 

NOTE: USB disconnect, address 2 is my Identification Card Reader which uses USB port for connection, works fine.
I un-pluged it to plug-in USB stick. Card Reader is not shown in first lsusb because I disconnected Card Reader and
then used first time lsusb.

lsusb (with USB stick in "usb 1-1" port)

tonis@tonis-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
tonis@tonis-desktop:~$

dmesg (with USB stick in "usb 1-1" port, I started copying where first dmesg ended)

[ 3807.952382] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 3808.180669] usb 1-1: configuration #1 chosen from 1 choice
[ 3808.475515] Initializing USB Mass Storage driver...
[ 3808.480280] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3808.481264] usbcore: registered new interface driver usb-storage
[ 3808.481275] USB Mass Storage support registered.
[ 3808.554268] usb-storage: device found at 4
[ 3808.554278] usb-storage: waiting for device to settle before scanning
[ 3813.553592] usb-storage: device scan complete
[ 3813.580097] scsi 2:0:0:0: Direct-Access     Kingston DT 101 II        1.00 PQ: 0 ANSI: 2
[ 3813.598466] sd 2:0:0:0: [sdb] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[ 3813.603490] sd 2:0:0:0: [sdb] Write Protect is off
[ 3813.603533] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 3813.603544] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3813.677413] sd 2:0:0:0: [sdb] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[ 3813.687847] sd 2:0:0:0: [sdb] Write Protect is off
[ 3813.687885] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 3813.687897] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3813.687958]  sdb:<6>usb 1-1: reset full speed USB device using uhci_hcd and address 4
[ 3814.272130] usb 1-1: device descriptor read/64, error -84
[ 3814.752129] usb 1-1: device descriptor read/64, error -84
[ 3814.968149] usb 1-1: reset full speed USB device using uhci_hcd and address 4
[ 3815.236829] usb 1-1: device descriptor read/64, error -84
[ 3815.676109] usb 1-1: device descriptor read/64, error -84
[ 3815.892238] usb 1-1: reset full speed USB device using uhci_hcd and address 4
[ 3816.528652] usb 1-1: device not accepting address 4, error -84
[ 3816.640141] usb 1-1: reset full speed USB device using uhci_hcd and address 4
[ 3817.048398] usb 1-1: device not accepting address 4, error -32
[ 3817.048598] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.048607] end_request: I/O error, dev sdb, sector 0
[ 3817.048619] Buffer I/O error on device sdb, logical block 0
[ 3817.048800] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.048807] end_request: I/O error, dev sdb, sector 0
[ 3817.048812] Buffer I/O error on device sdb, logical block 0
[ 3817.048939] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.048946] end_request: I/O error, dev sdb, sector 0
[ 3817.048951] Buffer I/O error on device sdb, logical block 0
[ 3817.049055] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049062] end_request: I/O error, dev sdb, sector 0
[ 3817.049067] Buffer I/O error on device sdb, logical block 0
[ 3817.049169] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049176] end_request: I/O error, dev sdb, sector 0
[ 3817.049181] Buffer I/O error on device sdb, logical block 0
[ 3817.049197] ldm_validate_partition_table(): Disk read failed.
[ 3817.049291] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049298] end_request: I/O error, dev sdb, sector 0
[ 3817.049303] Buffer I/O error on device sdb, logical block 0
[ 3817.049405] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049412] end_request: I/O error, dev sdb, sector 0
[ 3817.049417] Buffer I/O error on device sdb, logical block 0
[ 3817.049518] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049526] end_request: I/O error, dev sdb, sector 0
[ 3817.049531] Buffer I/O error on device sdb, logical block 0
[ 3817.049633] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049640] end_request: I/O error, dev sdb, sector 0
[ 3817.049645] Buffer I/O error on device sdb, logical block 0
[ 3817.049660] Dev sdb: unable to read RDB block 0
[ 3817.049753] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049760] end_request: I/O error, dev sdb, sector 0
[ 3817.049765] Buffer I/O error on device sdb, logical block 0
[ 3817.049867] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.049874] end_request: I/O error, dev sdb, sector 0
[ 3817.050004] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.050011] end_request: I/O error, dev sdb, sector 24
[ 3817.050112] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.050119] end_request: I/O error, dev sdb, sector 24
[ 3817.050222] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.050229] end_request: I/O error, dev sdb, sector 0
[ 3817.050332] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3817.050339] end_request: I/O error, dev sdb, sector 0
[ 3817.050353]  unable to read partition table
[ 3817.072410] usb 1-1: USB disconnect, address 4
[ 3817.074163] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3817.074306] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 3817.212175] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 3817.339259] usb 1-1: device descriptor read/64, error -32
[ 3817.587245] usb 1-1: device descriptor read/64, error -32
[ 3817.800124] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 3817.920102] usb 1-1: device descriptor read/64, error -32
[ 3818.144185] usb 1-1: device descriptor read/64, error -32
[ 3818.360207] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 3818.768276] usb 1-1: device not accepting address 7, error -32
[ 3818.883127] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 3819.292136] usb 1-1: device not accepting address 8, error -32
[ 3819.292194] hub 1-0:1.0: unable to enumerate USB device on port 1
tonis@tonis-desktop:~$ 

Lines which arise questions:
1. [ 3813.687958]  sdb:<6>usb 1-1: reset full speed USB device using uhci_hcd and address 4
1. Why reset? What it does reset?

2. [ 3814.272130] usb 1-1: device descriptor read/64, error -84
2. What means that?

3. [ 3817.339259] usb 1-1: device descriptor read/64, error -32
3. Again what means that?

With sudo lshw command some useful USB and more info,:

        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 1a
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd


Motherboard and processor info:

    description: Desktop Computer
    product: VT82C694X
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 694X-686B
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (04/12/2002)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(TM) CPU                1200MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.11.1
          slot: Socket 370
          size: 1200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up

I/O errors are supposedly devices going into sleep and waking up (Network Interface Card - NIC perhaps?)
Lastly uname -m gives: i686, so I got this older OS type (32 bit?).

---

### Post by Sooda on 2009-12-13
Pump

---

### Post by hang-time on 2009-12-28
looking for a solution too

26mb of "reset full speed USB device using uhci_hcd and address 2" error logs

no USB mass storage - but USB mouse keyboard and headset

---

