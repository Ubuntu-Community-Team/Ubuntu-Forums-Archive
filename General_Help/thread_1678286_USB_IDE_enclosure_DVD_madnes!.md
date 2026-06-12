---
title: "USB IDE enclosure DVD madnes!"
date: 2011-01-30
forum: General Help
---

### Post by Keduno on 2011-01-30
This has been killing me for the last 2 days, at first I could get Ubuntu to see the controller via lshw, lspci and lsusb, but no more, added /dev/sr0 to /etc/fstab with:

```
/dev/sr0        /media/cdrom    auto    rw,user,noauto,exec,utf8 0       0
```Yet I still couldn't see the drive in Nautilus until I added a folder called "cdrom" in /media, this allowed discs to show up, but they where all called cdrom and Icouldnot access them with any app via GUI, however I could play back a DVD by opening a disc in VLC at /dev/sr0.

All I've been wanting to do this whole time is make an uncompressed .iso image of a DVD, I never expected to have so many issues...

---

### Post by coffeecat on 2011-01-30
If you do a lsusb, do you get this line for the USB enclosure?

```
Bus 001 Device 006: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
```

Ignore the bus and device numbers. If your ID number is the same, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1618085](http://ubuntuforums.org/showthread.php?t=1618085)

I've posted some workarounds and there is some useful discussion with forum members other than the OP (who never re-appeared after posting his rant). 

If yours is not that device then, sorry, I can't help.

---

### Post by Keduno on 2011-01-30
Yep, I get the exact same line from LSUSB the enclosure is a Mapower 5.25" USB2 and Firewire 400 connections, drives I've tried are an NEC ND-3550A and currently a Hitachi GDR-8161B.

I removed the folder from /media and the line from fstab, I can mount the disc with your code of ```
 udisks --mount /dev/sr0 
```But it seems I'd have to do that for every disc and it still seems to not let most apps interact with the disc unless manually directed to /dev/sr0.

LSUSB```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0701 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 001 Device 003: ID 13fe:1e23 Kingston Technology Company Inc. 
Bus 001 Device 002: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```LSPCI```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
```LSHW```
description: Computer
    product: Aspire one
    vendor: Acer
    version: V1.02
    serial: LUS680B0659151C27B1601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal uuid=0DFCD88C-9784-9AE1-5986-00235A868F92
  *-core
       description: Motherboard
       product: Aspire one
       vendor: Acer
       physical id: 0
       version: V1.02
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.02 (03/12/2009)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x4D3420373054323836344548332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0x788C7ADA
             slot: J2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N270   @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1b
          bus info: cpu@0
          version: 6.12.2
          serial: 0001-06C2-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 xtpr pdcm movbe lahf_lm nx cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 1c
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 1d
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GME Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GME Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:56280000-562fffff ioport:50f0(size=8) memory:40000000-4fffffff memory:56300000-5633ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:56200000-5627ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:56340000-56343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:55100000-561fffff ioport:50000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:24:2c:2e:e0:6c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:55100000-5510ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:54100000-550fffff ioport:51000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=8192) memory:53000000-540fffff ioport:52000000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: c0
                serial: 00:23:5a:86:8f:92
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:45 memory:53000000-5303ffff ioport:1000(size=128)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:50a0(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5080(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5060(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5040(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:56344400-563447ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:50c0(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:50d8(size=8) ioport:50fc(size=4) ioport:50d0(size=8) ioport:50f8(size=4) ioport:5020(size=16) memory:56344000-563443ff
           *-disk
                description: ATA Disk
                product: WDC WD1600BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXC209512344
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9a0d38ea
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: be29c457-2e69-f640-8f06-2aac5acdc035
                   size: 7169MiB
                   capacity: 7169MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-04-07 21:19:14 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/ACER
                   version: 3.1
                   serial: 1431df62-7821-0946-bc56-cca15666d204
                   size: 142GiB
                   capacity: 142GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-04-08 13:32:46 filesystem=ntfs label=ACER mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5000(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 3935MiB (4126MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000c5269
           *-volume
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: fa441dac-e777-4349-9b01-950695c6cda7
                size: 3933MiB
                capacity: 3933MiB
                capabilities: primary bootable ext2 initialized
                configuration: filesystem=ext2 modified=2011-01-30 15:57:33 mount.fstype=ext2 mount.options=rw,relatime,errors=remount-ro mounted=2011-01-28 16:19:04 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:4
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD reader
             product: DVD-ROM GDR8161B
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom4
             logical name: /dev/dvd4
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/disk
             version: 0042
             capabilities: removable audio dvd
             configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom4
                logical name: /media/disk
                configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 10/12/2007
       serial: Battery 0
       slot: Fake
```DPKG-QUERY```
520    libgdata7
520    libhtml-tree-perl
520    libparted0debian1
520    python-twisted-names
528    libsndfile1
528    ncurses-bin
532    byobu
532    erlang-inets
532    erlang-xmerl
532    gucharmap
532    simple-scan
532    x11-xserver-utils
532    xfonts-scalable
536    libgstfarsight0.10-0
536    liboil0.3
540    python-dbus
540    xserver-xorg-video-openchrome
544    brasero
544    fontconfig
544    hplip
544    libgcrypt11
544    libglu1-mesa
544    libvisual-0.4-plugins
548    aspell-en
552    consolekit
552    libgdk-pixbuf2.0-0
552    libxml-twig-perl
556    gnome-applets
556    wget
560    libpixman-1-0
564    defoma
564    mlocate
568    python-epsilon
580    gtk2-engines-pixbuf
580    libgtk2.0-common
580    liborbit2
584    apt-utils
588    sane-utils
592    libmng1
592    python-crypto
592    tsclient
592    ttf-khmeros-core
596    libthai-data
596    python-mechanize
600    libpostproc51
604    dbus
604    libgphoto2-port0
604    libical0
604    sudo
608    dhcp3-common
612    libvpx0
612    light-themes
616    libwpd8c2a
616    usbutils
616    zip
620    x11-utils
624    libgtkspell0
628    transmission-common
632    libdirac-decoder0
636    libgd2-xpm
640    telepathy-salut
640    usb-modeswitch-data
640    x11-common
644    foomatic-db-compressed-ppds
644    upstart
648    lshw
652    libgnomeui-0
652    lp-solve
652    memtest86+
656    myspell-en-au
660    gconf-editor
660    gnupg-agent
660    libsvga1
660    metacity
660    xserver-xorg-video-sis
664    libfreetype6
668    evince
668    totem-plugins
672    dhcp3-client
672    system-config-printer-common
676    compiz-core
676    libmjpegtools-1.9
680    libprotoc6
680    python-pexpect
680    python-zope.interface
684    bogofilter-common
684    psmisc
684    rsync
688    gnome-nettool
688    libsqlite3-0
692    libgmp3c2
692    libgpgme11
692    libmpfr4
692    myspell-en-za
692    python-telepathy
692    samba-common
696    libpulse0
696    python-gtksourceview2
700    python-apport
704    python-chardet
704    tar
712    ntfsprogs
712    rsyslog
720    bogofilter-bdb
720    vim-tiny
728    jockey-common
728    libbonobo2-0
728    libgnomevfs2-0
732    cups-driver-gutenprint
732    dnsmasq-base
732    libqt4-dbus
736    ca-certificates
744    libtag1-vanilla
744    libxml-parser-perl
748    libxvidcore4
752    procps
752    python
756    libschroedinger-1.0-0
760    libmono-addins0.2-cil
760    python-gnome2
760    xdg-user-dirs
768    bsdmainutils
768    hunspell-en-us
772    libtheora0
776    modemmanager
780    hunspell-en-ca
780    libgnome2-vfs-perl
784    console-terminus
784    python-apt
788    libgtkhtml3.14-19
796    libdirac-encoder0
804    system-tools-backends
804    ufw
820    openjdk-6-jre
824    libmatroska2
824    libmp4v2-0
824    libnet-dbus-perl
832    xfonts-encodings
840    ibus-table
840    myspell-en-gb
840    notify-osd
844    openssl
852    libpango1.0-0
856    libopenexr6
856    libswscale0
856    onboard
864    libstlport4.6ldbl
864    wodim
872    media-player-info
876    libkrb5-3
884    adduser
884    libpango-perl
884    pnm2ppa
892    pciutils
896    libquicktime1
896    libsnmp-base
896    wpasupplicant
900    cpio
900    pppconfig
904    librpc-xml-perl
904    login
912    evince-common
912    foomatic-db-engine
912    tcpdump
924    libmtp8
924    python-couchdb
928    libgstreamer-plugins-base0.10-0
932    debconf
940    python-gst0.10
952    libclutter-1.0-0
960    libnewt0.52
960    sed
964    language-pack-en
964    python-gobject
964    python-libxml2
972    net-tools
972    python-mako
976    python-ubuntuone-client
984    libcamel1.2-14
984    metacity-common
988    libprotobuf6
988    xserver-xorg-video-intel
996    libvte9
1000    gnome-desktop-data
1000    libvlccore4
1000    p7zip
1004    gvfs
1004    iproute
1004    libelf1
1004    python-pygoocanvas
1008    libexempi3
1008    udisks
1012    gnome-terminal-data
1020    screen
1020    wamerican
1020    wbritish
1036    bash-completion
1044    update-manager-core
1048    dictionaries-common
1048    ibus-pinyin
1052    kiso
1056    libsilc-1.1-2
1060    libgnome2-perl
1064    icedtea-6-jre-cacao
1064    libsane-hpaio
1068    pidgin-plugin-pack
1072    libboost-regex1.42.0
1072    libgtksourceview2.0-common
1076    libwww-perl
1084    ppp
1084    python-xapian
1088    gtk2-engines
1096    libcaca0
1100    libpam-modules
1108    gnome-bluetooth
1108    manpages
1112    gnome-control-center
1112    libgtop2-common
1116    python-feedparser
1124    gnome-panel
1124    grep
1124    python-imaging
1128    libx264-98
1128    nautilus-data
1132    mousetweaks
1140    debconf-i18n
1140    xscreensaver-gl
1148    libglib-perl
1164    pidgin-musictracker
1168    libstdc++6
1176    libgnutls26
1180    zenity
1184    gnome-settings-daemon
1192    libbrasero-media1
1208    make
1212    bash
1224    libmagickwand3
1232    libevdocument3
1232    xserver-xorg-video-radeon
1256    bluez
1256    libslang2
1256    python-axiom
1264    gstreamer0.10-plugins-ugly
1272    speech-dispatcher
1280    libtelepathy-glib0
1284    apparmor
1288    xterm
1292    mono-gmcs
1300    branding-ubuntu
1300    mono-csharp-shell
1304    libasound2
1304    libglibmm-2.4-1c2a
1312    gnome-search-tool
1328    hicolor-icon-theme
1336    diffutils
1352    libcairo2
1352    network-manager
1356    libx11-6
1388    libperl5.10
1396    console-setup
1400    file-roller
1404    genisoimage
1416    busybox-static
1424    hplip-cups
1428    gnome-accessibility-themes
1444    gcalctool
1444    ttf-ubuntu-font-family
1456    hwdata
1468    libdb4.8
1480    udev
1484    seamonkey-chatzilla
1492    python-tagpy
1504    totem
1508    python-rdflib
1512    gpac
1512    libsamplerate0
1524    system-config-printer-gnome
1544    telepathy-gabble
1560    libvorbisenc2
1564    bleachbit
1576    kbd
1580    libxml2
1584    libdns66
1588    libc-bin
1596    libdjvulibre21
1600    python-papyon
1616    iptables
1620    eog
1620    util-linux
1644    libxapian15
1648    libqt4-network
1648    mjpegtools
1652    libwxbase2.8-0
1656    update-manager
1660    python-configobj
1664    pidgin
1684    libexif12
1692    lftp
1700    libbonoboui2-common
1704    sgml-data
1712    findutils
1712    hpijs
1724    libgstreamer0.10-0
1724    ttf-liberation
1736    libexiv2-6
1740    vinagre
1752    tesseract-ocr-eng
1756    nano
1760    python-twisted-conch
1788    libavformat52
1820    pitivi
1836    totem-common
1840    gedit-common
1844    libssl0.9.8
1860    w3m
1868    gedit
1900    gstreamer0.10-plugins-base
1916    tzdata-java
1928    python-twisted-web
1936    espeak-data
1948    alsa-utils
1948    libpoppler7
1988    software-center
2000    brasero-common
2020    man-db
2040    x11-apps
2044    menu
2056    openssh-client
2060    gnome-system-log
2064    python-coherence
2088    libgladeui-1-9
2148    network-manager-gnome
2156    e2fsprogs
2160    gvfs-backends
2188    language-pack-gnome-en
2260    gnome-system-tools
2272    gnome-panel-data
2304    gdm
2308    libgsl0ldbl
2312    gnome-themes-ubuntu
2316    grub-pc
2340    libaspell15
2340    libdirectfb-1.2-9
2372    pulseaudio
2424    command-not-found-data
2432    libpython2.6
2436    capplets-data
2440    passwd
2464    gnome-disk-utility
2464    gnome-media-common
2476    language-selector-common
2488    docbook-xml
2508    libx11-data
2532    couchdb-bin
2548    libgtk2.0-cil
2560    libmagic1
2592    ttf-dejavu-core
2604    compiz-plugins
2616    synaptic
2628    python-gtk2
2628    ttf-indic-fonts-core
2636    seahorse
2644    libwebkit-1.0-common
2648    openprinting-ppds
2680    libmono-corlib2.0-cil
2724    gnome-dictionary
2764    checkbox
2764    libnss3-1d
2772    gnome-keyring
2776    tomboy
2796    gnome-user-guide-en
2804    guile-1.8-libs
2840    libglib2.0-0
2840    libvala-0.10-0
2988    libsnmp15
3036    nautilus
3044    tesseract-ocr
3108    transmission-gtk
3128    syslinux-common
3232    tcl8.4
3240    manpages-dev
3280    compiz-fusion-plugins-main
3288    mencoder
3348    groff-base
3352    grub-common
3352    shared-mime-info
3384    xkb-data
3392    libgpac0.4.5
3400    p7zip-full
3408    libgnomevfs2-common
3460    python-nevow
3496    ibus
3500    baobab
3508    libgucharmap7
3520    dmz-cursor-theme
3536    mono-runtime
3540    libfftw3-3
3552    ibus-pinyin-db-android
3648    ubuntu-wallpapers
3712    xserver-xorg-core
3828    gnome-user-guide
3896    libgtk2-perl
3940    vlc
4060    libgtkmm-2.4-1c2a
4076    gdb
4100    xcursor-themes
4176    cups-common
4180    gstreamer0.10-plugins-good
4204    ttf-freefont
4300    linux-libc-dev
4372    tcl8.5
4388    gnome-mime-data
4408    gnome-orca
4464    gnome-power-manager
4476    xfonts-75dpi
4508    libmono-system2.0-cil
4512    perl-base
4556    gnome-doc-utils
4568    yelp
4584    gstreamer0.10-plugins-bad
4624    libgweather-common
4628    liblouis-data
4764    gsfonts
4808    xfonts-100dpi
4896    gcc-4.4
4896    python2.6-minimal
4956    libpurple0
5004    ubuntu-mono
5148    libgtk2.0-0
5184    ttf-wqy-microhei
5212    gnupg
5216    example-content
5260    language-pack-en-base
5384    mplayer
5404    geoip-database
5456    ttf-thai-tlwg
5544    gnome-system-monitor
5648    libgphoto2-2
5732    seamonkey-mailnews
5788    ttf-dejavu-extra
5852    libmagickcore3
5892    foo2zjs
5900    brltty
5920    binutils
5968    apt
6008    dpkg
6084    libsmbclient
6200    ttf-takao-pgothic
6276    tzdata
6640    mkvtoolnix
6744    libgutenprint2
7032    gnome-screensaver
7060    python-twisted-core
7224    notify-osd-icons
7268    gnome-applets-data
7304    erlang-base
7412    libqtcore4
7644    shotwell
8012    openjdk-6-jre-lib
8016    libqt3-mt
8180    cups
8272    xfonts-base
8476    vlc-nox
8484    libopencc1
8488    libgs8
8640    cpp-4.4
9008    python2.6
9088    libwxgtk2.8-0
9280    locales
9476    libc6
9812    linux-headers-2.6.35-25-generic
10036    ghostscript
11016    kdelibs5-data
11052    libavcodec52
11152    gnome-icon-theme
12012    hplip-data
12304    libqtgui4
12580    ttf-unfonts-core
12636    iso-codes
12648    coreutils
12828    libsane
13308    perl
14780    libwebkit-1.0-2
14924    language-pack-gnome-en-base
15852    perl-modules
16580    samba-common-bin
19104    libc6-dev
19240    libicu42
19836    libflite1
22776    vlc-data
24212    xulrunner-1.9.2
25636    linux-firmware
26352    app-install-data
27336    pidgin-data
27388    kdelibs-data
27572    humanity-icon-theme
27984    kdelibs4c2a
29920    firefox
30944    osmos
32456    seamonkey-browser
33224    freepats
41320    smbclient
41732    libgl1-mesa-dri
57288    songbird
78284    linux-headers-2.6.35-25
78712    openjdk-6-jre-headless
104636    linux-image-2.6.35-22-generic
104664    linux-image-2.6.35-23-generic
104696    linux-image-2.6.35-24-generic
104732    linux-image-2.6.35-25-generic
133840    ubuntu-docs
```

---

### Post by coffeecat on 2011-01-30
There is nothing else, that I know of, that you can do in Maverick apart from the various workarounds I posted in the thread I linked earlier. But you could do a me too on the Launchpad bug I linked to there. Not that I think it is likely to get fixed in Maverick. The realistic fact is that developer time is limited and other external CD/DVD devices seem to be working just fine in Maverick - it's this particular enclosure that is the problem.

The good news is that it works fine in Natty. I've just tried it in a fully-updated Natty Alpha and data CD/DVDs, music CDs and video DVDs are recognised and automounted without any problem.

---

