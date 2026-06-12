---
title: "Karmic Koala 9.10 unresponsive UI"
date: 2010-04-21
forum: General Help
---

### Post by intrader on 2010-04-21
On Dell Inspiron 9200, with or without accelerator for NVIDEA graphics.

P.S. I would like to give 9.10 a chance. Please help.

Scenario - have gedit and browser open (browser with the forum message being edited), then do the following:

1.This example demonstrates one problem (unresponsive single click)
Use the System-->Preferences-->Mouse

Click repeatedly on the light bulb at 1 second interval ---> result: often the light does not turn on.
Result: it appears that the click event does not complete. I have noticed that a mouse-out will cause the click to complete (specifically as in 2. and 3 after a brief moment (hopefully before the drag and drop icon appears).

2. Click on any icon, submit button, close, etc. takes many tries. 

3. Click on any icon, panel button, link, etc. if you linger a moment a floating icon (a drag and drop hand).

4. Scrollbar button and action follow the mouse outside of the scrollbar. The scrollbar sticks - difficult to make scrollbar stop following the mouse.

5. Example, have two visible windows (for example gedit and the browser) From gedit move to browser by click on browser. ---> result takes forever to recognise the focus and click and go to the broser.

6. Unresponsive UI. In browser highlight text in textarea (with difficulty) then chose Copy (slow UI), from this window click on desktop's Applications (takes many clicks to open), from Accessories click on gedit (slow or takes more than one try), paste (speed of paste OK).

7. From browser, Alt-TAB to make the gedit window active, then click on File (slow), Save As (takes many tries)

8. In gedit, selection in Save As of where to save has strange initial behaviour flashing the list of choices several times - eventually I chose 'Desktop'.

9.Back button takes many tries -as with the close button.

10. Back on the gedit window with this text. I try to Edit -> Select All. I have to try several times as the menu flashes.

Many other problems.

Excuse the long rant. 

<History>

While running 9.04 for a long time without problems I noticed the Synaptic Package Manager offering to upgrade to 9.10. I took the bait.:(

I shared with the forum, with no help or any response. I decided to reinstall 9.04. 

I reinstalled 9.04 clean and worked the last few months Ok. 

I manually messed up tomboy when I deleted some mono files, on recommendation from the tomboy irc, I reinstalled 9.10 clearn from .iso.

Unresponsive UI in the new 9.10. 

This prompted me to share this rant.

</history>

Note: from another post, it suggests that GDK has problems and that we need GDK_NATIVE_WINDOWS to 1. I don't have enough knowledge to know where this is done.

Note: Gut feeling, it appears that these problem have to do with an effort to implement 'gestures' in the window manager.
<lshw>
intrader@intrader-laptop:~$ sudo lshw
[sudo] password for intrader: 
intrader-laptop           
    description: Portable Computer
    product: Inspiron 8200
    vendor: Dell Computer Corporation
    serial: 66VRQ11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-3600-1056-8052-B6C04F513131
  *-core
       description: Motherboard
       product: Inspiron 8200
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A11 (01/07/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 Mobile CPU 1.90GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 1200MHz
          capacity: 2500MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts cpufreq
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
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:fc000000-fdffffff memory:e0000000-e7ffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 Go]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master vga_palette cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:11 memory:fc000000-fcffffff memory:e0000000-e7ffffff(prefetchable) memory:fd000000-fd00ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=8192) memory:f4000000-fbffffff memory:40000000-49ffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 78
                serial: 00:08:74:06:89:ea
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.107 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
                resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:48000000-4801ffff(prefetchable)
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f8000000-f8000fff ioport:e000(size=256) ioport:e400(size=256) memory:40000000-43ffffff(prefetchable) memory:f4000000-f7ffffff
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f8001000-f8001fff ioport:e800(size=256) ioport:f000(size=256) memory:44000000-47ffffff(prefetchable) memory:4c000000-4fffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4451 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:f8fff000-f8fff7ff memory:f8ff8000-f8ffbfff
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:4a000000-4a0003ff
           *-disk
                description: ATA Disk
                product: ST9100823A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.05
                serial: 3LG0D0TS
                size: 93GiB (100GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=765f765f
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 44266343-ba16-4d41-b7eb-1a9b336c5c34
                   size: 49GiB
                   capacity: 49GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-07-19 07:40:10 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 6f807b89-f9b0-43b6-a8b0-1963744e6060
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-04-20 14:18:17 filesystem=ext3 modified=2010-04-24 11:25:52 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback mounted=2010-04-24 11:25:52 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1192MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 25GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM GDR8081N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0108
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: UJDA360
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.02
                serial: `MATSHITAUJDA360         1.02205280KME131400432
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:d800(size=256) ioport:dc80(size=64)
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:d400(size=256) ioport:dc00(size=128)
  *-battery
       product: LIP8120DLP
       vendor: Sony Corp.
       physical id: 1
       slot: Right Module Bay
       capacity: 65120mWh
       configuration: voltage=14.8V
intrader@intrader-laptop:~$ 
</lshw>
<lspci>
intrader@intrader-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
</lspci>
<Xorg.0.log>
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux intrader-laptop 2.6.31-20-generic #58-Ubuntu SMP
 Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=756bf3
65-561c-477e-a152-62243ac68104 ro quiet splash
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 

</Xorg.log>
Note: I am attempting to record this with serna On Ubuntu: Recording A Desktop Session - however, playback using Movie Player can't be shown full screen. I also do not see a way to to an attachment while editing a post. Posted a quote below.


Initial Post: Wed 21 Apr 2010 02:45:46 PM PDT.

---

### Post by intrader on 2010-04-22
Please help!

On Dell Inspiron 8200, with or without the NVIDEA accelerator (version 96)


After many hours testing, verified the following cases:
<first>
Use the System-->Preferences-->Mouse

Click repeatedly on the light bulb at 1 second interval ---> result: quite often the light will **not** turn on.
</first>

<second>
While entering this reply, click on scroll-bar button.
Move your mouse over the web page.
Move your mouse --- result: scroll follows the mouse causing scroll of the page.
</second>

<third>
Open the Mouse preferences as in <first>
Click on close 
Quite a few times ---> result: mouse preferences window does not close, takes a few tries.
</third>

<similar to second>
While entering this text which has now its own scollbar.
Click on the scrollbar.
Does not always happen.
Move your mouse over the message. ---> result: Scrollbar follows the mouse, and is difficult to have it stop. ESC sometimes stops the following as well a rightmouse click
</similar to second>

<fourth>
Applications-->Accessories-->gedit 
Click gedit, sometimes it opens gedit
Most of time after click on gedit. ---> result: a drag-and-drop icon (with hand) peels off and follows the mouse difficult to dismiss. ESC always does it.
</fourth>

<fifth>
Open gedit (with difficulty, but it does open)
Put the gedit window where you can still see this message window.
Open a file in gedit.
Highlight something in the gedit window 
Click on the visible message. ---->Result one: with many tries finally the message is again editable in browser.
--->Result two: when edit resumes highlighting continues into this message.
</fifth>

<sixth>
Begin a highlight operation on a line and move mouse to next line.
---> result: click does no cancel the highlight, highlight follows the mouse, difficult to cancel.
</sixth>
There are many more - Most annoying is that buttons do not activate a lot of the time.

Terrible, please help. I am about to go back to 9.04.
<history>
1. In November I tried 9.10 via the Synaptic Package Manager Upgrader path and reported these problems with no response.
2. After many days testing and wasting time, I reinstalled 9.04. This works OK.
3. Recently, I made the mistake to mannually delete some of mono. This caused problems with Tomboy. On the recommendation by tomboy irc, I clean installed (with formatting of / and /home) 9.10
4. The problems are still there.
</history>

---

### Post by intrader on 2010-04-24
> **intrader said:**
> On Dell Inspiron 9200, with or without accelerator for NVIDEA graphics.

P.S. I would like to give 9.10 a chance. Please help.

I am attempting to record this with serna On Ubuntu: Recording A Desktop Session - however, playback using Movie Player can't be shown full screen. I also do not see a way to to an attachement while editing a post. Maybe I need to post a separate thread.

Scenario - have gedit and browser open (browser with the forum message being edited), then do the following:

1.This example demonstrates one problem (unresponsive single click)
Use the System-->Preferences-->Mouse

Click repeatedly on the light bulb at 1 second interval ---> result: often the light does not turn on.
Result: it appears that the click event does not complete. I have noticed that a mouse-out will cause the click to complete (specifically as in 2. and 3 after a brief moment (hopefully before the drag and drop icon appears).

2. Click on any icon, submit button, close, etc. takes many tries. 

3. Click on any icon, panel button, link, etc. if you linger a moment a floating icon (a drag and drop hand).

4. Scrollbar button and action follow the mouse outside of the scrollbar. The scrollbar sticks - difficult to make scrollbar stop following the mouse.

5. Example, have two visible windows (for example gedit and the browser) From gedit move to browser by click on browser. ---> result takes forever to recognise the focus and click and go to the broser.

6. Unresponsive UI. In browser highlight text in textarea (with difficulty) then chose Copy (slow UI), from this window click on desktop's Applications (takes many clicks to open), from Accessories click on gedit (slow or takes more than one try), paste (speed of paste OK).

7. From browser, Alt-TAB to make the gedit window active, then click on File (slow), Save As (takes many tries)

8. In gedit, selection in Save As of where to save has strange initial behaviour flashing the list of choices several times - eventually I chose 'Desktop'.

9.Back button takes many tries -as with the close button.

10. Back on the gedit window with this text. I try to Edit -> Select All. I have to try several times as the menu flashes.

Many other problems.

Excuse the long rant. 

<History>

While running 9.04 for a long time without problems I noticed the Synaptic Package Manager offering to upgrade to 9.10. I took the bait.:(

I shared with the forum, with no help or any response. I decided to reinstall 9.04. 

I reinstalled 9.04 clean and worked the last few months Ok. 

I manually messed up tomboy when I deleted some mono files, on recommendation from the tomboy irc, I reinstalled 9.10 clearn from .iso.

Unresponsive UI in the new 9.10. 

This prompted me to share this rant.

</history>

Note: from another post, it suggests that GDK has problems and that we need GDK_NATIVE_WINDOWS to 1. I don't have enough knowledge to know where this is done.

Note: Gut feeling, it appears that these problem have to do with an effort to implement 'gestures' in the window manager.

Wed 21 Apr 2010 02:45:46 PM PDT.

I am unable to attach, as the file i over 55MB. The playback with Music Box also has problems - when I try to change the size of the window, Music Box terminates. Aweful

---

