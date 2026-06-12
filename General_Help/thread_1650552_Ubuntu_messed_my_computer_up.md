---
title: "Ubuntu messed my computer up"
date: 2010-12-21
forum: General Help
---

### Post by bradsha on 2010-12-21
Well i just installed ubuntu and the apps i wish to use and well where do i start its freezing  sounds crashing then my internet goes and most apps are crashing it makes the desktop unuseble. It works really well for like a haf an hour then crashes  i never had this problem in windows witch i had on here before i may go back unless i can find some kind of fix. :(

---

### Post by matt_symes on 2010-12-21
That's ironic. I just reinstalled windows on a partition and the same thing happened to me.

---

### Post by bradsha on 2010-12-21
Does any one know what i can do ?

---

### Post by wojox on 2010-12-21
What are your system specs?

Did you check Hardware Drivers for any video driver?

You are using 9.10 Karmic Koala?

---

### Post by bradsha on 2010-12-21
My computer is a acer it has  4 gigs of ram it has its nvdia drivers are installed. And no im on 10.10. and now my icons wount change. and my sound just  cut out great!   im not sure whats going on......

---

### Post by amsterdamharu on 2010-12-21
Maybe your computer has some hardware that doesn't play well with Ubuntu. Let's see what you got there:
Can you press alt + F2 and type "gnome-terminal"
Then copy and paste the following command in the terminal (use left mouse in terminal and choose paste).
```
sudo lshw
```Now select all the text in the terminal and paste it here.

---

### Post by bradsha on 2010-12-21
```
dylannator-aspire-x3300   
    description: Desktop Computer
    product: Aspire X3300
    vendor: Acer
    serial: PTSBX02020005033AB3000
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=F97366C0-CDE1-11D3-A40C-DEFC726D6194
  *-core
       description: Motherboard
       product: WMCP78M
       vendor: Acer
       physical id: 0
     *-firmware
          description: BIOS
          vendor: AMI
          physical id: 0
          version: P01-A3 (08/10/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X2 215 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) II X2 215 Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: [empty]
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: [empty]
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: ACR256X64D3U1333C9
             vendor: Kingston
             physical id: 2
             serial: 2BBE30B2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: ACR256X64D3U1333C9
             vendor: Kingston
             physical id: 3
             serial: 2AE730B2
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP78S [GeForce 8200] LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:4f00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:fbf80000-fbffffff
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fbf7f000-fbf7ffff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fbf7ec00-fbf7ecff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fbf7d000-fbf7dfff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fbf7e800-fbf7e8ff
     *-ide
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:fbf78000-fbf7bfff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-storage
          description: SATA controller
          product: MCP78S [GeForce 8200] AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi2
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi ht ahci_1.0 bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:43 ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=16) memory:fbf76000-fbf77fff
        *-disk
             description: ATA Disk
             product: WDC WD6400AAKS-2
             vendor: Western Digital
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WCASY8652058
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0009839c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 03a18790-e334-43e8-83d4-ff8983b126cb
                size: 585GiB
                capacity: 585GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-12-21 16:02:31 filesystem=ext4 lastmountpoint=/&#65533;k&#65533;&#65533;&#65533;&#65533;Z&&#65533;n&#65533;&#65533;&#65533;&#65533;S&#65533;&#65533;&#65533;@B&#65533;&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;k&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-12-21 16:09:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-12-21 17:00:22 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 10GiB
                capacity: 10GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 10GiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH41N
             vendor: HL-DT-ST
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: MN01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:26:2d:22:df:17
          size: 100MB/s
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.2 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:44 memory:fbf7c000-fbf7cfff ioport:b880(size=8) memory:fbf7e400-fbf7e4ff memory:fbf7e000-fbf7e00f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht normal_decode bus_master cap_list
          resources: ioport:d000(size=4096) memory:fc000000-fdefffff ioport:f0000000(size=167772160)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:20 memory:fc000000-fcffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:dc00(size=128) memory:fdee0000-fdefffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:10.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40
     *-pci:3
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:4
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 13
          bus info: pci@0000:00:13.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:e000(size=4096) memory:fdf00000-fdffffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6315 Series Firewire Controller
             vendor: VIA Technologies, Inc.
             physical id: 0
             bus info: pci@0000:05:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=0
             resources: irq:17 memory:fdfff800-fdffffff ioport:e800(size=256)
     *-pci:5
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: d
          bus info: usb@1:3
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@8:0.0.1
             logical name: /dev/sdc
     *-scsi:1
          physical id: e
          bus info: usb@2:5
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sdd
             size: 3819MiB (4005MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=15774c20
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@9:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/98AC-A7E4
                version: FAT32
                serial: 98ac-a7e4
                size: 3818MiB
                capacity: 3819MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
```

---

### Post by amsterdamharu on 2010-12-21
Ok, I got this out of the stuff you posted:
Graphics: Nvidia GeForce 8200
Audio: nVidia MCP72XE/MCP72P/MCP78U/MCP78S

Could be so kind and edit your previous post to wrap the text in code tags so it's easier to read?

If you copy and paste the following command in a terminal does it give any output?
```
lsmod | grep nvidia
```Does the following give you any output?
```
lsmod | grep nouv
```As for your audio problems; could you post the output of the following command?
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by bradsha on 2010-12-21
```

```lsmod | grep nvidia```

```

lsmod | grep nouv gives me no input just blank 

```

```cat /proc/asound/card0/codec#* | grep Codec```

```

---

### Post by bradsha on 2010-12-21
I have no idea how to put the codes in sorry but 

dylannator@dylannator-Aspire-X3300:~$ lsmod | grep nvidia   
nvidia              10221046  38 
 
dylannator@dylannator-Aspire-X3300:~$ lsmod | grep nouv
dylannator@dylannator-Aspire-X3300:~$ 


dylannator@dylannator-Aspire-X3300:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
Codec: Nvidia MCP77/78 HDMI

---

### Post by amsterdamharu on 2010-12-21
> I have no idea how to put the codes inYou did fine, there are 2 soundcards available? I can't find the nvidia in the supported audio models but ALC888 has many subsettings won't mention all of them but here are some:
```
3stack-dig    3-jack with SPDIF I/O
6stack-dig    6-jack digital with SPDIF I/O
3stack-6ch    3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
acer-aspire    Acer Aspire 9810
acer-aspire-4930g Acer Aspire 4930G
acer-aspire-6530g Acer Aspire 6530G
acer-aspire-7730g Acer Aspire 7730G
acer-aspire-8930g Acer Aspire 8930G
```Could not find your aspire x3300 but we can try the "3stack-6ch". Could you press alt + F2 and copy paste the following:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```Add this as the last line if there is no other line starting with "aptions snd-hda-intel":
```
options snd-hda-intel model=3stack-6ch
```Your nvidia drivers are loaded and should not give you a problem. We can see if some kernel arguments can help you.
Can you press alt + F2 and copy paste the following:
```
gksu gedit /etc/default/grub
```replace the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```with
```
GRUB_CMDLINE_LINUX_DEFAULT="noapic noapci nosplash"
```And save the file
Press alt + F2 and copy paste "gnome-terminal", then copy paste the following command:
```
sudo update-grub
```Now choose reboot, you will get a lot more output during the startup.

After a reboot can you press alt + F2 and type "pavucontrol" this should give you the volume control. In the "input devices" tab you can play around with the microphone settings check to see if it works (unmute and see if the green bar in the bottom moves when you blow in the mic). This because a lot of times the mic doesn't work.

I will be out for a while, hope this will get you a bit stabler system.

---

### Post by 3rdalbum on 2010-12-22
If you're getting crashes, the very first thing I'd check is your RAM. If you can, take out one of your RAM sticks and if the problem still occurs, put it back and take out a different one. Repeat until the problem goes away. Usually, unexplained crashes and glitches on Linux are due to faulty RAM and as far as I know there's no software that will reliably catch bad RAM (Memtest is pretty close to useless).

---

### Post by bradsha on 2010-12-22
Well my usb headset no longer working i hope this  helps the sound i did it all . Im gonna try to bring my comp in tomorrow hopefully  to check it out casue in no way am i blaming ubutnu i think it mite be my comp with working with ubuntu witch so far seems to not going so good

---

### Post by colobix on 2010-12-22
Have you enabled your graphics card yet? if not, this can't be a graphic card issue.
I would start with the system files to see if there are something wrong here. Maybe something happened during the installation like a corrupt file or package somewhere.
So, go to synaptic (system > admin > synaptic package manager) and from the "edit" menu, go to "repair broken packages".
This will (as it says), repair broken packages on your system.
Synaptic is your package manager where you can find, install or remove things on your system.
You can also check your installation from the terminal and see if everything has been installed correctly. 
```
sudo apt-get install -f,
```

---

### Post by amsterdamharu on 2010-12-22
> Well my usb headset no longer working
Did you add the line "options snd-hda-intel model=3stack-6ch" that might make the sound card in you computer work but not the usb.

I asked "there are 2 sound cards available?"
And with your usb remark you answered me.

Does the on board sound card work and does it break when you start using the headset?

Did adding the kernel parameters make it crash less (make it crash at all)?

You just bought this system and had no problems with Windows, it's unlikely a memory issue or the timing must have been just right.

When you start "pavucontrol" (alt + F2 and type pavucontrol) is there any way to choose what sound device to use (like in the configuration tab)?

I doubt someone there will fix Linux problems for you but you can try, sound in Linux is a pain so maybe you should try your on board card with a microphone first to see if that works.

---

### Post by amsterdamharu on 2010-12-22
@[colobix]("http://ubuntuforums.org/member.php?u=637517")

```
dylannator@dylannator-Aspire-X3300:~$ lsmod | grep nvidia   
nvidia              10221046  38 
```
> Have you enabled your graphics card yet?
I guess that's a yes.

---

### Post by amsterdamharu on 2010-12-22
As for multiple soundcards or bluetooth usb headsets maybe this can help:
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Step 13 explains what software to install and how to choose the audio device you want to use.

You can install audacity to try to record sound.

---

### Post by bradsha on 2010-12-27
Hey guys sorry i went on a trip and its all going well with it not having as much problems as before i thank you. But my usb headset witch i need for skype and work no longer works is there any way to fix this ?

---

### Post by amsterdamharu on 2010-12-27
Is it a bluetooth headset?
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

If it's not you can still use step 13 to install software and choose what sound card to use.

---

### Post by bradsha on 2010-12-27
No its not blue tooth its plugin usb and how do i do that ?

---

### Post by amsterdamharu on 2010-12-27
Did you install the programs in step 13 of the link I posted before? That explains how to switch from one sound device to another.
[https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset)

Windows probably automatically uses whatever sound comes in but in Ubuntu you have to switch (or so I hear because I have only one soundcard).

---

### Post by bradsha on 2010-12-28
Sorry for kinda bumping this i need my head set for work a plug in mic works but its not clear i need to use my usb if possible

---

### Post by bradsha on 2010-12-28
I tried and step and it failed i don't know how to switch from usb sadly its not working

---

### Post by amsterdamharu on 2010-12-28
```
I tried and step and it failed
```

You could be a bit more informative here. Like what commands did you type and what was the output. The only thing you have to do is copy and paste the lot and copy and paste it back here. Actually less trouble than typing the text "it doesn't work".

What devices can you choose when opening the PulseAudio Device Chooser?

---

