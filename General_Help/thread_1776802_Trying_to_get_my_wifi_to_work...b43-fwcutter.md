---
title: "Trying to get my wifi to work...b43-fwcutter"
date: 2011-06-06
forum: General Help
---

### Post by Mynxenoa on 2011-06-06
I downloaded it, and now I have no idea what to do. Can someone tell me how I need to extract the files, or even find them? I used the synaptic package manager to receive it. 

At first my wifi tells me that the firmware is missing, or the device is not ready. I don't know history of the laptop but I don't know how to test if its operational or not

---

### Post by linuxinstalledfromhdd on 2011-06-06
If you want to download the windows driver for your wireless device, and install it with ndiswrapper, you need to install ndiswrapper from Synaptic first.

---

### Post by Mynxenoa on 2011-06-06
How do you use ndiswrapper after you get it?

---

### Post by jramshu on 2011-06-06
More info is needed. What version of *buntu are you using? Are you using lan? Card specs, etc.

---

### Post by collisionystm on 2011-06-06
> **Mynxenoa said:**
> I downloaded it, and now I have no idea what to do. Can someone tell me how I need to extract the files, or even find them? I used the synaptic package manager to receive it. 

At first my wifi tells me that the firmware is missing, or the device is not ready. I don't know history of the laptop but I don't know how to test if its operational or not

What kind of computer? You don't necessarily need ndiswrapper.

Try this method...

[http://ubuntuforums.org/showthread.php?t=1742147](http://ubuntuforums.org/showthread.php?t=1742147)

---

### Post by walt.smith1960 on 2011-06-06
Most say NDISwrapper should be the last resort, not the first.  It'd probably be a good start to post the output of this command: ```
lspci
``` I'm assuming your wireless card is internal.  If it were a USB 'dongle', you'd use the command ```
lsusb
``` lspci (LSPCI in lower case) **l**i**s**ts your **pci** devices.  Same with lsusb. The output of lspci should look something like this:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```Anyone looking at this would know my ethernet controller (not my network controller/WiFi device) is:  Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02).  Knowing that, others could suggest file edits or downloads to bring the device to life.  I hope this is of some help.

---

### Post by Mynxenoa on 2011-06-12
Here are my stats. Tell me what I need to do again. 


id:



----

      description: 



Notebook
    product: 



HP Pavilion dv6000 (RG254UA#ABA)
    vendor: 



Hewlett-Packard
    version: 



Rev 1
    serial: 



CNF6424J50
    width: 



64 bits
    capabilities: 



smbios-2.33 dmi-2.33 vsyscall64 vsyscall32 
    configuration: boot=oem-specific chassis=notebook uuid=434E4636-3432-344A-3530-001636A0397B




                  id:core
          description: Motherboard        product: 30B7        vendor: Quanta        physical id: 0
        version: 65.20        serial: None      
                          id:firmware
             description: BIOS           vendor: Hewlett-Packard           physical id: 0
           version: F.19           date: 10/03/2006           size: 99KiB           capacity: 960KiB           capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification          
        
                          id:cpu
             description: CPU           product: AMD Turion(tm) 64 X2 Mobile Technology TL-50           vendor: Hynix Semiconductor (Hyundai Electronics)           physical id: 4
           bus info: cpu@0
           version: AMD Turion(tm) 64 X2 Mobile TL           slot: Socket S1           size: 1600MHz           capacity: 1600MHz           width: 64 bits           clock: 200MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq          
                                   id:cache:0
                description: L1 cache              physical id: 5
              slot: L1 Cache              size: 64KiB              capacity: 64KiB              capabilities: asynchronous internal write-back             
           
                                   id:cache:1
                description: L2 cache              physical id: 6
              slot: L2 Cache              size: 512KiB              capacity: 512KiB              capabilities: synchronous internal write-through unified             
           
        
                          id:memory:0
             description: System Memory           physical id: c
           slot: System board or motherboard           size: 2GiB           capacity: 2GiB         
                                   id:bank:0
                description: DIMM DDR2 Synchronous 1 MHz (1000.0 ns)              physical id: 0
              slot: DIMM 1              size: 1GiB              width: 64 bits              clock: 1MHz (1000.0ns)            
           
                                   id:bank:1
                description: DIMM DDR2 2 MHz (500.0 ns)              physical id: 1
              slot: DIMM 2              size: 1GiB              width: 64 bits              clock: 2MHz (500.0ns)            
           
        
                          id:memory:1
             description: RAM memory           product: C51 Host Bridge           vendor: nVidia Corporation           physical id: 1
           bus info: pci@0000:00:00.0
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           capabilities: ht bus_master cap_list            configuration: latency=0         
        
                          id:memory:2
             description: RAM memory           product: C51 Memory Controller 0           vendor: nVidia Corporation           physical id: 0.1
           bus info: pci@0000:00:00.1
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           configuration: latency=0         
        
                          id:memory:3
             description: RAM memory           product: C51 Memory Controller 1           vendor: nVidia Corporation           physical id: 0.2
           bus info: pci@0000:00:00.2
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           configuration: latency=0         
        
                          id:memory:4
             description: RAM memory           product: C51 Memory Controller 5           vendor: nVidia Corporation           physical id: 0.3
           bus info: pci@0000:00:00.3
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           configuration: latency=0         
        
                          id:memory:5
             description: RAM memory           product: C51 Memory Controller 4           vendor: nVidia Corporation           physical id: 0.4
           bus info: pci@0000:00:00.4
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           capabilities: bus_master            configuration: latency=0         
        
                          id:memory:6
             description: RAM memory           product: C51 Host Bridge           vendor: nVidia Corporation           physical id: 0.5
           bus info: pci@0000:00:00.5
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           capabilities: bus_master cap_list            configuration: latency=0         
        
                          id:memory:7
             description: RAM memory           product: C51 Memory Controller 3           vendor: nVidia Corporation           physical id: 0.6
           bus info: pci@0000:00:00.6
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           configuration: latency=0         
        
                          id:memory:8
             description: RAM memory           product: C51 Memory Controller 2           vendor: nVidia Corporation           physical id: 0.7
           bus info: pci@0000:00:00.7
           version: a2           width: 32 bits           clock: 66MHz (15.2ns)           configuration: latency=0         
        
                          id:pci:0
             description: PCI bridge           product: C51 PCI Express Bridge           vendor: nVidia Corporation           physical id: 2
           bus info: pci@0000:00:02.0
           version: a1           width: 32 bits           clock: 33MHz           capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list            configuration: driver=pcieport           resources: irq:40 ioport:4000(size=4096) memory:b3000000-b31fffff ioport:d0000000(size=2097152)         
        
                          id:pci:1
             description: PCI bridge           product: C51 PCI Express Bridge           vendor: nVidia Corporation           physical id: 3
           bus info: pci@0000:00:03.0
           version: a1           width: 32 bits           clock: 33MHz           capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list            configuration: driver=pcieport           resources: irq:41 memory:b3200000-b33fffff         
                                   id:network
                description: Network controller              product: BCM4311 802.11b/g WLAN              vendor: Broadcom Corporation              physical id: 0
              bus info: pci@0000:03:00.0
              version: 01              width: 32 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list               configuration: latency=0              resources: memory:b3200000-b3203fff            
           
        
                          id:display
             description: VGA compatible controller           product: C51 [Geforce Go 6150]           vendor: nVidia Corporation           physical id: 5
           bus info: pci@0000:00:05.0
           version: a2           width: 64 bits           clock: 66MHz           capabilities: pm msi vga_controller bus_master cap_list rom            configuration: driver=nouveau latency=0           resources: irq:19 memory:b2000000-b2ffffff memory:c0000000-cfffffff memory:b1000000-b1ffffff memory:80000000-8001ffff

---

### Post by wildmanne39 on 2011-06-13
Hi, this should work for you please read down the page your card is the 4311
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

---

### Post by Mynxenoa on 2011-06-13
Okay, I got it working thanks to you man! Thank you. Now I can finally start learning Ubuntu a little bit better. I had to restart it a few times as well as make sure I had the firmware package installed for 11.04 because the additional drivers weren't working without it. Now I have to configure it to Backtrack 5.

---

### Post by wildmanne39 on 2011-06-14
> **Mynxenoa said:**
> Okay, I got it working thanks to you man! Thank you. Now I can finally start learning Ubuntu a little bit better. I had to restart it a few times as well as make sure I had the firmware package installed for 11.04 because the additional drivers weren't working without it. Now I have to configure it to Backtrack 5.Hi, your welcome would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

