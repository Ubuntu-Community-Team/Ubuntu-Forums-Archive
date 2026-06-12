---
title: "root disk check failed! cannot boot :/ ubuntu 10.10"
date: 2011-04-25
forum: General Help
---

### Post by JinsuCraft on 2011-04-25
I applying changes through update manager in ubuntu 10.04 then my computer froze. So I had to restart it manually. 
Now I can't boot ubuntu normal or recovery mode.
I get an error message saying 'the disk drive / is not ready yet or blah blah'.
I don't have a livecd to fix it this with...

but here is my 'cat /etc/fstab' relevant output
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0

Any help would be appreciated!

---

### Post by Rubi1200 on 2011-04-25
Hi and welcome to the forums :-)

You need to try and get hold of a LiveCD because chances are you will need to use it to fix this.

For what it's worth, you could do a chkdsk in Windows and see if it helps.

Download and instructions for an Ubuntu CD:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by JinsuCraft on 2011-04-29
I just made live CD.
What do I need to do?? :/

---

### Post by Rubi1200 on 2011-04-29
You need to set your BIOS to allow booting from the CD. When the computer starts you usually see a screen with the manufacturer's name. At that screen there is an option to enter BIOS, usually something like F2, F12, or similar.

Go into BIOS to the Boot menu and set the computer to boot from the CD drive first (followed by the hard-drive).

Then, do the following:

Choose the option to try Ubuntu on the CD and make sure you are connected to the internet.

Download the boot info script, run it, and post the results here in a new post. There is a link at the bottom of my post with instructions.

Good luck.

---

### Post by JinsuCraft on 2011-04-29
Thx so much for helping me out with this Rubi1200.
Here is the boot info script result.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   109,723,949   109,707,885   f W95 Ext d (LBA)
/dev/sda5              16,128   109,723,949   109,707,822   7 HPFS/NTFS
/dev/sda2    *    109,723,950   156,296,384    46,572,435   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       69bad5cc-d07d-4d91-8029-2e78ce55546b   ext4                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        22581C7E581C5341                       ntfs       Backup                        
/dev/sda5        B6D8C9CDD8C98C55                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6d8c9cdd8c98c55
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b6d8c9cdd8c98c55
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 22581c7e581c5341
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


  11.0GB: boot/grub/grub.cfg
  13.3GB: boot/initrd.img-2.6.35-22-generic
   4.8GB: boot/vmlinuz-2.6.35-22-generic
   4.8GB: boot/vmlinuz-2.6.35-28-generic
  13.3GB: initrd.img
   4.8GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  71 a9 71 c2 71 23 72 33  72 38 72 4a 72 4f 72 59  |q.q.q#r3r8rJrOrY|
00000010  72 6f 72 79 72 85 72 b7  72 c1 72 cb 72 da 72 0c  |roryr.r.r.r.r.r.|
00000020  73 16 73 20 73 2f 73 61  73 6b 73 75 73 84 73 b6  |s.s s/sasksus.s.|
00000030  73 c0 73 ca 73 d9 73 e0  73 e5 73 f1 73 23 74 2d  |s.s.s.s.s.s.s#t-|
00000040  74 37 74 46 74 78 74 82  74 8c 74 9b 74 cd 74 d7  |t7tFtxt.t.t.t.t.|
00000050  74 e1 74 f0 74 22 75 2c  75 36 75 45 75 77 75 81  |t.t.t"u,u6uEuwu.|
00000060  75 8b 75 9a 75 a1 75 a6  75 b2 75 b7 75 ca 75 d4  |u.u.u.u.u.u.u.u.|
00000070  75 e0 75 e5 75 f8 75 02  76 0e 76 13 76 26 76 30  |u.u.u.u.v.v.v&v0|
00000080  76 3c 76 41 76 57 76 61  76 6d 76 72 76 85 76 8f  |v<vAvWvavmvrv.v.|
00000090  76 bb 76 c3 76 cb 76 22  56 47 41 2e 63 70 70 22  |v.v.v.v"VGA.cpp"|
000000a0  2e 00 02 30 00 00 00 00  00 20 00 04 00 02 02 10  |...0..... ......|
000000b0  00 18 00 f6 00 16 01 f5  00 0a 06 d8 76 d8 76 34  |............v.v4|
000000c0  77 34 77 22 2e 5c 76 69  64 65 6f 2e 68 70 70 22  |w4w".\video.hpp"|
000000d0  2e 00 00 28 00 00 00 00  00 16 00 01 00 02 02 10  |...(............|
000000e0  00 14 00 25 03 16 01 7c  77 22 2e 5c 76 69 64 65  |...%...|w".\vide|
000000f0  6f 2e 68 70 70 22 2e 00  64 65 6f 30 00 00 00 00  |o.hpp"..deo0....|
00000100  00 1e 00 03 00 02 02 10  00 18 00 31 03 c4 04 c5  |...........1....|
00000110  04 22 2e c8 77 c8 77 05  78 22 2e 5c 76 69 64 65  |."..w.w.x".\vide|
00000120  6f 2e 68 70 70 22 2e 00  2e 00 00 28 00 00 00 00  |o.hpp".....(....|
00000130  00 18 00 02 00 02 02 10  00 14 00 bd 05 be 05 f0  |................|
00000140  78 19 79 22 2e 5c 76 69  64 65 6f 2e 68 70 70 22  |x.y".\video.hpp"|
00000150  2e 00 68 1c 0f 00 00 00  00 0e 0f bf 03 02 02 10  |..h.............|
00000160  00 90 07 33 00 39 00 3f  00 46 00 4c 00 51 00 57  |...3.9.?.F.L.Q.W|
00000170  00 59 00 67 00 6a 00 6d  00 6f 00 70 00 74 00 76  |.Y.g.j.m.o.p.t.v|
00000180  00 85 00 88 00 8b 00 8d  00 8e 00 92 00 94 00 a2  |................|
00000190  00 a5 00 a8 00 b0 00 b2  00 b3 00 b5 00 bb 00 bd  |................|
000001a0  00 be 00 c0 00 c6 00 c8  00 c9 00 cb 00 cd 00 d0  |................|
000001b0  00 d3 00 d4 00 d6 00 d9  00 e7 00 ea 00 ed 00 01  |................|
000001c0  01 01 07 fe ff ff 3f 00  00 00 2e 02 8a 06 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Rubi1200 on 2011-04-29
Hi,

Is Windows still booting normally?

Look here for Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem # 2, solution # 1 should fix this and don't forget to apply the Permanent Fix once you can boot Ubuntu again.

---

### Post by JinsuCraft on 2011-04-29
ya, windows boot normally.
I have to clarify, I've installed Ubuntu with 10.10 image downloaded from the website.
In this case, is it ok if I use '10.04 upgraded to 10.10' solutions?

---

### Post by Rubi1200 on 2011-04-29
You could try that, but bcbc, the Wubi expert here on the forum, and I have noticed that solution #1 almost always works whereas #2 sometimes fixes it and sometimes not. Or you can try both and see what works best for you.

---

### Post by JinsuCraft on 2011-04-29
Are you referring to the solution #1 for Problem #2?

---

### Post by Rubi1200 on 2011-04-29
Which solution are you referring to?

You seem to have problem #2, we are agreed on that :-)

I am saying to use solution #1 for problem #2 because, in my experience, it almost always works.

However, if you want to try problem #2, solution #2 you are more than welcome. Just know that you may have to use the first solution anyway.

Does this make sense?

---

### Post by JinsuCraft on 2011-04-29
Ya, my bad. I just wanted to make sure.
I just tried it. Let me reboot! first.

---

### Post by JinsuCraft on 2011-04-29
Now Ubuntu boots up and gets to the login screen. Then freezes.
The login screen does not show any users. Normally it should show a user in the login screen, but strangely it doesn't have any users listed.
Should i try different solutions? or Is this a different problem?

---

### Post by Rubi1200 on 2011-04-29
Hmm, that sounds like a different problem. 

I know you are probably really keen to get back to using Ubuntu, but if you can wait just a few hours until bcbc, the Wubi expert, comes online he may know what is going on and have some other solutions.

Thanks for being patient with this.

---

### Post by JinsuCraft on 2011-04-29
No problem, I hope it's not too serious of a problem...

---

### Post by Rubi1200 on 2011-04-29
> **JinsuCraft said:**
> No problem, I hope it's not too serious of a problem...
Thank you :-)

Define not too serious ;)

For the moment, I suspect it may be a graphics-related issue, but I want another opinion.

Meantime, if you could post the specifications for the computer especially graphics card and RAM that would be great.

---

### Post by JinsuCraft on 2011-04-29
I tried to do solution #2..
but I don't have /media/win/wubildr file?
so i can't make a backup of it.
However, /media/win/winboot/wubildr is there. 
I'm assuming that the solution tells me to make a backup just have a backup plan when something goes wrong.
Does it matter if i make a backup of /media/win/wubildr or not?

---

### Post by JinsuCraft on 2011-04-29
```

ubuntu                    
    description: Portable Computer
    product: MXC061
    vendor: Dell Inc.
    serial: HTW3RB1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5400-1057-8033-C8C04F524231
  *-core
       description: Motherboard
       product: 0MG532
       vendor: Dell Inc.
       physical id: 0
       serial: .HTW3RB1.CN7016668C09WC.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A10 (04/02/2007)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Microprocessor
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MiB
             capacity: 4MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: HYMP512S64BP8-C4
             vendor: AD00000000000000
             physical id: 0
             serial: 00005091
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: HYMP512S64BP8-C4
             vendor: AD00000000000000
             physical id: 1
             serial: 00006092
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
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
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff memory:efec0000-efefffff
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
             resources: memory:eff80000-efffffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:efebc000-efebffff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:efd00000-efdfffff ioport:80400000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 02
                serial: 00:18:de:22:28:cb
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:43 memory:efdff000-efdfffff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:efa00000-efcfffff ioport:e0000000(size=2097152)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:ffa80000-ffa803ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:ef900000-ef9fffff
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:6b:90:25
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: irq:17 memory:ef9fe000-ef9fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:ef9fd800-ef9fdfff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:ef9fd400-ef9fd4ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:ef9fd600-ef9fd6ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:02:01.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=r852 latency=0
                resources: irq:18 memory:ef9fd700-ef9fd7ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2080B
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0085
                serial: NW9HT6C2DWFL
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=073e4091
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   size: 52GiB
                   capacity: 52GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/win
                      capacity: 52GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/Backup
                   version: 3.1
                   serial: 3af075d3-b3d6-3d45-a055-6a21ab1f4b6c
                   size: 22GiB
                   capacity: 22GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2006-09-21 15:10:40 filesystem=ntfs label=Backup mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632D
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: DE03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)


```
ran lshw and pasted it on here.
Sorry for the long list. I don't wanna confuse you with my ignorance, so I posted the wholething.

---

### Post by bcbc on 2011-04-29
> **JinsuCraft said:**
> I applying changes through update manager in ubuntu 10.04 then my computer froze. So I had to restart it manually. 
Now I can't boot ubuntu normal or recovery mode.
I get an error message saying 'the disk drive / is not ready yet or blah blah'.
I don't have a livecd to fix it this with...

but here is my 'cat /etc/fstab' relevant output
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0

Any help would be appreciated!
You should avoid hard restarts... Alt+SysRq REISUB instead.

I'd try booting in recovery mode to a root terminal with networking, then enter:
```
apt-get update
apt-get upgrade
```

Or there is a specific recovery menu item to fix package errors.

If you can't do this in recovery mode, then you have to boot from a live CD and chroot into the wubi install and fix the package errors from there.

You might also try fsck'ing the root.disk (but it's more likely that you have half updated packages). Don't fsck the root.disk while mounted.

PS take a backup of the root.disk before repairing just in case - so you can extract data later if things don't work out

---

### Post by JinsuCraft on 2011-04-29
> I'd try booting in recovery mode to a root terminal with networking, then enter:


Code:
apt-get update
apt-get upgrade
Or there is a specific recovery menu item to fix package errors.


I'll try to do this first!. recovery doesn't freeze today.
But, the root terminal doesn't seem to have networking, because when i type in ifconfig, it shows nothing.
Do i need to enable networking first?
If so,

sudo ifup eth1

is this the code for it?
> 
If you can't do this in recovery mode, then you have to boot from a live CD and chroot into the wubi install and fix the package errors from there.

I do have a live CD now. So how do i do this..?
I didn't do my hw and don't know how to do these magic in ubuntu.

---

### Post by bcbc on 2011-04-29
> **JinsuCraft said:**
> I'll try to do this first!. recovery doesn't freeze today.
But, the root terminal doesn't seem to have networking, because when i type in ifconfig, it shows nothing.
Do i need to enable networking first?
If so,

sudo ifup eth1

is this the code for it?

I do have a live CD now. So how do i do this..?
I didn't do my hw and don't know how to do these magic in ubuntu.
If you can boot into recovery it should be a lot easier than chroot'ing. I'm not sure why you have to do anything special to get networking... strange that it's not working. What happens when you try to fix package errors?

---

### Post by JinsuCraft on 2011-04-29
Weird. but /etc/network/interface didn't have any entry about eth0.
anyways, first the recovery mode was read-only.
so I remounted
```

sudo mount -o remount,rw /

```Then I added 
'iface eth0 inet dhcp' in the file.* <- deleted this line after I succesfully recovered my ubuntu. I edited  /etc/network/interfaces to have 'auto eth0' and 'auth wlan0'
Then did 
```

sudo dhclient eth0

```first tried

```

apt-get update

```Then it told me to run
```

dpkg --configure -a

```after
```

apt-get upgrade

```And now it works. Thanks so much! bcbc and rubi!

---

### Post by Rubi1200 on 2011-04-30
Excellent! Really pleased you got this sorted out.

Enjoy :-)

---

