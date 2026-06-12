---
title: "dvb-t works better under ubuntu than windows!"
date: 2006-04-11
forum: General Help
---

### Post by easyease on 2006-04-11
i bought an artec dvb-t usb device a couple of weeks ago and found it very awkward to use under windows(jerky picture and sound, and naff software), just today i installed kaffeine player using the xine engine plug in and its way better. the picture is crystal clear and i can even pick up more channels than by using the windows software that was supplied. the tv guide function in kaffeine is better than the artec software too.
its even better for recording programs because i can record to a program stream mpg format rather than the transport stream format that the windows software provides.
 this is the day windows is redundent in my house!:-D

---

### Post by T*&amp;1p87)v# on 2006-04-11
thats great,

I am thinking of buying such kind of device myself, can you post more specific info on the device and soft you are using, also your hardware configuration.
thanks a lot

---

### Post by easyease on 2006-04-11
yeah sure mate. ill post more details here this evening.
here is the device as listed on ebay.
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=9710305340&sspagename=ADME%3AB](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=9710305340&sspagename=ADME%3AB)

---

### Post by easyease on 2006-04-11
heres my results from my a lshw, not sure you will need to know all this but might as well copy and paste it all......
 description: Desktop Computer
    product: VT8363
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8363A-686B
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (07/06/2001)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.2
          slot: Socket A
          size: 1GHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 256KB
     *-cache UNCLAIMED
          description: L2 cache
          physical id: b
          slot: External Cache
          size: 256KB
          capacity: 256KB
          capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 1f
          slot: System board or motherboard
          size: 384MB
          capacity: 512MB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 128MB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: BANK_1
             size: 128MB
        *-bank:2
             description: DIMM
             physical id: 2
             slot: BANK_2
             size: 128MB
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: BANK_3
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: e0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e0000000-e3ffffff
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 440]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e4000000-e4ffffff iomemory:d0000000-d7ffffff iomemory:d8000000-d807ffff irq:11
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:d000-d00f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   description: ATA Disk
                   product: QUANTUM FIREBALLlct15 20
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: A01.0F00
                   serial: 313012016890
                   size: 19GB
                   capacity: 19GB
                   capabilities: ata dma lba iordy smart security pm
                   configuration: mode=udma4 smart=on
              *-disk:1
                   description: ATA Disk
                   product: Maxtor 6L080L0
                   vendor: Maxtor
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   version: BAJ41G10
                   serial: L22FJMEG
                   size: 74GB
                   capacity: 74GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma5 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: DVD reader
                   product: HITACHI DVD-ROM GD-5000
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 0212
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: SONY CD-RW CRX145E
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.0b
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d400-d41f irq:10
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@00:07.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:d800-d81f irq:10
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@00:09.0
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e000-e01f irq:12
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: MOD3000 BOX
                   vendor: DiBcom SA
                   physical id: 2
                   bus info: usb@3:2
                   version: 0.01
                   capabilities: usb-1.00
                   configuration: driver=DiBcom based USB Budget DVB-T device maxpower=500mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 9.1
             bus info: pci@00:09.1
             version: 61
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e400-e41f irq:5
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Audio device
                   vendor: Mustek Systems, Inc.
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.00
                   capabilities: usb-1.10 audio-control
                   configuration: driver=snd-usb-audio maxpower=80mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: F8E842-DL Mouse
                   vendor: Belkin
                   physical id: 2
                   bus info: usb@4:2
                   version: 2.70
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             resources: irq:9
        *-network:0
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@00:08.0
             logical name: eth0
             version: 08
             serial: 00:02:b3:5d:7a:42
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A ip=192.168.2.100 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:e7102000-e7102fff ioport:dc00-dc3f iomemory:e7000000-e70fffff irq:11
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 9.2
             bus info: pci@00:09.2
             version: 63
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:e7100000-e71000ff irq:10
           *-usbhost
                product: VIA Technologies, Inc. USB 2.0
                vendor: Linux 2.6.12-10-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=4 speed=480.0MB/s
        *-usb:5
             description: USB Controller
             product: USS-312 USB Controller
             vendor: Agere Systems (former Lucent Microelectronics)
             physical id: a
             bus info: pci@00:0a.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd
             resources: iomemory:e7101000-e7101fff irq:5
           *-usbhost
                product: Agere Systems (former Lucent Microelectronics) USS-312 USB Controller
                vendor: Linux 2.6.12-10-386 ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: b
             bus info: pci@00:0b.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=C-Media PCI
             resources: ioport:e800-e8ff irq:10
        *-network:1 DISABLED
             description: Ethernet interface
             product: 3c905 100BaseTX [Boomerang]
             vendor: 3Com Corporation
             physical id: c
             bus info: pci@00:0c.0
             logical name: eth1
             version: 00
             serial: 00:60:97:62:ea:90
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=half link=no multicast=yes port=MII speed=10MB/s
             resources: ioport:ec00-ec3f irq:11

kaffeine automatically detected the device and it works a lot better than the windows software included. i couldnt help laugh reading this thread on another forum where a bunch of windows users where getting stressed about the product.....
[http://forum.digitalspy.co.uk/board/showthread.php?t=190364](http://forum.digitalspy.co.uk/board/showthread.php?t=190364)

---

### Post by T*&amp;1p87)v# on 2006-04-11
Thanks,

Well I assume you have the nvidia proprietary drivers installed and all that.
The problem is that I do not know if my ati9600 mobility will be good enogh to fire up this baby. And I hope I will have the same luck with kaffeine :)

---

### Post by easyease on 2006-04-11
fingers crossed! hope it all works as easily for you as it has for me. just make sure you set the player engine to the kaffeine-xine instead of the gstreamer, then restart kaffeine.

---

### Post by easyease on 2006-06-17
uh oh, just upgraded to dapper yesterday and its not letting me install the kaffeine-xine engine that it needs to work!!!!!!!!!!!!!!!!
 looks like im downgrading back to breezy tomorrow..........

---

