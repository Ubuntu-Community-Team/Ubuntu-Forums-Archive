---
title: "WLAN problems"
date: 2009-12-09
forum: General Help
---

### Post by Dro1d on 2009-12-09
Hi, I just installed Ubuntu 9.10 i386 on my desktop and it doesn't recognize my WiFi adapter (and it's my only existing connection to the internet) ...

I have D-Link DWL 520+ on my PC and when i scan the devices it says

knoxx@knoxx-desktop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.


Someone asked me for my system specs, here they are:

Motherboard ASUS A8N5X Version 1.XX Serial Number 123456789000
CPU AMD Athlon(tm) 64 Processor 3200+ Socket 939
Memory MOSEL 2x 512MB DDR (PC3200) 200MHz
Graphics Adapter NVIDIA GeForce 7600GS 256MB PCI-E
Network Adapter 1 NVIDIA nForce Networking Controller
Network Adapter 2 D-Link AirPlus DWL-520+ Wireless PCI Adapter

So, after reading lots of threads and talking to a few people I made it happen over ndiswrapper with the Windows XP 32bit driver, but then i decided to switch to the x64 because i have the AMD ATH 3200+ x64 processor and when i try to do it with ndiswrapper it says something like this : Error this distro is 64bit and the driver is 32bit : bad magic !

so , after downloading acx-20080210.tar.bz2 and acx_karmic.patch over my Windows box and doing the following :



mkdir acx
cd acx
tar xjvf acx-20080210.tar.bz2
patch -p0 < acx_karmic.patch
cd acx-20080210/
make -C /lib/modules/`uname -r`/build M=`pwd`
sudo insmod acx.ko

Nothing was found

sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

so i read somewhere that i need to do

sudo dmesg -c
sudo insmod acx.ko
dmesg
iwconfig

I do it, but when i get to the dmesg part i get this :
knoxx@blunt:~$ dmesg
acx: this driver is still EXPERIMENTAL
acx: reading README file and/or Craig's HOWTO is recommended, visit [http://acx100.sf.net](http://acx100.sf.net) in case of further questions/discussion
acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
acx: running on a little-endian CPU
acx: PCI/VLYNQ module v0.3.37 initialized, waiting for cards to probe...
ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
   alloc irq_desc for 16 on node 0
   alloc kstat_irqs on node 0
 acx_pci 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
 acx: found ACX100-based wireless network card at 0000:05:06.0, irq:16, phymem1:0xD3010000, phymem2:0xD3000000, mem1:0xffffc9001058a000, mem1_size:4096, mem2:0xffffc900105a0000, mem2_size:65536
 initial debug setting is 0x000A
 using IRQ 16
 acx: need to load firmware for acx100 chipset with radio ID 0d, please provide via firmware hotplug:
 acx: either one file only (<c>ombined firmware image file, radio-specific) or two files (radio-less base image file *plus* separate <r>adio-specific extension file)
 requesting firmware image 'tiacx100c0D'
 acx_pci 0000:05:06.0: firmware: requesting tiacx100c0D
 acx: firmware image 'tiacx100c0D' was not provided. Check your hotplug scripts
 requesting firmware image 'tiacx100'
 acx_pci 0000:05:06.0: firmware: requesting tiacx100
 acx: firmware image 'tiacx100' was not provided. Check your hotplug scripts
 acx: reset_dev() FAILED
 acx_pci 0000:05:06.0: PCI INT A disabled
 acx_pci: probe of 0000:05:06.0 failed with error -5
 USB module v0.3.37 initialized, probing for devices...
 usbcore: registered new interface driver acx_usb
 
 meaning i need to get tiacx100c0D and tiacx100 firmware, witch is strange because when i go to /lib/firmware/acx/default/ the tiacx100 is there but it's not loading or something, any ideas how to fix this ?

---

### Post by bkratz on 2009-12-09
This thread may be of some use

[http://ubuntuforums.org/showthread.php?t=1321303&highlight=ACX+100](http://ubuntuforums.org/showthread.php?t=1321303&highlight=ACX+100)

---

### Post by Dro1d on 2009-12-09
I tried that, read my post -.- It doesn't work for me on x64 because of "missing firmware" wich is actually there

---

