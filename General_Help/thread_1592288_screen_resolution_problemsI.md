---
title: "screen resolution problemsI"
date: 2010-10-10
forum: General Help
---

### Post by 16sinker on 2010-10-10
I've upgraded from Lucid to Meerkat on an "old" Dell Inspiron 4000. Both distributions run great on this computer, but I have to deal with horizontal scroll bar on most web pages including some pages on this forum. This computer ran Windows XP previously, without the horizontal scroll bar, but I used the entire disc when installing Lucid. System>preferences>monitors indicates that my monitor is unknown and I'm only able to get a resolution of 800x600, therefore the horizontal scrolling. Is there a fix which will allow me to use a resolution of 1024x768? I should mention that this computer only has a 14" screen and that being the case, is the Ubuntu Netbook edition a possible fix? It is really annoying to have to deal with horizontal scrolling on most web pages.

---

### Post by rapiertg on 2010-10-10
Hello,

Tried to add modes to "screen" section of xorg.conf?
If not then try to modify your /etc/xorg.conf file to have right resolutions. Some example of this section:
```

Section "Screen"
         Identifier      "Default Screen"
         Device          "Radeon M3"
         Monitor         "Generic Monitor"
         DefaultDepth    24
         SubSection "Display"
                 Depth           24
                 Modes           "1400x1050" "1024x768"
         EndSubSection
 EndSection

```

---

### Post by 16sinker on 2010-10-10
> **rapiertg said:**
> Hello,

Tried to add modes to "screen" section of xorg.conf?
If not then try to modify your /etc/xorg.conf file to have right resolutions. Some example of this section:
```

Section "Screen"
         Identifier      "Default Screen"
         Device          "Radeon M3"
         Monitor         "Generic Monitor"
         DefaultDepth    24
         SubSection "Display"
                 Depth           24
                 Modes           "1400x1050" "1024x768"
         EndSubSection
 EndSection

```
No, I haven't tried that and don't have any idea how to do it. I would appreciate some detailed instruction as to how to accomplish this. Thanks.

---

### Post by 16sinker on 2010-10-10
Do I run the code that was provided in your post, to access this file? If so, I would assume that would be done in a terminal. Yes?

---

### Post by rapiertg on 2010-10-11
Can you paste the output of the command in terminal:

```

cat /etc/X11/xorg.conf

```

---

### Post by 16sinker on 2010-10-11
> **rapiertg said:**
> Can you paste the output of the command in terminal:

```

cat /etc/X11/xorg.conf

```
bofus@ubuntudell:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
bofus@ubuntudell:~
: command not found

---

### Post by dino99 on 2010-10-11
what graphic card in it ?

---

### Post by 16sinker on 2010-10-11
> **dino99 said:**
> what graphic card in it ?
I did copy-paste and don't see a mistake. I don't know what graphic card is in the computer.

---

### Post by dino99 on 2010-10-11
> **16sinker said:**
> I did copy-paste and don't see a mistake. I don't know what graphic card is in the computer.

into a console: sudo lshw > hw.txt

---

### Post by 16sinker on 2010-10-11
> **dino99 said:**
> into a console: sudo lshw > hw.txt
Console same as terminal?

---

### Post by 16sinker on 2010-10-11
> **16sinker said:**
> Console same as terminal?
bofus@ubuntudell:~$ sudo lshw > hw.txt
[sudo] password for bofus: 
bofus@ubuntudell:~$ sudo lshw > hw.txt
PCI (sysfs)

---

### Post by rapiertg on 2010-10-11
Ok so theres no xorg.conf.

No probs, just create one.

```
sudo gedit /etc/X11/xorg.conf
```now you should specify what it should contain. You can find a lot in Google about it. But for now i would suggest to try and paste into it something like this:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection
```Save and reboot. If the Pc wont boot up just turn it on into root command line and give a command:
```
rm /etc/X11/xorg.conf
```and reboot and we will investigate it further.

---

### Post by dino99 on 2010-10-11
console=terminal

open hw.txt with gedit and look at graphic chip or card to know which driver you need

---

### Post by 16sinker on 2010-10-11
> **rapiertg said:**
> Ok so theres no xorg.conf.

No probs, just create one.

```
sudo gedit /etc/X11/xorg.conf
```now you should specify what it should contain. You can find a lot in Google about it. But for now i would suggest to try and paste into it something like this:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection
```Save and reboot. If the Pc wont boot up just turn it on into root command line and give a command:
```
rm /etc/X11/xorg.conf
```and reboot and we will investigate it further.
bofus@ubuntudell:~$ Section "Device"
Section: command not found
bofus@ubuntudell:~$     Identifier    "Configured Video Device"
Identifier: command not found
bofus@ubuntudell:~$     Driver        "ati"
Driver: command not found
bofus@ubuntudell:~$ EndSection
EndSection: command not found
bofus@ubuntudell:~$

---

### Post by rapiertg on 2010-10-11
We missunderstood.

The first commend will open text editor in which you should paste the later code i gave you.

---

### Post by 16sinker on 2010-10-11
bofus@ubuntudell:~$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection
bofus@ubuntudell:~$

---

### Post by rapiertg on 2010-10-11
now try to reboot your pc and check your resolutions

---

### Post by 16sinker on 2010-10-11
> **rapiertg said:**
> now try to reboot your pc and check your resolutions
Rebooted. Checked monitor resolutions under System>Preferences. 800x600 and 640x480 are the only resolutions detected.

---

### Post by rapiertg on 2010-10-11
cal you please attach the file Xorg.0.log that can be found in /var/log/

---

### Post by 16sinker on 2010-10-11
> **rapiertg said:**
> cal you please attach the file Xorg.0.log that can be found in /var/log/

I don't understand your request. Sorry.

---

### Post by 16sinker on 2010-10-11
Perhaps this is what you requested.
ubuntudell
    description: Portable Computer
    product: Inspiron 4000
    vendor: Dell Computer Corporation
    serial: 7C46V01
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-43B0-1034-8036-B7C04F563031
  *-core
       description: Motherboard
       product: Inspiron 4000
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A23 (11/07/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.8.10
          slot: Microprocessor
          size: 900MHz
          capacity: 1GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal varies unified
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=32
          resources: irq:0 memory:f0000000-f3ffffff
        *-pci:0
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fd000000-feffffff memory:f4000000-f7ffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage Mobility M3 AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:f4000000-f7ffffff ioport:ec00(size=256) memory:fdffc000-fdffffff memory:fd000000-fd01ffff
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:11 memory:30000000-30000fff ioport:1000(size=256) ioport:1400(size=256) memory:20000000-23ffffff memory:24000000-27ffffff
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5
             resources: irq:11 memory:30001000-30001fff ioport:1800(size=256) ioport:1c00(size=256) memory:28000000-2bffffff memory:2c000000-2fffffff
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:860(size=16)
           *-disk
                description: ATA Disk
                product: IC25N020ATDA04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: DA3O
                serial: 63063L40838
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000158e8
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: dec98aaf-7beb-45cf-8554-510977ec2020
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-09-25 07:02:54 filesystem=ext4 lastmountpoint=/&#65533;&#65533;X&#65533;cB&#65533;8N&#65533;m&#65533;&#65533;P&#65533;&#65533;&#65533;l!&#65533;8N&#65533;@&#65533;&#65533;:f&#65533;:f&#1984;cB&#1344;h&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-10-10 20:27:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-11 04:45:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 840MiB
                   capacity: 840MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 840MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=32
             resources: irq:11 ioport:cce0(size=32)
        *-bridge:1
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1983S Maestro-3i PCI Audio Accelerator
             vendor: ESS Technology
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Maestro3 latency=32 maxlatency=24 mingnt=2
             resources: irq:5 ioport:c800(size=256) memory:f9ffe000-f9ffffff
        *-pci:1
             description: PCI bridge
             product: Mini-PCI bridge
             vendor: Actiontec Electronics Inc
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm hotswap normal_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fb000000-fcffffff
           *-network
                description: Ethernet interface
                product: 82557/8/9/0/1 Ethernet Pro 100
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:08:04.0
                logical name: eth0
                version: 08
                serial: 00:20:e0:6a:54:e5
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:11 memory:fbfff000-fbffffff ioport:dcc0(size=64) memory:fbe00000-fbefffff memory:fc000000-fc0fffff
           *-communication UNCLAIMED
                description: Communication controller
                product: WinModem 56k
                vendor: Agere Systems
                physical id: 8
                bus info: pci@0000:08:08.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=0 maxlatency=14 mingnt=252
                resources: memory:fbffec00-fbffecff ioport:dcb8(size=8) ioport:d800(size=256)
     *-network
          description: Wireless interface
          product: RT2561/RT61 802.11g PCI
          vendor: RaLink
          physical id: 1
          bus info: pci@0000:0d:00.0
          logical name: wlan0
          version: 00
          serial: 00:0e:2e:84:9e:b7
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-22-generic firmware=N/A ip=10.0.1.6 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
          resources: irq:11 memory:2c000000-2c007fff
  *-battery
       product: LIP4038DLP
       vendor: Sony Corp.
       physical id: 1
       slot: Left Module Bay
       capacity: 26640mWh
       configuration: voltage=14.8V

---

### Post by sendblink23 on 2010-10-11
> **16sinker said:**
> I don't understand your request. Sorry.

Places > Home
File System >
Check: var > log

Find in there: Xorg.0.log

Post the content of that file here

---

### Post by rapiertg on 2010-10-11
Paste this into terminal
```
cp /var/log/Xorg.0.log ~/xorg.txt
```Now you will find a file named xorg.txt in your home directory. Please attach it with your next post.

---

### Post by sendblink23 on 2010-10-11
Video: Rage Mobility M3 AGP 2x

- that answers the question of what video he has

---

### Post by rapiertg on 2010-10-11
> **sendblink23 said:**
> Video: Rage Mobility M3 AGP 2x

- that answers the question of what video he has

Yes, found it in somewhere in google already, and thats why i created basic xorg. Dunno why it doesnt work thru. Lets see some logs then :guitar:

---

### Post by 16sinker on 2010-10-11
No results. Here:bofus@ubuntudell:~$ cp /var/log/Xorg.0.log ~/xorg.txt
bofus@ubuntudell:~$

---

### Post by sendblink23 on 2010-10-11
> **rapiertg said:**
> Yes, found it in somewhere in google already, and thats why i created basic xorg. Dunno why it doesnt work thru. Lets see some logs then :guitar:

isn't he suppose to use like open source drivers or something like that or old stuff ... his system is quite old P3

---

### Post by rapiertg on 2010-10-11
now choose Places from menu and choose Home. There you will find a file called xorg.txt. Is it there? If so then attach it to your post.

---

### Post by 16sinker on 2010-10-11
Contents of Xorg.0.log:  [    31.933] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    31.933] X Protocol Version 11, Revision 0
[    31.933] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    31.933] Current Operating System: Linux ubuntudell 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    31.933] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=dec98aaf-7beb-45cf-8554-510977ec2020 ro vga=771 quiet splash
[    31.933] Build Date: 16 September 2010  05:39:22PM
[    31.934] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    31.934] Current version of pixman: 0.18.4
[    31.934]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    31.934] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.934] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 05:41:58 2010
[    31.935] (==) Using config file: "/etc/X11/xorg.conf"
[    31.935] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.965] (==) No Layout section.  Using the first Screen section.
[    31.965] (**) |-->Screen "Default Screen" (0)
[    31.965] (**) |   |-->Monitor "Configured Monitor"
[    31.966] (**) |   |-->Device "Configured Video Device"
[    31.966] (==) Automatically adding devices
[    31.966] (==) Automatically enabling devices
[    31.966] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.966]     Entry deleted from font path.
[    31.966] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    31.967] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.967] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.967] (II) Loader magic: 0x81f8e00
[    31.967] (II) Module ABI versions:
[    31.967]     X.Org ANSI C Emulation: 0.4
[    31.967]     X.Org Video Driver: 8.0
[    31.967]     X.Org XInput driver : 11.0
[    31.967]     X.Org Server Extension : 4.0
[    31.972] (--) PCI:*(0:1:0:0) 1002:4c46:1028:00b0 rev 2, Mem @ 0xf4000000/67108864, 0xfdffc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
[    31.973] (II) Open ACPI successful (/var/run/acpid.socket)
[    31.973] (II) LoadModule: "extmod"
[    31.997] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    31.998] (II) Module extmod: vendor="X.Org Foundation"
[    31.998]     compiled for 1.9.0, module version = 1.0.0
[    31.998]     Module class: X.Org Server Extension
[    31.998]     ABI class: X.Org Server Extension, version 4.0
[    31.998] (II) Loading extension MIT-SCREEN-SAVER
[    31.998] (II) Loading extension XFree86-VidModeExtension
[    31.998] (II) Loading extension XFree86-DGA
[    31.998] (II) Loading extension DPMS
[    31.998] (II) Loading extension XVideo
[    31.998] (II) Loading extension XVideo-MotionCompensation
[    31.998] (II) Loading extension X-Resource
[    31.998] (II) LoadModule: "dbe"
[    31.999] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    31.999] (II) Module dbe: vendor="X.Org Foundation"
[    31.999]     compiled for 1.9.0, module version = 1.0.0
[    31.999]     Module class: X.Org Server Extension
[    31.999]     ABI class: X.Org Server Extension, version 4.0
[    32.000] (II) Loading extension DOUBLE-BUFFER
[    32.000] (II) LoadModule: "glx"
[    32.001] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.002] (II) Module glx: vendor="X.Org Foundation"
[    32.002]     compiled for 1.9.0, module version = 1.0.0
[    32.002]     ABI class: X.Org Server Extension, version 4.0
[    32.002] (==) AIGLX enabled
[    32.002] (II) Loading extension GLX
[    32.002] (II) LoadModule: "record"
[    32.002] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.003] (II) Module record: vendor="X.Org Foundation"
[    32.003]     compiled for 1.9.0, module version = 1.13.0
[    32.003]     Module class: X.Org Server Extension
[    32.003]     ABI class: X.Org Server Extension, version 4.0
[    32.003] (II) Loading extension RECORD
[    32.003] (II) LoadModule: "dri"
[    32.008] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.009] (II) Module dri: vendor="X.Org Foundation"
[    32.009]     compiled for 1.9.0, module version = 1.0.0
[    32.009]     ABI class: X.Org Server Extension, version 4.0
[    32.009] (II) Loading extension XFree86-DRI
[    32.009] (II) LoadModule: "dri2"
[    32.010] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.010] (II) Module dri2: vendor="X.Org Foundation"
[    32.010]     compiled for 1.9.0, module version = 1.2.0
[    32.010]     ABI class: X.Org Server Extension, version 4.0
[    32.010] (II) Loading extension DRI2
[    32.010] (II) LoadModule: "ati"
[    32.014] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    32.015] (II) Module ati: vendor="X.Org Foundation"
[    32.015]     compiled for 1.9.0, module version = 6.13.1
[    32.015]     Module class: X.Org Video Driver
[    32.015]     ABI class: X.Org Video Driver, version 8.0
[    32.015] (II) LoadModule: "r128"
[    32.016] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    32.017] (II) Module r128: vendor="X.Org Foundation"
[    32.017]     compiled for 1.8.99.905, module version = 6.8.1
[    32.017]     Module class: X.Org Video Driver
[    32.017]     ABI class: X.Org Video Driver, version 8.0
[    32.017] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    32.026] (++) using VT number 7

[    32.027] (II) R128(0): PCI bus 1 card 0 func 0
[    32.027] (**) R128(0): Depth 24, (--) framebuffer bpp 32
[    32.027] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    32.027] (==) R128(0): Default visual is TrueColor
[    32.027] (II) Loading sub module "vgahw"
[    32.027] (II) LoadModule: "vgahw"
[    32.033] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    32.034] (II) Module vgahw: vendor="X.Org Foundation"
[    32.034]     compiled for 1.9.0, module version = 0.1.0
[    32.034]     ABI class: X.Org Video Driver, version 8.0
[    32.034] (II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    32.034] (==) R128(0): RGB weight 888
[    32.034] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    32.034] (II) Loading sub module "int10"
[    32.034] (II) LoadModule: "int10"
[    32.035] (II) Loading /usr/lib/xorg/modules/libint10.so
[    32.035] (II) Module int10: vendor="X.Org Foundation"
[    32.035]     compiled for 1.9.0, module version = 1.0.0
[    32.035]     ABI class: X.Org Video Driver, version 8.0
[    32.035] (II) R128(0): initializing int10
[    32.041] (II) R128(0): Primary V_BIOS segment is: 0xc000
[    32.041] (--) R128(0): Chipset: "ATI Rage 128 Mobility M3 LF (AGP)" (ChipID = 0x4c46)
[    32.041] (--) R128(0): Linear framebuffer at 0xf4000000
[    32.048] (--) R128(0): MMIO registers at 0xfdffc000
[    32.049] (--) R128(0): VideoRAM: 8192 kByte (128-bit SDR SGRAM 1:1)
[    32.049] (**) R128(0): Using flat panel for display
[    32.050] (II) R128(0): Primary Display == Type 2
[    32.050] (II) R128(0): Panel size: 1024x768
[    32.050] (II) R128(0): Panel ID: Samsung LT141X8-L02     
[    32.051] (II) R128(0): Panel Type: Color, Single, TFT
[    32.051] (II) R128(0): Panel Interface: LVDS
[    32.051] (II) R128(0): PLL parameters: rf=2700 rd=12 min=12000 max=27000; xclk=10500
[    32.051] (II) Loading sub module "ddc"
[    32.051] (II) LoadModule: "ddc"
[    32.051] (II) Module "ddc" already built-in
[    32.051] (II) Loading sub module "vbe"
[    32.051] (II) LoadModule: "vbe"
[    32.068] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    32.068] (II) Module vbe: vendor="X.Org Foundation"
[    32.069]     compiled for 1.9.0, module version = 1.1.0
[    32.069]     ABI class: X.Org Video Driver, version 8.0
[    32.070] (II) R128(0): VESA BIOS detected
[    32.070] (II) R128(0): VESA VBE Version 2.0
[    32.070] (II) R128(0): VESA VBE Total Mem: 8192 kB
[    32.070] (II) R128(0): VESA VBE OEM: ATI MOBILE M3
[    32.070] (II) R128(0): VESA VBE OEM Software Rev: 1.0
[    32.070] (II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    32.070] (II) R128(0): VESA VBE OEM Product: M3  
[    32.070] (II) R128(0): VESA VBE OEM Product Rev: 01.00
[    32.070] (II) Loading sub module "ddc"
[    32.070] (II) LoadModule: "ddc"
[    32.070] (II) Module "ddc" already built-in
[    32.073] (II) R128(0): VESA VBE DDC supported
[    32.073] (II) R128(0): VESA VBE DDC Level none
[    32.073] (II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
[    32.094] (II) R128(0): VESA VBE DDC read failed
[    32.095] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.095] (II) R128(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
[    32.095] (II) R128(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[    32.095] (II) R128(0): Clock range:  12.00 to 270.00 MHz
[    32.095] (II) R128(0): Not using default mode "640x350" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x400" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "720x400" (no mode of this name)
[    32.095] (II) R128(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "1024x768i" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.107] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.107] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.107] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x960" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x960" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x1024" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x1024" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x1024" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    32.109] (II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "832x624" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1360x768" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1360x768" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1440x900" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1600x1024" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1920x1080" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using mode "1280x1024" (no mode of this name)
[    32.117] (II) R128(0): Not using mode "1024x768" (no mode of this name)
[    32.118] (II) R128(0): Modifying mode according to VBIOS: 800x600 [pclk 40.0 MHz] for FP to: 800x600 [pclk 65.0 MHz]
[    32.118] (II) R128(0): Modifying mode according to VBIOS: 800x600 [pclk 36.0 MHz] for FP to: 800x600 [pclk 65.0 MHz]
[    32.118] (II) R128(0): Modifying mode according to VBIOS: 640x480 [pclk 25.2 MHz] for FP to: 640x480 [pclk 65.0 MHz]
[    32.118] (--) R128(0): Virtual size is 800x600 (pitch 800)
[    32.118] (**) R128(0):  Default mode "800x600": 65.0 MHz (scaled from 40.0 MHz), 37.9 kHz, 60.3 Hz
[    32.124] (II) R128(0): Modeline "800x600"x60.3   65.00  800 824 841 1120  600 602 608 638 +hsync +vsync (37.9 kHz)
[    32.124] (**) R128(0):  Default mode "800x600": 65.0 MHz (scaled from 36.0 MHz), 35.2 kHz, 56.2 Hz
[    32.124] (II) R128(0): Modeline "800x600"x56.2   65.00  800 824 841 1120  600 602 608 638 +hsync +vsync (35.2 kHz)
[    32.124] (**) R128(0):  Default mode "640x480": 65.0 MHz (scaled from 25.2 MHz), 31.5 kHz, 59.9 Hz
[    32.124] (II) R128(0): Modeline "640x480"x59.9   65.00  640 664 681 960  480 482 488 518 -hsync -vsync (31.5 kHz)
[    32.124] (==) R128(0): DPI set to (96, 96)
[    32.124] (II) Loading sub module "fb"
[    32.124] (II) LoadModule: "fb"
[    32.125] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.125] (II) Module fb: vendor="X.Org Foundation"
[    32.125]     compiled for 1.9.0, module version = 1.0.0
[    32.125]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.125] (II) Loading sub module "ramdac"
[    32.125] (II) LoadModule: "ramdac"
[    32.125] (II) Module "ramdac" already built-in
[    32.125] (II) Loading sub module "xaa"
[    32.126] (II) LoadModule: "xaa"
[    32.127] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    32.127] (II) Module xaa: vendor="X.Org Foundation"
[    32.127]     compiled for 1.9.0, module version = 1.2.1
[    32.127]     ABI class: X.Org Video Driver, version 8.0
[    32.130] (II) Loading sub module "shadowfb"
[    32.130] (II) LoadModule: "shadowfb"
[    32.130] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    32.131] (II) Module shadowfb: vendor="X.Org Foundation"
[    32.131]     compiled for 1.9.0, module version = 1.0.0
[    32.131]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.131] (II) R128(0): Page flipping disabled
[    32.131] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
[    32.131] (--) Depth 24 pixmap format is 32 bpp
[    32.142] drmOpenDevice: node name is /dev/dri/card0
[    32.148] drmOpenDevice: node name is /dev/dri/card0
[    32.386] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    32.386] drmOpenDevice: node name is /dev/dri/card0
[    32.386] drmOpenDevice: open result is 11, (OK)
[    32.387] drmOpenByBusid: drmOpenMinor returns 11
[    32.387] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    32.387] (II) [drm] loaded kernel module for "r128" driver.
[    32.387] (II) [drm] DRM interface version 1.3
[    32.387] (II) [drm] DRM open master succeeded.
[    32.387] (II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
[    32.387] (II) R128(0): [drm] framebuffer handle = 0xf4000000
[    32.387] (II) R128(0): [drm] added 1 reserved context for kernel
[    32.387] (II) R128(0): X context handle = 0x1
[    32.387] (II) R128(0): [drm] installed DRM signal handler
[    32.388] (II) R128(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x1002/0x4c46]
[    32.481] (II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
[    32.482] (II) R128(0): [agp] ring handle = 0xf0000000
[    32.483] (II) R128(0): [agp] Ring mapped at 0xb7564000
[    32.483] (II) R128(0): [agp] ring read ptr handle = 0xf0101000
[    32.483] (II) R128(0): [agp] Ring read ptr mapped at 0xb77c6000
[    32.483] (II) R128(0): [agp] vertex/indirect buffers handle = 0xf0102000
[    32.483] (II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb7364000
[    32.483] (II) R128(0): [agp] AGP texture map handle = 0xf0302000
[    32.489] (II) R128(0): [agp] AGP Texture map mapped at 0xb6e84000
[    32.489] (II) R128(0): [drm] register handle = 0xfdffc000
[    32.489] (II) R128(0): [dri] Visual configs initialized
[    32.489] (II) R128(0): CCE in BM mode
[    32.489] (II) R128(0): Using 8 MB AGP aperture
[    32.489] (II) R128(0): Using 1 MB for the ring buffer
[    32.489] (II) R128(0): Using 2 MB for vertex/indirect buffers
[    32.489] (II) R128(0): Using 5 MB for AGP textures
[    32.490] (II) R128(0): Memory manager initialized to (0,0) (800,2416)
[    32.490] (II) R128(0): Reserved area from (0,600) to (800,602)
[    32.490] (II) R128(0): Largest offscreen area available: 800 x 1814
[    32.490] (II) R128(0): Reserved back buffer from (0,602) to (800,1202)
[    32.490] (II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
[    32.490] (II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
[    32.490] (II) R128(0): Reserved 640 kb for textures at offset 0x75f800
[    32.490] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    32.490]     Screen to screen bit blits
[    32.490]     Solid filled rectangles
[    32.490]     8x8 mono pattern filled rectangles
[    32.490]     Indirect CPU to Screen color expansion
[    32.490]     Solid Lines
[    32.490]     Dashed Lines
[    32.491]     Setting up tile and stipple cache:
[    32.491]         24 128x128 slots
[    32.491] (II) R128(0): Acceleration enabled
[    32.491] (==) R128(0): Backing store disabled
[    32.491] (==) R128(0): Silken mouse enabled
[    32.491] (II) R128(0): Using hardware cursor (scanline 7212)
[    32.491] (II) R128(0): Largest offscreen area available: 800 x 610
[    32.492] (==) R128(0): DPMS enabled
[    32.496] (II) R128(0): [DRI] installation complete
[    32.518] (II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
[    32.519] (II) R128(0): [drm] Mapped 128 vertex/indirect buffers
[    32.519] (II) R128(0): [drm] dma control initialized, using IRQ 11
[    32.519] (II) R128(0): Direct rendering enabled
[    32.519] (==) RandR enabled
[    32.519] (II) Initializing built-in extension Generic Event Extension
[    32.522] (II) Initializing built-in extension SHAPE
[    32.522] (II) Initializing built-in extension MIT-SHM
[    32.522] (II) Initializing built-in extension XInputExtension
[    32.522] (II) Initializing built-in extension XTEST
[    32.522] (II) Initializing built-in extension BIG-REQUESTS
[    32.522] (II) Initializing built-in extension SYNC
[    32.522] (II) Initializing built-in extension XKEYBOARD
[    32.522] (II) Initializing built-in extension XC-MISC
[    32.522] (II) Initializing built-in extension SECURITY
[    32.522] (II) Initializing built-in extension XINERAMA
[    32.522] (II) Initializing built-in extension XFIXES
[    32.522] (II) Initializing built-in extension RENDER
[    32.522] (II) Initializing built-in extension RANDR
[    32.522] (II) Initializing built-in extension COMPOSITE
[    32.522] (II) Initializing built-in extension DAMAGE
[    32.523] (II) Initializing built-in extension GESTURE
[    32.578] (II) AIGLX: Screen 0 is not DRI2 capable
[    32.578] drmOpenDevice: node name is /dev/dri/card0
[    32.578] drmOpenDevice: open result is 12, (OK)
[    32.578] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    32.578] drmOpenDevice: node name is /dev/dri/card0
[    32.578] drmOpenDevice: open result is 12, (OK)
[    32.578] drmOpenByBusid: drmOpenMinor returns 12
[    32.578] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    32.592] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.592] (II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
[    32.592] (II) GLX: Initialized DRI GL provider for screen 0
[    32.763] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.823] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    32.825] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    32.825] (II) LoadModule: "evdev"
[    32.826] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.827] (II) Module evdev: vendor="X.Org Foundation"
[    32.827]     compiled for 1.9.0, module version = 2.3.2
[    32.827]     Module class: X.Org XInput Driver
[    32.827]     ABI class: X.Org XInput driver, version 11.0
[    32.827] (**) Video Bus: always reports core events
[    32.827] (**) Video Bus: Device: "/dev/input/event4"
[    32.827] (II) Video Bus: Found keys
[    32.827] (II) Video Bus: Configuring as keyboard
[    32.827] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    32.827] (**) Option "xkb_rules" "evdev"
[    32.828] (**) Option "xkb_model" "pc105"
[    32.828] (**) Option "xkb_layout" "us"
[    32.830] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    32.830] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.830] (**) Power Button: always reports core events
[    32.831] (**) Power Button: Device: "/dev/input/event1"
[    32.831] (II) Power Button: Found keys
[    32.831] (II) Power Button: Configuring as keyboard
[    32.831] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    32.831] (**) Option "xkb_rules" "evdev"
[    32.832] (**) Option "xkb_model" "pc105"
[    32.832] (**) Option "xkb_layout" "us"
[    32.834] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    32.834] (II) No input driver/identifier specified (ignoring)
[    32.835] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    32.835] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    32.835] (**) Sleep Button: always reports core events
[    32.835] (**) Sleep Button: Device: "/dev/input/event2"
[    32.835] (II) Sleep Button: Found keys
[    32.835] (II) Sleep Button: Configuring as keyboard
[    32.835] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    32.835] (**) Option "xkb_rules" "evdev"
[    32.835] (**) Option "xkb_model" "pc105"
[    32.835] (**) Option "xkb_layout" "us"
[    32.846] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    32.846] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    32.847] (**) AT Translated Set 2 keyboard: always reports core events
[    32.847] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    32.847] (II) AT Translated Set 2 keyboard: Found keys
[    32.847] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    32.847] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    32.847] (**) Option "xkb_rules" "evdev"
[    32.847] (**) Option "xkb_model" "pc105"
[    32.847] (**) Option "xkb_layout" "us"
[    32.849] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    32.849] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    32.849] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.849] (II) LoadModule: "synaptics"
[    32.850] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.850] (II) Module synaptics: vendor="X.Org Foundation"
[    32.850]     compiled for 1.9.0, module version = 1.2.2
[    32.850]     Module class: X.Org XInput Driver
[    32.850]     ABI class: X.Org XInput driver, version 11.0
[    32.850] (II) Synaptics touchpad driver version 1.2.2
[    32.850] (**) Option "Device" "/dev/input/event5"
[    32.851] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    32.851] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    32.851] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    32.851] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    32.851] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    32.851] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.851] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.851] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    32.851] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    32.851] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    32.852] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    32.852] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    32.853] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.854] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    32.854] (II) No input driver/identifier specified (ignoring)
[    35.854] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    35.854] (II) No input driver/identifier specified (ignoring)
[    35.881] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    35.881] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    35.881] (**) TPPS/2 IBM TrackPoint: always reports core events
[    35.882] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[    35.882] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    35.882] (II) TPPS/2 IBM TrackPoint: Found relative axes
[    35.882] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    35.882] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    35.882] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    35.882] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.882] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    35.882] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.

---

### Post by 16sinker on 2010-10-11
xorg.txt:  [    31.933] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    31.933] X Protocol Version 11, Revision 0
[    31.933] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    31.933] Current Operating System: Linux ubuntudell 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    31.933] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=dec98aaf-7beb-45cf-8554-510977ec2020 ro vga=771 quiet splash
[    31.933] Build Date: 16 September 2010  05:39:22PM
[    31.934] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    31.934] Current version of pixman: 0.18.4
[    31.934]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    31.934] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.934] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 11 05:41:58 2010
[    31.935] (==) Using config file: "/etc/X11/xorg.conf"
[    31.935] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.965] (==) No Layout section.  Using the first Screen section.
[    31.965] (**) |-->Screen "Default Screen" (0)
[    31.965] (**) |   |-->Monitor "Configured Monitor"
[    31.966] (**) |   |-->Device "Configured Video Device"
[    31.966] (==) Automatically adding devices
[    31.966] (==) Automatically enabling devices
[    31.966] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.966]     Entry deleted from font path.
[    31.966] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    31.967] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.967] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.967] (II) Loader magic: 0x81f8e00
[    31.967] (II) Module ABI versions:
[    31.967]     X.Org ANSI C Emulation: 0.4
[    31.967]     X.Org Video Driver: 8.0
[    31.967]     X.Org XInput driver : 11.0
[    31.967]     X.Org Server Extension : 4.0
[    31.972] (--) PCI:*(0:1:0:0) 1002:4c46:1028:00b0 rev 2, Mem @ 0xf4000000/67108864, 0xfdffc000/16384, I/O @ 0x0000ec00/256, BIOS @ 0x????????/131072
[    31.973] (II) Open ACPI successful (/var/run/acpid.socket)
[    31.973] (II) LoadModule: "extmod"
[    31.997] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    31.998] (II) Module extmod: vendor="X.Org Foundation"
[    31.998]     compiled for 1.9.0, module version = 1.0.0
[    31.998]     Module class: X.Org Server Extension
[    31.998]     ABI class: X.Org Server Extension, version 4.0
[    31.998] (II) Loading extension MIT-SCREEN-SAVER
[    31.998] (II) Loading extension XFree86-VidModeExtension
[    31.998] (II) Loading extension XFree86-DGA
[    31.998] (II) Loading extension DPMS
[    31.998] (II) Loading extension XVideo
[    31.998] (II) Loading extension XVideo-MotionCompensation
[    31.998] (II) Loading extension X-Resource
[    31.998] (II) LoadModule: "dbe"
[    31.999] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    31.999] (II) Module dbe: vendor="X.Org Foundation"
[    31.999]     compiled for 1.9.0, module version = 1.0.0
[    31.999]     Module class: X.Org Server Extension
[    31.999]     ABI class: X.Org Server Extension, version 4.0
[    32.000] (II) Loading extension DOUBLE-BUFFER
[    32.000] (II) LoadModule: "glx"
[    32.001] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.002] (II) Module glx: vendor="X.Org Foundation"
[    32.002]     compiled for 1.9.0, module version = 1.0.0
[    32.002]     ABI class: X.Org Server Extension, version 4.0
[    32.002] (==) AIGLX enabled
[    32.002] (II) Loading extension GLX
[    32.002] (II) LoadModule: "record"
[    32.002] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.003] (II) Module record: vendor="X.Org Foundation"
[    32.003]     compiled for 1.9.0, module version = 1.13.0
[    32.003]     Module class: X.Org Server Extension
[    32.003]     ABI class: X.Org Server Extension, version 4.0
[    32.003] (II) Loading extension RECORD
[    32.003] (II) LoadModule: "dri"
[    32.008] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.009] (II) Module dri: vendor="X.Org Foundation"
[    32.009]     compiled for 1.9.0, module version = 1.0.0
[    32.009]     ABI class: X.Org Server Extension, version 4.0
[    32.009] (II) Loading extension XFree86-DRI
[    32.009] (II) LoadModule: "dri2"
[    32.010] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.010] (II) Module dri2: vendor="X.Org Foundation"
[    32.010]     compiled for 1.9.0, module version = 1.2.0
[    32.010]     ABI class: X.Org Server Extension, version 4.0
[    32.010] (II) Loading extension DRI2
[    32.010] (II) LoadModule: "ati"
[    32.014] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    32.015] (II) Module ati: vendor="X.Org Foundation"
[    32.015]     compiled for 1.9.0, module version = 6.13.1
[    32.015]     Module class: X.Org Video Driver
[    32.015]     ABI class: X.Org Video Driver, version 8.0
[    32.015] (II) LoadModule: "r128"
[    32.016] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    32.017] (II) Module r128: vendor="X.Org Foundation"
[    32.017]     compiled for 1.8.99.905, module version = 6.8.1
[    32.017]     Module class: X.Org Video Driver
[    32.017]     ABI class: X.Org Video Driver, version 8.0
[    32.017] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    32.026] (++) using VT number 7

[    32.027] (II) R128(0): PCI bus 1 card 0 func 0
[    32.027] (**) R128(0): Depth 24, (--) framebuffer bpp 32
[    32.027] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    32.027] (==) R128(0): Default visual is TrueColor
[    32.027] (II) Loading sub module "vgahw"
[    32.027] (II) LoadModule: "vgahw"
[    32.033] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    32.034] (II) Module vgahw: vendor="X.Org Foundation"
[    32.034]     compiled for 1.9.0, module version = 0.1.0
[    32.034]     ABI class: X.Org Video Driver, version 8.0
[    32.034] (II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    32.034] (==) R128(0): RGB weight 888
[    32.034] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    32.034] (II) Loading sub module "int10"
[    32.034] (II) LoadModule: "int10"
[    32.035] (II) Loading /usr/lib/xorg/modules/libint10.so
[    32.035] (II) Module int10: vendor="X.Org Foundation"
[    32.035]     compiled for 1.9.0, module version = 1.0.0
[    32.035]     ABI class: X.Org Video Driver, version 8.0
[    32.035] (II) R128(0): initializing int10
[    32.041] (II) R128(0): Primary V_BIOS segment is: 0xc000
[    32.041] (--) R128(0): Chipset: "ATI Rage 128 Mobility M3 LF (AGP)" (ChipID = 0x4c46)
[    32.041] (--) R128(0): Linear framebuffer at 0xf4000000
[    32.048] (--) R128(0): MMIO registers at 0xfdffc000
[    32.049] (--) R128(0): VideoRAM: 8192 kByte (128-bit SDR SGRAM 1:1)
[    32.049] (**) R128(0): Using flat panel for display
[    32.050] (II) R128(0): Primary Display == Type 2
[    32.050] (II) R128(0): Panel size: 1024x768
[    32.050] (II) R128(0): Panel ID: Samsung LT141X8-L02     
[    32.051] (II) R128(0): Panel Type: Color, Single, TFT
[    32.051] (II) R128(0): Panel Interface: LVDS
[    32.051] (II) R128(0): PLL parameters: rf=2700 rd=12 min=12000 max=27000; xclk=10500
[    32.051] (II) Loading sub module "ddc"
[    32.051] (II) LoadModule: "ddc"
[    32.051] (II) Module "ddc" already built-in
[    32.051] (II) Loading sub module "vbe"
[    32.051] (II) LoadModule: "vbe"
[    32.068] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    32.068] (II) Module vbe: vendor="X.Org Foundation"
[    32.069]     compiled for 1.9.0, module version = 1.1.0
[    32.069]     ABI class: X.Org Video Driver, version 8.0
[    32.070] (II) R128(0): VESA BIOS detected
[    32.070] (II) R128(0): VESA VBE Version 2.0
[    32.070] (II) R128(0): VESA VBE Total Mem: 8192 kB
[    32.070] (II) R128(0): VESA VBE OEM: ATI MOBILE M3
[    32.070] (II) R128(0): VESA VBE OEM Software Rev: 1.0
[    32.070] (II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    32.070] (II) R128(0): VESA VBE OEM Product: M3  
[    32.070] (II) R128(0): VESA VBE OEM Product Rev: 01.00
[    32.070] (II) Loading sub module "ddc"
[    32.070] (II) LoadModule: "ddc"
[    32.070] (II) Module "ddc" already built-in
[    32.073] (II) R128(0): VESA VBE DDC supported
[    32.073] (II) R128(0): VESA VBE DDC Level none
[    32.073] (II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
[    32.094] (II) R128(0): VESA VBE DDC read failed
[    32.095] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.095] (II) R128(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
[    32.095] (II) R128(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
[    32.095] (II) R128(0): Clock range:  12.00 to 270.00 MHz
[    32.095] (II) R128(0): Not using default mode "640x350" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x400" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "720x400" (no mode of this name)
[    32.095] (II) R128(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x480" (vrefresh out of range)
[    32.095] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.095] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "1024x768i" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.106] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.106] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.107] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.107] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    32.107] (II) R128(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x960" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x960" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x1024" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x1024" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1280x1024" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[    32.107] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.107] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1600x1200" (no mode of this name)
[    32.108] (II) R128(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    32.108] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    32.108] (II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    32.109] (II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "832x624" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1152x864" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[    32.109] (II) R128(0): Not using default mode "1360x768" (no mode of this name)
[    32.109] (II) R128(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1360x768" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1400x1050" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[    32.110] (II) R128(0): Not using default mode "1440x900" (no mode of this name)
[    32.110] (II) R128(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1600x1024" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1680x1050" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1920x1080" (no mode of this name)
[    32.116] (II) R128(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[    32.116] (II) R128(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    32.117] (II) R128(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    32.117] (II) R128(0): Not using mode "1280x1024" (no mode of this name)
[    32.117] (II) R128(0): Not using mode "1024x768" (no mode of this name)
[    32.118] (II) R128(0): Modifying mode according to VBIOS: 800x600 [pclk 40.0 MHz] for FP to: 800x600 [pclk 65.0 MHz]
[    32.118] (II) R128(0): Modifying mode according to VBIOS: 800x600 [pclk 36.0 MHz] for FP to: 800x600 [pclk 65.0 MHz]
[    32.118] (II) R128(0): Modifying mode according to VBIOS: 640x480 [pclk 25.2 MHz] for FP to: 640x480 [pclk 65.0 MHz]
[    32.118] (--) R128(0): Virtual size is 800x600 (pitch 800)
[    32.118] (**) R128(0):  Default mode "800x600": 65.0 MHz (scaled from 40.0 MHz), 37.9 kHz, 60.3 Hz
[    32.124] (II) R128(0): Modeline "800x600"x60.3   65.00  800 824 841 1120  600 602 608 638 +hsync +vsync (37.9 kHz)
[    32.124] (**) R128(0):  Default mode "800x600": 65.0 MHz (scaled from 36.0 MHz), 35.2 kHz, 56.2 Hz
[    32.124] (II) R128(0): Modeline "800x600"x56.2   65.00  800 824 841 1120  600 602 608 638 +hsync +vsync (35.2 kHz)
[    32.124] (**) R128(0):  Default mode "640x480": 65.0 MHz (scaled from 25.2 MHz), 31.5 kHz, 59.9 Hz
[    32.124] (II) R128(0): Modeline "640x480"x59.9   65.00  640 664 681 960  480 482 488 518 -hsync -vsync (31.5 kHz)
[    32.124] (==) R128(0): DPI set to (96, 96)
[    32.124] (II) Loading sub module "fb"
[    32.124] (II) LoadModule: "fb"
[    32.125] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.125] (II) Module fb: vendor="X.Org Foundation"
[    32.125]     compiled for 1.9.0, module version = 1.0.0
[    32.125]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.125] (II) Loading sub module "ramdac"
[    32.125] (II) LoadModule: "ramdac"
[    32.125] (II) Module "ramdac" already built-in
[    32.125] (II) Loading sub module "xaa"
[    32.126] (II) LoadModule: "xaa"
[    32.127] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    32.127] (II) Module xaa: vendor="X.Org Foundation"
[    32.127]     compiled for 1.9.0, module version = 1.2.1
[    32.127]     ABI class: X.Org Video Driver, version 8.0
[    32.130] (II) Loading sub module "shadowfb"
[    32.130] (II) LoadModule: "shadowfb"
[    32.130] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    32.131] (II) Module shadowfb: vendor="X.Org Foundation"
[    32.131]     compiled for 1.9.0, module version = 1.0.0
[    32.131]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.131] (II) R128(0): Page flipping disabled
[    32.131] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
[    32.131] (--) Depth 24 pixmap format is 32 bpp
[    32.142] drmOpenDevice: node name is /dev/dri/card0
[    32.148] drmOpenDevice: node name is /dev/dri/card0
[    32.386] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    32.386] drmOpenDevice: node name is /dev/dri/card0
[    32.386] drmOpenDevice: open result is 11, (OK)
[    32.387] drmOpenByBusid: drmOpenMinor returns 11
[    32.387] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    32.387] (II) [drm] loaded kernel module for "r128" driver.
[    32.387] (II) [drm] DRM interface version 1.3
[    32.387] (II) [drm] DRM open master succeeded.
[    32.387] (II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
[    32.387] (II) R128(0): [drm] framebuffer handle = 0xf4000000
[    32.387] (II) R128(0): [drm] added 1 reserved context for kernel
[    32.387] (II) R128(0): X context handle = 0x1
[    32.387] (II) R128(0): [drm] installed DRM signal handler
[    32.388] (II) R128(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x7190; Card 0x1002/0x4c46]
[    32.481] (II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
[    32.482] (II) R128(0): [agp] ring handle = 0xf0000000
[    32.483] (II) R128(0): [agp] Ring mapped at 0xb7564000
[    32.483] (II) R128(0): [agp] ring read ptr handle = 0xf0101000
[    32.483] (II) R128(0): [agp] Ring read ptr mapped at 0xb77c6000
[    32.483] (II) R128(0): [agp] vertex/indirect buffers handle = 0xf0102000
[    32.483] (II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb7364000
[    32.483] (II) R128(0): [agp] AGP texture map handle = 0xf0302000
[    32.489] (II) R128(0): [agp] AGP Texture map mapped at 0xb6e84000
[    32.489] (II) R128(0): [drm] register handle = 0xfdffc000
[    32.489] (II) R128(0): [dri] Visual configs initialized
[    32.489] (II) R128(0): CCE in BM mode
[    32.489] (II) R128(0): Using 8 MB AGP aperture
[    32.489] (II) R128(0): Using 1 MB for the ring buffer
[    32.489] (II) R128(0): Using 2 MB for vertex/indirect buffers
[    32.489] (II) R128(0): Using 5 MB for AGP textures
[    32.490] (II) R128(0): Memory manager initialized to (0,0) (800,2416)
[    32.490] (II) R128(0): Reserved area from (0,600) to (800,602)
[    32.490] (II) R128(0): Largest offscreen area available: 800 x 1814
[    32.490] (II) R128(0): Reserved back buffer from (0,602) to (800,1202)
[    32.490] (II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
[    32.490] (II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
[    32.490] (II) R128(0): Reserved 640 kb for textures at offset 0x75f800
[    32.490] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    32.490]     Screen to screen bit blits
[    32.490]     Solid filled rectangles
[    32.490]     8x8 mono pattern filled rectangles
[    32.490]     Indirect CPU to Screen color expansion
[    32.490]     Solid Lines
[    32.490]     Dashed Lines
[    32.491]     Setting up tile and stipple cache:
[    32.491]         24 128x128 slots
[    32.491] (II) R128(0): Acceleration enabled
[    32.491] (==) R128(0): Backing store disabled
[    32.491] (==) R128(0): Silken mouse enabled
[    32.491] (II) R128(0): Using hardware cursor (scanline 7212)
[    32.491] (II) R128(0): Largest offscreen area available: 800 x 610
[    32.492] (==) R128(0): DPMS enabled
[    32.496] (II) R128(0): [DRI] installation complete
[    32.518] (II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
[    32.519] (II) R128(0): [drm] Mapped 128 vertex/indirect buffers
[    32.519] (II) R128(0): [drm] dma control initialized, using IRQ 11
[    32.519] (II) R128(0): Direct rendering enabled
[    32.519] (==) RandR enabled
[    32.519] (II) Initializing built-in extension Generic Event Extension
[    32.522] (II) Initializing built-in extension SHAPE
[    32.522] (II) Initializing built-in extension MIT-SHM
[    32.522] (II) Initializing built-in extension XInputExtension
[    32.522] (II) Initializing built-in extension XTEST
[    32.522] (II) Initializing built-in extension BIG-REQUESTS
[    32.522] (II) Initializing built-in extension SYNC
[    32.522] (II) Initializing built-in extension XKEYBOARD
[    32.522] (II) Initializing built-in extension XC-MISC
[    32.522] (II) Initializing built-in extension SECURITY
[    32.522] (II) Initializing built-in extension XINERAMA
[    32.522] (II) Initializing built-in extension XFIXES
[    32.522] (II) Initializing built-in extension RENDER
[    32.522] (II) Initializing built-in extension RANDR
[    32.522] (II) Initializing built-in extension COMPOSITE
[    32.522] (II) Initializing built-in extension DAMAGE
[    32.523] (II) Initializing built-in extension GESTURE
[    32.578] (II) AIGLX: Screen 0 is not DRI2 capable
[    32.578] drmOpenDevice: node name is /dev/dri/card0
[    32.578] drmOpenDevice: open result is 12, (OK)
[    32.578] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    32.578] drmOpenDevice: node name is /dev/dri/card0
[    32.578] drmOpenDevice: open result is 12, (OK)
[    32.578] drmOpenByBusid: drmOpenMinor returns 12
[    32.578] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    32.592] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.592] (II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
[    32.592] (II) GLX: Initialized DRI GL provider for screen 0
[    32.763] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.823] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    32.825] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    32.825] (II) LoadModule: "evdev"
[    32.826] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.827] (II) Module evdev: vendor="X.Org Foundation"
[    32.827]     compiled for 1.9.0, module version = 2.3.2
[    32.827]     Module class: X.Org XInput Driver
[    32.827]     ABI class: X.Org XInput driver, version 11.0
[    32.827] (**) Video Bus: always reports core events
[    32.827] (**) Video Bus: Device: "/dev/input/event4"
[    32.827] (II) Video Bus: Found keys
[    32.827] (II) Video Bus: Configuring as keyboard
[    32.827] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    32.827] (**) Option "xkb_rules" "evdev"
[    32.828] (**) Option "xkb_model" "pc105"
[    32.828] (**) Option "xkb_layout" "us"
[    32.830] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    32.830] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.830] (**) Power Button: always reports core events
[    32.831] (**) Power Button: Device: "/dev/input/event1"
[    32.831] (II) Power Button: Found keys
[    32.831] (II) Power Button: Configuring as keyboard
[    32.831] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    32.831] (**) Option "xkb_rules" "evdev"
[    32.832] (**) Option "xkb_model" "pc105"
[    32.832] (**) Option "xkb_layout" "us"
[    32.834] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    32.834] (II) No input driver/identifier specified (ignoring)
[    32.835] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    32.835] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    32.835] (**) Sleep Button: always reports core events
[    32.835] (**) Sleep Button: Device: "/dev/input/event2"
[    32.835] (II) Sleep Button: Found keys
[    32.835] (II) Sleep Button: Configuring as keyboard
[    32.835] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    32.835] (**) Option "xkb_rules" "evdev"
[    32.835] (**) Option "xkb_model" "pc105"
[    32.835] (**) Option "xkb_layout" "us"
[    32.846] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    32.846] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    32.847] (**) AT Translated Set 2 keyboard: always reports core events
[    32.847] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    32.847] (II) AT Translated Set 2 keyboard: Found keys
[    32.847] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    32.847] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    32.847] (**) Option "xkb_rules" "evdev"
[    32.847] (**) Option "xkb_model" "pc105"
[    32.847] (**) Option "xkb_layout" "us"
[    32.849] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    32.849] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    32.849] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    32.849] (II) LoadModule: "synaptics"
[    32.850] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    32.850] (II) Module synaptics: vendor="X.Org Foundation"
[    32.850]     compiled for 1.9.0, module version = 1.2.2
[    32.850]     Module class: X.Org XInput Driver
[    32.850]     ABI class: X.Org XInput driver, version 11.0
[    32.850] (II) Synaptics touchpad driver version 1.2.2
[    32.850] (**) Option "Device" "/dev/input/event5"
[    32.851] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    32.851] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    32.851] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    32.851] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    32.851] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    32.851] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.851] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    32.851] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    32.851] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    32.851] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    32.852] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    32.852] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    32.853] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    32.854] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    32.854] (II) No input driver/identifier specified (ignoring)
[    35.854] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse1)
[    35.854] (II) No input driver/identifier specified (ignoring)
[    35.881] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event6)
[    35.881] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    35.881] (**) TPPS/2 IBM TrackPoint: always reports core events
[    35.882] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
[    35.882] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    35.882] (II) TPPS/2 IBM TrackPoint: Found relative axes
[    35.882] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    35.882] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    35.882] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    35.882] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.882] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    35.882] (II) TPPS/2 IBM TrackPoint: initialized for relative axes

---

### Post by 16sinker on 2010-10-11
> **rapiertg said:**
> now choose Places from menu and choose Home. There you will find a file called xorg.txt. Is it there? If so then attach it to your post.

I posted the contents of the xorg.txt file as you requested 11 hours ago. I had hoped that from the volume of this file something would have been apparent to you relative the screen resolution problems that I have with my old Dell. I'm in no hurry to solve this problem with this machine. It may be a problem that we can't resolve, but I want to try to get rid of horizontal scrolling before I pass it on to someone in need of a working computer. Thanks for your help this morning and I'm sorry that I can't be more help. I'm very familiar with Ubuntu as a user and can generally follow instructions provided on this forum, The other Ubuntu machine that I use is running a clean install of Lucid very nicely and it also formerly ran XP at 1024x768 and I've had no resolution problems with it running that resolution. It, however has a 15" screen. I really enjoy using Ubuntu and will continue to use it in order to rehab these old

---

### Post by 16sinker on 2010-10-11
> **rapiertg said:**
> now choose Places from menu and choose Home. There you will find a file called xorg.txt. Is it there? If so then attach it to your post.

I posted the contents of the xorg.txt file as you requested 11 hours ago. I had hoped that from the volume of this file something would have been apparent to you relative the screen resolution problems that I have with my old Dell. I'm in no hurry to solve this problem with this machine. It may be a problem that we can't resolve, but I want to try to get rid of horizontal scrolling before I pass it on to someone in need of a working computer. Thanks for your help this morning and I'm sorry that I can't be more help. I'm very familiar with Ubuntu as a user and can generally follow instructions provided on this forum, The other Ubuntu machine that I use is running a clean install of Lucid very nicely and it also formerly ran XP at 1024x768 and I've had no resolution problems with it running that resolution. It, however has a 15" screen. I really enjoy using Ubuntu and will continue to use it in order to rehab these old machines.

---

### Post by rapiertg on 2010-10-12
> **16sinker said:**
> I posted the contents of the xorg.txt file as you requested 11 hours ago. I had hoped that from the volume of this file something would have been apparent to you relative the screen resolution problems that I have with my old Dell. I'm in no hurry to solve this problem with this machine. It may be a problem that we can't resolve, but I want to try to get rid of horizontal scrolling before I pass it on to someone in need of a working computer. Thanks for your help this morning and I'm sorry that I can't be more help. I'm very familiar with Ubuntu as a user and can generally follow instructions provided on this forum, The other Ubuntu machine that I use is running a clean install of Lucid very nicely and it also formerly ran XP at 1024x768 and I've had no resolution problems with it running that resolution. It, however has a 15" screen. I really enjoy using Ubuntu and will continue to use it in order to rehab these old machines.

To be honest, i tried to investigate your logs but i doubt i can be of help any further as my ubuntu experience can be just too small. According to some info from web your monitor is capable of displaing 1024x768. I dont know why its not picking up resolution from config file. Ok lets try it again with more specific xorg.conf:

Open the file with a command:

```

sudo gedit /etc/X11/xorg.conf

```delete everything, and paste following:
```

Section "InputDevice"
     Identifier    "Generic Keyboard"
     Driver        "kbd"
     Option        "XkbRules"    "xorg"
     Option        "XkbModel"    "pc105"
     Option        "XkbLayout"    "us"
 EndSection
  Section "InputDevice"
     Identifier  "Mouse0"
     Driver      "mouse"
     Option      "Protocol" "PS/2"
     Option      "Device" "/dev/mouse"
 EndSection
  Section "InputDevice"
     Identifier    "Synaptics Touchpad"
     Driver        "synaptics"
     Option        "SendCoreEvents"    "true"
     Option        "Device"        "/dev/psaux"
     Option        "Protocol"        "auto-dev"
     Option        "HorizEdgeScroll"    "0"
 EndSection
  Section "Device"
     Identifier  "VideoCard0"
     ### Available Driver options are:-
         #Option     "NoAccel"
         #Option     "SWcursor"
         #Option     "HWcursor"
         #Option     "Dac6Bit"
         #Option     "Dac8Bit"
         #Option     "ForcePCIMode"
         #Option     "CCEPIOMode"
         #Option     "CCENoSecurity"
         #Option     "CCEusecTimeout"
         #Option     "AGPSize"
         #Option     "RingSize"
         #Option     "VBListSize"
         #Option     "VBSize"
         #Option     "UseCCEfor2D"
         #Option     "PanelWidth"
         #Option     "PanelHeight"
         #Option     "UseFBDev"
     Driver      "r128"
     VendorName  "ATI"
     BoardName   "Rage 128 Mobility M3 AGP 2x"
     BusID       "PCI:1:0:0"
 EndSection
  Section "Monitor"
     Identifier    "Monitor0"
     HorizSync    31-75
     VertRefresh    50-85
     Option        "DPMS"
 EndSection
  Section "Screen"
         Identifier "Screen0"
         Device     "VideoCard0"
         Monitor    "Monitor0"
         DefaultDepth   24
         SubSection "Display"
                 Viewport   0 0
                 Depth     16
                 Modes   "1280x1024" "1024x768"
         EndSubSection
         SubSection "Display"
                 Viewport   0 0
                 Depth     24
                 Modes   "1280x1024" "1024x768"
         EndSubSection
 EndSection
  Section "ServerLayout"
     Identifier    "Default Layout"
     Screen        "Screen0"
     InputDevice    "Synaptics Touchpad"
 EndSection
```

save the file and reboot. Then check resolutions. 

PS. Sorry not to answer for quite a long time but i had no PC near me.

---

### Post by 16sinker on 2010-10-12
> **rapiertg said:**
> To be honest, i tried to investigate your logs but i doubt i can be of help any further as my ubuntu experience can be just too small. According to some info from web your monitor is capable of displaing 1024x768. I dont know why its not picking up resolution from config file. Ok lets try it again with more specific xorg.conf:

Open the file with a command:

```

sudo gedit /etc/X11/xorg.conf

```delete everything, and paste following:
```

Section "InputDevice"
     Identifier    "Generic Keyboard"
     Driver        "kbd"
     Option        "XkbRules"    "xorg"
     Option        "XkbModel"    "pc105"
     Option        "XkbLayout"    "us"
 EndSection
  Section "InputDevice"
     Identifier  "Mouse0"
     Driver      "mouse"
     Option      "Protocol" "PS/2"
     Option      "Device" "/dev/mouse"
 EndSection
  Section "InputDevice"
     Identifier    "Synaptics Touchpad"
     Driver        "synaptics"
     Option        "SendCoreEvents"    "true"
     Option        "Device"        "/dev/psaux"
     Option        "Protocol"        "auto-dev"
     Option        "HorizEdgeScroll"    "0"
 EndSection
  Section "Device"
     Identifier  "VideoCard0"
     ### Available Driver options are:-
         #Option     "NoAccel"
         #Option     "SWcursor"
         #Option     "HWcursor"
         #Option     "Dac6Bit"
         #Option     "Dac8Bit"
         #Option     "ForcePCIMode"
         #Option     "CCEPIOMode"
         #Option     "CCENoSecurity"
         #Option     "CCEusecTimeout"
         #Option     "AGPSize"
         #Option     "RingSize"
         #Option     "VBListSize"
         #Option     "VBSize"
         #Option     "UseCCEfor2D"
         #Option     "PanelWidth"
         #Option     "PanelHeight"
         #Option     "UseFBDev"
     Driver      "r128"
     VendorName  "ATI"
     BoardName   "Rage 128 Mobility M3 AGP 2x"
     BusID       "PCI:1:0:0"
 EndSection
  Section "Monitor"
     Identifier    "Monitor0"
     HorizSync    31-75
     VertRefresh    50-85
     Option        "DPMS"
 EndSection
  Section "Screen"
         Identifier "Screen0"
         Device     "VideoCard0"
         Monitor    "Monitor0"
         DefaultDepth   24
         SubSection "Display"
                 Viewport   0 0
                 Depth     16
                 Modes   "1280x1024" "1024x768"
         EndSubSection
         SubSection "Display"
                 Viewport   0 0
                 Depth     24
                 Modes   "1280x1024" "1024x768"
         EndSubSection
 EndSection
  Section "ServerLayout"
     Identifier    "Default Layout"
     Screen        "Screen0"
     InputDevice    "Synaptics Touchpad"
 EndSection
```

save the file and reboot. Then check resolutions. 

PS. Sorry not to answer for quite a long time but i had no PC near me.
Worked like a charm! Now have 1024 x768 resolution. Good fix Rapiertg. Thanks

---

### Post by 16sinker on 2010-10-12
> **16sinker said:**
> Worked like a charm! Now have 1024 x768 resolution. Good fix Rapiertg. Thanks
Now if someone would direct me as to how and where to mark this thread as solved, I will do so. Thanks again.

---

### Post by rapiertg on 2010-10-12
> **16sinker said:**
> Now if someone would direct me as to how and where to mark this thread as solved, I will do so. Thanks again.
Im glad i could help. Good luck in Yours futher ubuntu experience.

---

### Post by 16sinker on 2010-10-12
I used the thread tools and marked this thread solved. Please let me know if there is anything additionally to meet the standards of this Forum. It is an enjoyable experience to be involved in this community of Ubuntu Forums. I have learned from following the instructions of those that are involved in helping those of us who are lacking in the technical skills that solve these problems. I hope to aquire those skills so that I can contribute.

---

### Post by Dorie on 2011-06-30
Hi!   I've read through this thread, and was tempted to try the same fix, but noticed that it has been tailored in some ways to fit the particular specifications (video card, etc) of the original user's problem computer.

I have a completely different setup, and a slightly different problem in that the screen resolution is definitely off, but not to the extent that it causes sideways scrolling to occur.  

I'm also having problems with the sound, but I doubt it's related..

Anywho, I was wondering if someone here could help me edit the fix so that I could try altering that xorg file on this computer. :)  I can post the same text file he posted, if that's useful, or just give you my specifications... 

This computer has a 790FX-GD70 motherboard, not sure about the rest off the top of my head.  I can look up whatever you need?

I'm new here, and this thread is "solved", so maybe I'm posting in the wrong place.  But just thought I'd give it a try...

Thanks,
Dorie

---

