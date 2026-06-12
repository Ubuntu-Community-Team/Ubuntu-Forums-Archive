---
title: "cd/dvd drive won't work"
date: 2010-06-20
forum: General Help
---

### Post by Gaambo on 2010-06-20
Hey guys,
i got a brand new Ubuntu 10.04 but can't get my cd/dvd drive to work.
If i insert a dvd it sometimes recognises it but after a couple of minutes it's away.
System - Administration - disk utility says 'no media detected'.
if I try to mount /dev/sr0 it says "no medium found on /dev/sr0" when i try to open it in nautilus it says the same. 
cd/dvd and cd/dvd drive both work fine in win7.
/etc/fstab 
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1	/media/cdrom1	udf,iso9660 user,noauto,exec,utf8 0	  0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
```

ls -ls /dev/ | grep -e cd -e dvd
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:36 cdrom -> sr1
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:41 cdrom1 -> sr0
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:41 cdrw1 -> sr0
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:36 dvd -> sr1
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:41 dvd1 -> sr0
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:41 dvdrw1 -> sr0
0 drwxr-xr-x  2 root root          60 2010-06-20 14:36 pktcdvd
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:41 scd0 -> sr0
0 lrwxrwxrwx  1 root root           3 2010-06-20 12:36 scd1 -> sr1
0 crw-rw----  1 root cdrom    21,   1 2010-06-20 12:36 sg1
0 crw-rw----  1 root cdrom    21,   2 2010-06-20 12:36 sg2
0 brw-rw----+ 1 root cdrom    11,   0 2010-06-20 12:41 sr0
0 brw-rw----+ 1 root cdrom    11,   1 2010-06-20 12:36 sr1

```

```
dmesg | grep cd
``` doesn't say anything.
I searched through forums and google but nothing really worked.
It's a LG drive, i'm using ubuntu 10.04 - 2.6.32-22-generic kernel , also doesn't work on other kernel versions.
anybody an idea what's wrong?

EDIT:
forgot something. also when after a couple of minutes the dvd suddenly disappears from everywhere (places, mount, nautilus, disk utility) the little light on the cd/dvd drive stops blinking - so, could there be anything wrong? for example the drive goes to "standby" mode or something?

---

### Post by frogknowledge on 2010-11-14
I have the same problem, under Computer it shows the icon for the CD/DVD Drive but I can not open it or clicking on it will not work any help guys?

Also noticed that their is no permissions set for it could that be?

---

### Post by rafrosty on 2010-11-15
Likewise, I've searched, tried many things. Alright.
I'm running 10.04 LTS UNR kernel 2.6.32-25-generic on a DELL Desktop 

An error I've often seen while trying to make this work
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

lscpci

00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:08.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)


```

```

sudo lshw

galaxycauldron            
    description: Computer
    product: Dimension 8200
    vendor: Dell Computer Corporation
    serial: FQ7P611
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal cpus=1 power-on_password=enabled uuid=44454C4C-5100-1037-8050-C6C04F363131
  *-core
       description: Motherboard
       product: Dimension 8200
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A03 (12/07/2001)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 2200MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
             physical id: 0
             slot: RIMM1
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
             physical id: 1
             slot: RIMM2
             size: 256MiB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns) [empty]
             physical id: 2
             slot: RIMM3
             clock: 400MHz (2.5ns)
        *-bank:3
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: RIMM4
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82850 850 (Tehama) Chipset Host Bridge (MCH)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82850 850 (Tehama) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fc000000-fdffffff memory:f0000000-f7ffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fc000000-fcffffff memory:f0000000-f7ffffff(prefetchable) memory:fd000000-fd00ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=4096) memory:fe100000-fe2fffff memory:20000000-200fffff(prefetchable)
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:16 ioport:ece0(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 7.1
                bus info: pci@0000:02:07.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:ecd8(size=8)
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax/Voice/Spkp Modem
                vendor: Conexant Systems, Inc.
                physical id: 8
                bus info: pci@0000:02:08.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:fe1f0000-fe1fffff ioport:ecd0(size=8)
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: 9
                bus info: pci@0000:02:09.0
                logical name: eth0
                version: 31
                serial: 00:08:a1:0f:cf:07
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.1.107 latency=64 link=yes maxlatency=40 mingnt=20 multicast=yes
                resources: irq:18 ioport:e800(size=256) memory:fe1efc00-fe1efcff memory:20000000-2003ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800BB-75CA
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMA8E1345528
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002a11c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: b49d29a9-bbb1-4051-878a-81c1a2671130
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-30 19:21:31 filesystem=ext4 lastmountpoint=/[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;k &#65533;j/&#65533;d&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;pwL&#65533;pwL&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;mn modified=2010-10-30 19:51:23 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-15 01:38:59 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1451MiB
                   capacity: 1451MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1451MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff80(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:dcd0(size=16)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff60(size=32)


```

```

sudo gedit /etc/fstab

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
UUID=555a14ad-29d5-46a3-bd11-d14ae53734ff none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

```
mount

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)

```
```
ls -ls /dev/ | grep -e cd -e dvd

0 lrwxrwxrwx  1 root root           3 2010-11-15 01:39 cdrom -> sr0
0 lrwxrwxrwx  1 root root           3 2010-11-15 01:39 cdrom1 -> sr1
0 lrwxrwxrwx  1 root root           3 2010-11-15 01:39 cdrw1 -> sr1
0 lrwxrwxrwx  1 root root           3 2010-11-15 01:39 dvd -> sr0
0 drwxr-xr-x  2 root root          60 2010-11-14 19:38 pktcdvd
0 lrwxrwxrwx  1 root root           3 2010-11-15 01:39 scd0 -> sr0
0 lrwxrwxrwx  1 root root           3 2010-11-15 01:39 scd1 -> sr1
0 crw-rw----  1 root cdrom    21,   1 2010-11-15 01:38 sg1
0 crw-rw----  1 root cdrom    21,   2 2010-11-15 01:38 sg2
0 brw-rw----+ 1 root cdrom    11,   0 2010-11-15 01:39 sr0
0 brw-rw----+ 1 root cdrom    11,   1 2010-11-15 01:39 sr1
```

I tried this and got something interesting.

```
 
sudo mount /dev/sr0

mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab


```

Thanks in advance,

---

### Post by bebop52 on 2010-11-16
Same problem here, first with Lucid 10.04, now with Maverik 10.10. 
This is described often in the web since several years. Some suggest to change boot order (first HD, then CDRom) or to disable CDRom in boot menu. Didn't work for me. 

I change from Windows XP to Ubuntu Lucid - should be a rewarding experience, should'nt it? But reality looks like this: 

(1) I have tons of audioprograms installed - ubuntu seems to be a musicians wet dream. But I can't even hear music or burn CD/DVD since my drive won't work. 

(2) I can't print anymore, because the mantainance buttons for  for my canon pixma ip3000 are greyed out, and the printer needs maintainance urgently. 

I'm only waiting for my monitor to get dark and disfunctional, then I have the worlds best OS with just some marginal I/O problems...

Where are the solutions to these very annoying problems? I couldn't find them, just a lot of problem reports. I hoped upgrading to 10.10 world solve them - but nothing happened. 

This may sound it bit frustrated. I really like linux/emacs, but I need to print and listen and burn too.

---

### Post by TheAnachron on 2010-11-16
bebop52, welcome on the forum.

please open a new thread for your questions. Thank you!

---

