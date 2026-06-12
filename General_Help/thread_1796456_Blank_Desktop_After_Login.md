---
title: "Blank Desktop After Login"
date: 2011-07-03
forum: General Help
---

### Post by Base_Dpx on 2011-07-03
Hello everyone. I'm new to Ubuntu, so new that in fact that this is my first install of the Operating System. I'm currently using Ubuntu 11.04. At login screen, the bottom bar is present, but after I log in it disappears and all I'm left with is just the mouse cursor and the desktop background. This happens for both the Ubuntu and Ubuntu Classic choices. But both top and bottom bars are present when I choose the Ubuntu Classic (No Effects) and Ubuntu (Safe Mode) options. Is there a reason that this keeps happening? A bad install? Hardware can't support the new version of Ubuntu?

I apologize in advance if this topic has already been discussed, but I was unable to find the discussion(s) on this specific problem on the forums.

---

### Post by wildmanne39 on 2011-07-03
> **Base_Dpx said:**
> Hello everyone. I'm new to Ubuntu, so new that in fact that this is my first install of the Operating System. I'm currently using Ubuntu 11.04. At login screen, the bottom bar is present, but after I log in it disappears and all I'm left with is just the mouse cursor and the desktop background. This happens for both the Ubuntu and Ubuntu Classic choices. But both top and bottom bars are present when I choose the Ubuntu Classic (No Effects) and Ubuntu (Safe Mode) options. Is there a reason that this keeps happening? A bad install? Hardware can't support the new version of Ubuntu?

I apologize in advance if this topic has already been discussed, but I was unable to find the discussion(s) on this specific problem on the forums.Hi, what is your system specs? put these commands in a terminal
```
sudo lshw
```
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Please post screen shots.

---

### Post by Base_Dpx on 2011-07-04
Alright, after fooling around with how to do screenshots in the terminals I think I manged to get most of the information  :lol:

---

### Post by wildmanne39 on 2011-07-04
> **Base_Dpx said:**
> Alright, after fooling around with how to do screenshots in the terminals I think I manged to get most of the information  :lol:HI, the main thing I was looking for is the graphics card you have but I did not see it, all you need to do is copy and paste the outcome of those commands here by using the directions I gave you in my previous post, here do this one last command
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Base_Dpx on 2011-07-04
Ohhhh okay, my mistake.

```
dpx@Base-L:~$ sudo lshw
[sudo] password for dpx: 
base-l                    
    description: Desktop Computer
    version: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 4CoreDual-SATA2.
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P2.20
          date: 09/22/2009
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E6600  @ 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: CPUSocket
          size: 3066MHz
          capacity: 3066MHz
          width: 64 bits
          clock: 267MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 2
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 3050MHz
          capabilities: vmx ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: PT880 Ultra/PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f8000000-fbffffff
        *-generic UNCLAIMED
             description: PIC
             product: PT894 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: PT890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:e000(size=4096) memory:fea00000-feafffff memory:d0000000-dfffffff
           *-display
                description: VGA compatible controller
                product: RV770 [Radeon HD 4850]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:65 memory:d0000000-dfffffff memory:feae0000-feaeffff ioport:e000(size=256) memory:feac0000-feadffff
           *-multimedia
                description: Audio device
                product: HD48x0 audio
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:66 memory:feafc000-feafffff
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) ioport:d000(size=256)
           *-disk
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: CC1H
                serial: 9VS44JFX
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b572b572
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: be79e3cb-9e41-7848-9834-22db5227634d
                   size: 1377GiB
                   capacity: 1377GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-10-09 13:01:13 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /boot
                      capacity: 245MiB
                      configuration: mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1906MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 9536MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /home
                      capacity: 8311MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:c480(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:c800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:c880(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:cc00(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fe9ffc00-fe9ffcff
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:25:22:34:50:84
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.1.8 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:c000(size=256) memory:fe9ff800-fe9ff8ff
        *-pci:2
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
     *-pci:1
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:7
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:67 memory:febfc000-febfffff
``````
dpx@Base-L:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV770
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
``````
dpx@Base-L:~$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]

```

---

### Post by wildmanne39 on 2011-07-04
Hi, I am not sure that you have a problem, when you are logged into the one that just says ubuntu move your mouse all the way to the left of the screen and does the launcher come out? There is no bottom bar in natty, and no desktop icons. Also if you move your cursor all the way to the top left corner of the screen there is a little ubuntu icon click on it and the apps menu will open, or you can open it by hitting alt+f2 and type what you are looking for in the search box. In my signature there are guides for using natty, if you do not have the launcher on the left of the screen when you move your cursor all the way to the left when logged in as ubuntu post back here with screenshots, if you do please mark thread solved.

---

### Post by Base_Dpx on 2011-07-04
There's no icon in the top left, or any kind of launcher on the left side. Actually, I can't do any kind of commands except the tty terminals (ctrl+alt+f1,f2,f3 etc...).  Couldn't even take a screenshot. Also looked at your links, still no solvable solution. 

Again, sorry for causing you so much grief.

---

### Post by wildmanne39 on 2011-07-05
> **Base_Dpx said:**
> There's no icon in the top left, or any kind of launcher on the left side. Actually, I can't do any kind of commands except the tty terminals (ctrl+alt+f1,f2,f3 etc...).  Couldn't even take a screenshot. Also looked at your links, still no solvable solution. 

Again, sorry for causing you so much grief.
Hi, you are not causing any problems I am on here to help people and I will help as long as I can. Did you do an upgrade? instead of a clean install. If so you should look at this link.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)
this may be the problem, sometimes it takes a little longer to get to the fix but I usually get there.

---

### Post by Base_Dpx on 2011-07-06
I did a clean install. Still followed the directions of that link, did it a few times over just to make sure. Still a no go.

---

### Post by pezgordo on 2011-09-16
I'm having exactly the same issue on Laptop Toshiba A215-S5815.

I login in buntu or ubuntu classic mode, hear the login music and then I only see background and mouse pointer, nothing shows up, no KB shortcut works, no left or right mouse click.

Only thing to do is CTRL + ALT + F1,F2,etc.

Video card is ATI x1200.
Ubuntu clasic (no effects) seems to load fine.

Installed 11.04 twice from scratch, same result.

First time from CD (downloaded image just before) and no Internet connection, second time from CD but connected to Internet so it updated averything but ended with the same status.

Will appreciate any help

---

### Post by pezgordo on 2011-10-05
Nobody?

Still not working, only classic mode.

Compiz effects where not working so I installed compiz-icon and settings manager. Tried to change some compiz settings and ended once again with empty desktop.

I'm guessing it has something to do with Unity since I remember reading some option for Unity in compiz manager and maybe that was enabled and triggered the Blank desktop after hitting ok at those compiz settings.

Don't know what to do next.
Probably will fresh install 10.04 again but I was really looking forward to test Natty and specifically Unity.

---

### Post by EScout209 on 2013-01-16
I’m having a similar problem as well.  I installed ubuntu 12.10 fresh beside Windows XP Pro.  I installed it on a Dell Inspiron 600m, using the instructions found here [http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html) (It has a non-PAE processor) The laptop has an ATI video card (Mobility Radeon 9000)  What I find odd is that I have a bunch of usable controls in the upper right edge of the log in screen, which disappear once I log in.

---

### Post by bubbarosa on 2013-03-03
I am having the same problem, but it was after I installed the NVIDIA driver.  On the first reboot it came up except every 10 seconds the screen went black for about 1 or 2 seconds then came back for 10 and continued this.   I installed the Nvidia driver and rebooted and not there is not flashing screen, but I have a desktop picture with nothing on it.  I move the curser all around and no hidden tool bars.   I can right click the mouse and get the create new folder, new document ect screen that pops up with that.  Otherwise nothing else.  I installed this a few days ago and was playing with it and messed it up.  It was working fine until i did something stupid.  But that is how ya learn.  So I reformatted and reinstalled and now this, not working.  I have no clue.

---

### Post by AngyPangy on 2013-03-06
Noone has a fix so far? I have the same problem: I've set it to automatic login, and after I installed ubuntu, there was a bar at the top and everything, but it all went away upon restart

---

### Post by Sebastian Riera on 2013-04-28
I'm completely new to this too and had the same issue. only found this thread to guide me so I was pretty close to giving up and re-installing windows. anyways found a fix that worked for me, but I have no idea if you will have the same luck. Basically, from the empty desktop I pulled up the terminal using the ctrl+alt+t shortcut then typed in "gnome-control-center" to access system settings. once there, I went to "software sources" and  "additional drivers" and then switched between the graphics card drivers until something worked. Again i am completely new to this so don't ask me for more (the first time i used Linux ever was yesterday)

---

