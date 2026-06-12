---
title: "Fan speed and wifi issues after Ubuntu 9.1 install"
date: 2011-01-08
forum: General Help
---

### Post by bigspoon on 2011-01-08
i've been having a number of problems (I assume driver issues) after installing Ubuntu Karmic (kernel 2.6.31-14-generic) on a Sony Vaio F series computer.

I've managed to fix the nvidia problem by reading posts on this forum. But the fan speed and wifi continue to elude me. 

My fan is running at high speeds all the time. And when I shutdown Ubuntu it goes into hibernate but doesn't turn off the laptop and the fan continues to run at high speeds. 

I've installed new Atheros drivers for wifi issues. They seem to be installed correctly. But Ubuntu doesn't recognize any available wifi. Below is the output for lscpi and lshw commands.


```

$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Atheros Communications Inc. Device 002e (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
3f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
3f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
3f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
3f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
3f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
3f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
3f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
3f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
3f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
3f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
3f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
sudo lshw -C network
  *-network               
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ndiswrapper latency=0
       resources: irq:16 memory:e7a00000-e7a0ffff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:b6:4e:b5
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=10.100.20.50 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:35 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff(prefetchable)


```

---

### Post by leifjonny on 2011-01-08
To let Linux control the fans you must disable fan-control in the BIOS and run 'sudo sensors-detect' to find the appropriate module. Just follow the directions. Then run 'sudo pwmconfig' to generate /etc/fancontrol. After that you can edit the /etc/fancontrol file to make the fans behave as you wish.

The other scenario may be that BIOS fan control is now disabled, and thats why the fans are running at full speed. In that case you can either do the above, or don't do the above and enable BIOS fan control.

You have to choose to use software or hardware fan control. If hardware fan control is disabled in the BIOS and you don't have software fan control running, the fans will always run at full speed.

---

### Post by bigspoon on 2011-01-08
thx for the tips leifjonny. I'm new to this. I'll look into that and post my findings when I get a chance.

---

### Post by gordintoronto on 2011-01-08
You are using a very old version of Ubuntu. I suggest 10.10 to solve fan/heat issues.

---

### Post by bigspoon on 2011-01-09
Thanks for the help everyone.

sensors-detect couldn't find sensors on my computer for fan speed.

I installed 10.10 to see if it would correct most of the mistakes. It fixed the wifi issue I was having and also fan issue. But it created a host of other issues I'm dealing with including display issues and the inability to hibernate or suspend gracefully.

Oh well, this seems like a better starting point than I was having in 9.1.

A good summary of the problems I was having on the specific computer is below:
[http://fabiostrozzi.eu/?p=300](http://fabiostrozzi.eu/?p=300)

---

### Post by freesqrt on 2011-07-01
Hi there,

I solved the unusual fan speed problem in vaio by upgrading the graphic card driver!!!!!!
I use a EA27FX vaio laptop with an ATI graphic interface. after installing ubuntu 10.04, the fan speed was very high. but ubuntu itself recommended  to upgrade the graphic interface and did it automatically. 
Now the fan speed is normal.

The interesting point is that before upgrading the driver, temperature was about 53- 57. but after that and slowed down the fans, temp decreased to 43- 48!!!!!

I think the basic driver of ubuntu for graphic card can not manages it sufficiently  so its temperature increases and ACPI should cool down it by increasing the fan speed. but ATI original driver can manages it more effectively.

I hope it be useful for every one has some problem like this.

---

