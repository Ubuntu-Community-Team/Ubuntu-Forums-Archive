---
title: "GUI for CPU speed?"
date: 2011-01-24
forum: General Help
---

### Post by qwertyjjj on 2011-01-24
Is there a GUI for CPU speed?
I can't seem to find anything in the Ubuntu software center and I'm trying not to use the command line as a proper OS should need the user to have any command line knowledge - just being lazy :)

I found some stuff about cpufreq and I installed it but it doesn't show up anywhere.

---

### Post by hwttdz on 2011-01-24
There's hardinfo, which you can install and add to the menus (if it doesn't get added automatically on install).  Of course in a proper OS you should be able to do anything without having to open up any gui's.  I'd prefer grep "@" /proc/cpuinfo or maybe 
sudo dmidecode|grep "Current Speed"
but whatever floats your boat.

Edit: realizes the OP does not state if you're only interested in determining the cpu speed or changing it yourself.  I had assumed the former.  If you meant the former the less elegant than command line methods (cpufreq-selector, and others) would be to install gnome-applets then add to panel "cpu frequency scaling monitor".

---

### Post by qwertyjjj on 2011-01-24
> **hwttdz said:**
> There's hardinfo, which you can install and add to the menus (if it doesn't get added automatically on install).  Of course in a proper OS you should be able to do anything without having to open up any gui's.  I'd prefer grep "@" /proc/cpuinfo or maybe 
sudo dmidecode|grep "Current Speed"
but whatever floats your boat.

Edit: realizes the OP does not state if you're only interested in determining the cpu speed or changing it yourself.  I had assumed the former.  If you meant the former the less elegant than command line methods (cpufreq-selector, and others) would be to install gnome-applets then add to panel "cpu frequency scaling monitor".

I added the panel and it says 800MHz. The CPU should be at 1.73 max but I would like to have it at least up at 1.0 or 1.2.
Not sure why it doesn;t increase automatically, the speedstep in Intel's are supposed but mine never seems to.
I clicked on 1.02 but it won;t increase the speed.

---

### Post by robert shearer on 2011-01-24
Depends if your cpu supports scaling.

Try this...
right click on the panel and choose 'add to panel'
In the window that opens scroll down to 'cpu frequency scaling monitor' and add it to the panel.

Once it is installed it will show a real-time readout of cpu speed if you hover the mouse over it.
Right click on it for options such as 'performance' etc.

> 
I added the panel and it says 800MHz.

Is it set for power saving ? try something  cpu intensive and monitor it.
It should ramp up then down again when the task is finished

---

### Post by qwertyjjj on 2011-01-24
> **robert shearer said:**
> Depends if your cpu supports scaling.

Try this...
right click on the panel and choose 'add to panel'
In the window that opens scroll down to 'cpu frequency scaling monitor' and add it to the panel.

Once it is installed it will show a real-time readout of cpu speed if you hover the mouse over it.
Right click on it for options such as 'performance' etc.



Is it set for power saving ? try something  cpu intensive and monitor it.
It should ramp up then down again when the task is finished

I changed it to performance and on demand and nothing.
Loaded FF plus some other programs and it doesn't budge from 800.
I had the same problem on Windows and for that I had to use something called Notebook Hardware control to ramp up the CPU manually.
When I right click the panel over the 800MHz it gives me 4 options but it never changes the CPU even if I click on a higher speed.

When I type this in the temrinal:
sudo dpkg-reconfigure gnome-applets
It doesn't give me any text or options, it just goes back to the prompt. I think the SPU freq in the panel is just a monitor?

---

### Post by davidmohammed on 2011-01-24
try and stress your laptop and see if the CPU goes to maximum

e.g.

sudo apt-get install stress

then type

stress --cpu 20

---

### Post by robert shearer on 2011-01-24
OK, now we need some useful info so you are going to have to run some commands and post here the outputs...
As hwttdz posted...
```
sudo dmidecode|grep "Current Speed"
```
and..
```
cat /proc/cpuinfo
```
and..
```
sudo lshw
```

---

### Post by qwertyjjj on 2011-01-25
> **robert shearer said:**
> OK, now we need some useful info so you are going to have to run some commands and post here the outputs...
As hwttdz posted...
```
sudo dmidecode|grep "Current Speed"
```
and..
```
cat /proc/cpuinfo
```
and..
```
sudo lshw
```

Right now, it seems to be flipping between 800 and 1.73 as it is supposed to. Doesn't this slow the system down a bit though? Wouldn;t it be better running at 1.73 all the time?

```

j@j-Inspiron-9300:~$ sudo dmidecode|grep "Current Speed"
[sudo] password for j: 
	Current Speed: 1733 MHz
j@j-Inspiron-9300:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.73GHz
stepping	: 8
cpu MHz		: 800.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips	: 1596.58
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

j@j-Inspiron-9300:~$ sudo lshw
j-inspiron-9300       
    description: Portable Computer
    product: Inspiron 9300
    vendor: Dell Inc.
    serial: 2TJ2Z1J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-5400-104A-8032-B2C04F5A314A
  *-core
       description: Motherboard
       product: 0C5668
       vendor: Dell Inc.
       physical id: 0
       serial: .2TJ2Z1J.CN129615AJ3266.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (09/19/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1733MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F9B0000
             physical id: 0
             serial: D34253B9
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F9B0000
             physical id: 1
             serial: D435CD3D
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:dfd00000-dfefffff memory:d0000000-d7ffffff
           *-display
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:41 memory:d0000000-d7ffffff ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfe00000-dfe1ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:dfc00000-dfcfffff ioport:80000000(size=67108864)
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:14:22:de:03:0d
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: irq:18 memory:dfcfe000-dfcfffff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: b3
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00704030-b0070402f irq:19 memory:dfc00000-dfc00fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff memory:84000000-87ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:dfcfc800-dfcfcfff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 17
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:dfcfc700-dfcfc7ff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:d3:04:21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.33 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:dfcfd000-dfcfdfff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:ee00(size=256) ioport:ec80(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG MP0603H
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: UD20
                serial: S03ZJ10YB51849
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f0170
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7c78da4b-a063-46b6-b567-91aecbbfc3fb
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-22 18:12:59 filesystem=ext4 lastmountpoint=/&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;&#591;&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;&#65533;P&#65533;&#65533;Dq!&#65533;&#65533;&#65533;&#65533;&#65533;@&#65533;&#65533; &#65533;&#65533; &#65533;&#65533;&#65533;&#591;&#65533;A&#65533;h&#65533;&#65533;&#65533;s!&#65533; j modified=2011-01-22 18:34:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-25 10:21:36 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2380MiB
                   capacity: 2380MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2380MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRW/DVD TSL462C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)
  *-battery
       product: DELL F51335A
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
j@j-Inspiron-9300:~$

```

---

### Post by robert shearer on 2011-01-25
> Right now, it seems to be flipping between 800 and 1.73 as it is supposed to.

I guess you rebooted. :)

> Doesn't this slow the system down a bit though? Wouldn;t it be better running at 1.73 all the time?

Doesn't this save your battery a bit and ensure cool operation, or would you rather run the battery down faster and get very hot while doing nothing ?? :)

Right click on the cpu scaling applet and choose 'performance'.
Close the applet and reboot.
Does it now run at 1.73 all the time ? can you tell any difference ?.

I run my machines for power-saving. My power bill is cheaper and I am saving some precious resources of this fair and green planet.

Theoretically there may be a slight lag when opening apps but I haven't noticed any in practice.
Once a cpu intensive app is running then the cpu is scaled up anyway.

I don't game so ymmv ?
What are you running that you feel you need constant high processor operation for ?.

---

### Post by qwertyjjj on 2011-01-25
> **robert shearer said:**
> I guess you rebooted. :)



Doesn't this save your battery a bit and ensure cool operation, or would you rather run the battery down faster and get very hot while doing nothing ?? :)

Right click on the cpu scaling applet and choose 'performance'.
Close the applet and reboot.
Does it now run at 1.73 all the time ? can you tell any difference ?.

I run my machines for power-saving. My power bill is cheaper and I am saving some precious resources of this fair and green planet.

Theoretically there may be a slight lag when opening apps but I haven't noticed any in practice.
Once a cpu intensive app is running then the cpu is scaled up anyway.

I don't game so ymmv ?
What are you running that you feel you need constant high processor operation for ?.

I've got Virtual Box running , which seems to slow down sometimes.
As we speak, I have rebooted and now it is stuck at 800 again.
It's almost like the Intel switch isn;t working. I notice it especially if the fan comes on, it won;t switch up to 1.73 after that.

---

### Post by qwertyjjj on 2011-01-25
> **qwertyjjj said:**
> I've got Virtual Box running , which seems to slow down sometimes.
As we speak, I have rebooted and now it is stuck at 800 again.
It's almost like the Intel switch isn;t working. I notice it especially if the fan comes on, it won;t switch up to 1.73 after that.

any ideas why the speed switch would stop working?

j@j-Inspiron-9300:~$ sudo modprobe p4_clockmod
[sudo] password for j: 
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.35-24-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): Device or resource busy
-Inspiron-9300:~$ nano /etc/modules
-Inspiron-9300:~$ nano /etc/modules
-Inspiron-9300:~$ p4_clockmod
p4_clockmod: command not found
-Inspiron-9300:~$ sudo cpufreq-selector -f 1000000
-Inspiron-9300:~$ sudo cpufreq-selector -f 1070000
-Inspiron-9300:~$ sudo cpufreq-selector -f 1070000
-Inspiron-9300:~$

---

### Post by qwertyjjj on 2011-01-25
It started off successfully switching between 800, 1.07, 1.33, and 1.73 and now all of a sudden it is stuck on 800 again and not increasing no matter how I try to load the CPU up:

```


j@j-Inspiron-9300:~$ sudo dmidecode|grep "Current Speed"
[sudo] password for j: 
	Current Speed: 800 MHz
j@j-Inspiron-9300:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.73GHz
stepping	: 8
cpu MHz		: 800.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips	: 1596.64
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

j@j-Inspiron-9300:~$ sudo lshw
j-inspiron-9300       
    description: Portable Computer
    product: Inspiron 9300
    vendor: Dell Inc.
    serial: 2TJ2Z1J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-5400-104A-8032-B2C04F5A314A
  *-core
       description: Motherboard
       product: 0C5668
       vendor: Dell Inc.
       physical id: 0
       serial: .2TJ2Z1J.CN129615AJ3266.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (09/19/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.73GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F9B0000
             physical id: 0
             serial: D34253B9
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F9B0000
             physical id: 1
             serial: D435CD3D
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:dfd00000-dfefffff memory:d0000000-d7ffffff
           *-display
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:41 memory:d0000000-d7ffffff ioport:de00(size=256) memory:dfdf0000-dfdfffff memory:dfe00000-dfe1ffff
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:bf60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:bf40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bf20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:ffa80800-ffa80bff
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:dfc00000-dfcfffff ioport:80000000(size=67108864)
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:14:22:de:03:0d
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
                resources: irq:18 memory:dfcfe000-dfcfffff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: b3
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00704030-b0070402f irq:19 memory:dfc00000-dfc00fff ioport:2000(size=256) ioport:2400(size=256) memory:80000000-83ffffff memory:84000000-87ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:dfcfc800-dfcfcfff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 17
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:17 memory:dfcfc700-dfcfc7ff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 05
                serial: 00:13:ce:d3:04:21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.33 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:dfcfd000-dfcfdfff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:16 ioport:ed00(size=256) ioport:ec40(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:ee00(size=256) ioport:ec80(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG MP0603H
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: UD20
                serial: S03ZJ10YB51849
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f0170
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7c78da4b-a063-46b6-b567-91aecbbfc3fb
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-22 18:12:59 filesystem=ext4 lastmountpoint=/5[;!&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;9&#65533;P&#65533;&#65533;&#65533;Dq!&#65533;P&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;s!&#65533; j modified=2011-01-22 18:34:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-25 16:49:17 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2380MiB
                   capacity: 2380MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2380MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRW/DVD TSL462C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:10c0(size=32)
  *-battery
       product: DELL F51335A
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
j@j-Inspiron-9300:~$

```

---

### Post by robert shearer on 2011-01-25
ok, hold off on posting the results of 
```
sudo lshw
```  everytime. It is a big output and we only need it  **once**.(it is a list of your hardware and won't change ok.)

just post the output of 
```
sudo dmidecode|grep "Current Speed"
```
When you feel you need to report the speed.

> I notice it especially if the fan comes on, it won;t switch up to 1.73 after that. 


Sounds like the processor is getting too hot and is being throttled until the fan cools it enough.
That's a hardware based safety measure and no amount of fiddling with software will fix it.

When was the last time this machine was cleaned ??
'Cause these symptoms are indicative of crud and dust stopping the cooling airflow over the cpu's heat-sink.

Result, the cpu gets too hot and is throttled to stop it destroying itself.

Note that when the machine is booted from cold the monitor shows it adjusting cpu scaling as it should and when you reboot hot you can't get it to scale.

Get it cleaned and maybe even have the heat-sink checked to see that it is fitted well and the thermal transfer paste hasn't dried out.

---

### Post by qwertyjjj on 2011-01-25
> **robert shearer said:**
> ok, hold off on posting the results of 
```
sudo lshw
```  everytime. It is a big output and we only need it  **once**.(it is a list of your hardware and won't change ok.)

just post the output of 
```
sudo dmidecode|grep "Current Speed"
```
When you feel you need to report the speed.



Sounds like the processor is getting too hot and is being throttled until the fan cools it enough.
That's a hardware based safety measure and no amount of fiddling with software will fix it.

When was the last time this machine was cleaned ??
'Cause these symptoms are indicative of crud and dust stopping the cooling airflow over the cpu's heat-sink.

Result, the cpu gets too hot and is throttled to stop it destroying itself.

Note that when the machine is booted from cold the monitor shows it adjusting cpu scaling as it should and when you reboot hot you can't get it to scale.

Get it cleaned and maybe even have the heat-sink checked to see that it is fitted well and the thermal transfer paste hasn't dried out.

I had to replace the GPU recently but I didn;t clean out the CPU fan which I should have done. I can open it up again because I'm pretty sure it had dust round it but the vent is still clear enough. Would a slight bit of dust cause that problem? It's at 800MHz now and the fan has come back on after about 1hr of it being off. When I had Notebook Hardware control on Windows XP and I would jam it up to 1.73 the fan came on almost immediately.

strange thing is that it ran at 1.73 no problems with fan on so why throttle it if it can run at that speed without major over heating?

---

### Post by robert shearer on 2011-01-25
rereading your posts...
> j@j-Inspiron-9300:~$ sudo modprobe p4_clockmod
[sudo] password for j:
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.35-24-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): Device or resource busy

You may have the wrong module..
see this link..
[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

It's old but seems to use your cpu for illustration and lists the required module as..speedstep_centrino (dont think a p4 module will work) 
speedstep_centrino is deprecated though.

[http://www.linux-phc.org/forum/viewtopic.php?f=8&t=202](http://www.linux-phc.org/forum/viewtopic.php?f=8&t=202)

---

### Post by qwertyjjj on 2011-01-26
> **robert shearer said:**
> rereading your posts...


You may have the wrong module..
see this link..
[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

It's old but seems to use your cpu for illustration and lists the required module as..speedstep_centrino (dont think a p4 module will work) 
speedstep_centrino is deprecated though.

[http://www.linux-phc.org/forum/viewtopic.php?f=8&t=202](http://www.linux-phc.org/forum/viewtopic.php?f=8&t=202)

thanks.
why would the new cpufreq not support centrinos?

cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
**  current policy: frequency should be within 800 MHz and 800 MHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.73 GHz:1.99%, 1.33 GHz:0.25%, 1.07 GHz:0.09%, 800 MHz:97.67%  (29872)

---

### Post by robert shearer on 2011-01-26
Odd,   I am at a loss from here so hope someone else can chime in.

Mr Google has a few interesting comments here...
 [http://ubuntuforums.org/archive/index.php/t-659640.html](http://ubuntuforums.org/archive/index.php/t-659640.html)
especially the last couple of posts.

also here...[http://ubuntuforums.org/archive/index.php/t-904748.html](http://ubuntuforums.org/archive/index.php/t-904748.html) re speed-step in bios

and here....[http://www.dslreports.com/forum/r24757626-cpu-freq-scaling-dead](http://www.dslreports.com/forum/r24757626-cpu-freq-scaling-dead)  re kernel version.

---

### Post by qwertyjjj on 2011-01-26
> **robert shearer said:**
> Odd,   I am at a loss from here so hope someone else can chime in.

Mr Google has a few interesting comments here...
 [http://ubuntuforums.org/archive/index.php/t-659640.html](http://ubuntuforums.org/archive/index.php/t-659640.html)
especially the last couple of posts.

also here...[http://ubuntuforums.org/archive/index.php/t-904748.html](http://ubuntuforums.org/archive/index.php/t-904748.html) re speed-step in bios

and here....[http://www.dslreports.com/forum/r24757626-cpu-freq-scaling-dead](http://www.dslreports.com/forum/r24757626-cpu-freq-scaling-dead)  re kernel version.

I'll try those thanks.
One last thing, is there anyway I can jam up the speed to 1.73 manually?
I was able to do this with Notebook hardware control on XP so isn't there a similar utility for Linux?

setting the upper frequency makes no difference to the lower and upper in the info:

```

j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 800 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.73 GHz:0.12%, 1.33 GHz:0.00%, 1.07 GHz:0.00%, 800 MHz:99.88%  (1)
j@j-Inspiron-9300:~$ sudo cpufreq-set -u 1.73GHz
[sudo] password for j: 
j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
**  current policy: frequency should be within 800 MHz and 800 MHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.73 GHz:0.12%, 1.33 GHz:0.00%, 1.07 GHz:0.00%, 800 MHz:99.88%  (1)
j@j-Inspiron-9300:~$ 

```

---

### Post by qwertyjjj on 2011-01-27
Here is an example where for no reason at all it changes the speed to 800 to 800. The fan didn't even come on so it can't be the PCU getting hot.
I have highlighted the times in bold 15 mins apart with the giverner speed settings.

```

j@j-Inspiron-9300:~$ date
**Thu Jan 27 09:05:41 CET 2011**
j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
 ** current policy: frequency should be within 800 MHz and 1.73 GHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.73 GHz.
  cpufreq stats: 1.73 GHz:18.10%, 1.33 GHz:1.19%, 1.07 GHz:0.59%, 800 MHz:80.12%  (9055)

j@j-Inspiron-9300:~$ date
**Thu Jan 27 09:20:23 CET 2011**
j@j-Inspiron-9300:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 1.73 GHz
  available frequency steps: 1.73 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
**  current policy: frequency should be within 800 MHz and 800 MHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 1.73 GHz:24.51%, 1.33 GHz:3.24%, 1.07 GHz:1.13%, 800 MHz:71.13%  (28892) 

```

---

### Post by cascade9 on 2011-01-27
> **qwertyjjj said:**
> I changed it to performance and on demand and nothing.
Loaded FF plus some other programs and it doesn't budge from 800.
I had the same problem on Windows and for that I had to use something called Notebook Hardware control to ramp up the CPU manually.


Probably a hardware error, dont blame ubuntu for that. If its not a hardware error, I'd guess its a BIOS problem. Could be either the BIOS setings used or some other more esoteric BIOS problem.   

> **qwertyjjj said:**
> any ideas why the speed switch would stop working?

j@j-Inspiron-9300:~$ sudo modprobe p4_clockmod
[sudo] password for j: 
FATAL: Error inserting p4_clockmod (/lib/modules/2.6.35-24-generic/kernel/arch/x86/kernel/cpu/cpufreq/p4-clockmod.ko): Device or resource busy
-Inspiron-9300:~$ nano /etc/modules
-Inspiron-9300:~$ nano /etc/modules
-Inspiron-9300:~$ p4_clockmod
p4_clockmod: command not found
-Inspiron-9300:~$ sudo cpufreq-selector -f 1000000
-Inspiron-9300:~$ sudo cpufreq-selector -f 1070000
-Inspiron-9300:~$ sudo cpufreq-selector -f 1070000
-Inspiron-9300:~$

What on earth made you install P4 clockmod? 

IIRC P4 clockmod was only made for P4s, they had horrible power control. Its liable to just make things worse on non-P4 CPUs.

---

