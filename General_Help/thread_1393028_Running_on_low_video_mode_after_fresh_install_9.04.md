---
title: "Running on low video mode after fresh install 9.04"
date: 2010-01-28
forum: General Help
---

### Post by bacchusmarsh on 2010-01-28
Hey i get this message both when booting from the live usb and once installed (i am asked to chose low graphics mode, or to reconfigure X):

Ubuntu is running in Low graphics mode.
error: update configuration to solve

(EE) intel(0): output LVDS enabled but has no modes
(EE) intel(0): no valid modes
(EE) screen(s) found, but none have usable configuration.

any idea how to reconfigure X for asus M6 to suit 9.04?

---

### Post by bacchusmarsh on 2010-01-28
here's all the info on my laptop

description: 	Notebook
product: 	M6A
vendor: 	ASUSTeK Computer Inc.
version: 	1.0
serial: 	SSN12345678901234567
width: 	32 bits
capabilities: 	smbios-2.3 dmi-2.3 smp-1.4 smp
configuration:	
chassis	=	notebook
cpus	=	1
uuid	=	28CE5D8A-0000-0080-385D-00173101788D
id:	
core
description: 	Motherboard
product: 	M6A
vendor: 	ASUSTeK Computer Inc.
physical id: 	
0
version: 	1.0
serial: 	BSN12345678901234567
id:	
firmware
description: 	BIOS
vendor: 	American Megatrends Inc.
physical id: 	
0
version: 	0207 (10/13/2005)
size: 	64KiB
capacity: 	448KiB
capabilities: 	isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
id:	
cpu
description: 	CPU
product: 	Intel(R) Pentium(R) M processor 2.00GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	6.13.8
slot: 	Socket 478
size: 	798MHz
capacity: 	2GHz
width: 	32 bits
clock: 	133MHz
capabilities: 	boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
id:	
cache:0
description: 	L1 cache
physical id: 	
5
slot: 	L1-Cache
size: 	32KiB
capacity: 	32KiB
capabilities: 	pipeline-burst internal varies data
id:	
cache:1
description: 	L2 cache
physical id: 	
6
slot: 	L2-cache
size: 	2MiB
capacity: 	2MiB
capabilities: 	pipeline-burst internal varies unified
id:	
memory
description: 	System Memory
physical id: 	
1d
slot: 	System board or motherboard
size: 	1GiB
id:	
bank:0
description: 	DIMM SDRAM Synchronous
product: 	PartNum1
vendor: 	Manufacturer1
physical id: 	
0
serial: 	SerNum1
slot: 	DIMM1
size: 	512MiB
width: 	64 bits
id:	
bank:1
description: 	DIMM SDRAM Synchronous
product: 	PartNum2
vendor: 	Manufacturer2
physical id: 	
1
serial: 	SerNum2
slot: 	DIMM2
size: 	512MiB
width: 	64 bits
id:	
pci
description: 	Host bridge
product: 	Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
vendor: 	Intel Corporation
physical id: 	
100
bus info: 	
pci@0000:00:00.0
version: 	04
width: 	32 bits
clock: 	33MHz
configuration:	
driver	=	agpgart-intel
module	=	intel_agp
id:	
pci:0
description: 	PCI bridge
product: 	Mobile 915GM/PM Express PCI Express Root Port
vendor: 	Intel Corporation
physical id: 	
1
bus info: 	
pci@0000:00:01.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm msi pciexpress bus_master cap_list
configuration:	
driver	=	pcieport-driver
id:	
display:0
description: 	VGA compatible controller
product: 	Mobile 915GM/GMS/910GML Express Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0
id:	
display:1
description: 	Display controller
product: 	Mobile 915GM/GMS/910GML Express Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2.1
bus info: 	
pci@0000:00:02.1
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0
id:	
multimedia
description: 	Audio device
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	04
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
module	=	snd_hda_intel
id:	
usb:0
description: 	USB Controller
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
vendor: 	Intel Corporation
physical id: 	
1d
bus info: 	
pci@0000:00:1d.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
module	=	uhci_hcd
id:	
usb:1
description: 	USB Controller
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
vendor: 	Intel Corporation
physical id: 	
1d.1
bus info: 	
pci@0000:00:1d.1
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
module	=	uhci_hcd
id:	
usb:2
description: 	USB Controller
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
vendor: 	Intel Corporation
physical id: 	
1d.2
bus info: 	
pci@0000:00:1d.2
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
module	=	uhci_hcd
id:	
usb:3
description: 	USB Controller
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
vendor: 	Intel Corporation
physical id: 	
1d.3
bus info: 	
pci@0000:00:1d.3
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	bus_master
configuration:	
driver	=	uhci_hcd
latency	=	0
module	=	uhci_hcd
id:	
usb:4
description: 	USB Controller
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
vendor: 	Intel Corporation
physical id: 	
1d.7
bus info: 	
pci@0000:00:1d.7
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	pm debug bus_master cap_list
configuration:	
driver	=	ehci_hcd
latency	=	0
module	=	ehci_hcd
id:	
pci:1
description: 	PCI bridge
product: 	82801 Mobile PCI Bridge
vendor: 	Intel Corporation
physical id: 	
1e
bus info: 	
pci@0000:00:1e.0
version: 	d4
width: 	32 bits
clock: 	33MHz
capabilities: 	pci bus_master cap_list
id:	
network:0
description: 	Ethernet interface
product: 	88E8001 Gigabit Ethernet Controller
vendor: 	Marvell Technology Group Ltd.
physical id: 	
0
bus info: 	
pci@0000:02:00.0
logical name: 	
eth0
version: 	13
serial: 	00:17:31:01:78:8d
capacity: 	1GB/s
width: 	32 bits
clock: 	66MHz
capabilities: 	pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	skge
driverversion	=	1.13
firmware	=	N/A
latency	=	64
link	=	no
maxlatency	=	31
mingnt	=	23
module	=	skge
multicast	=	yes
port	=	twisted pair
id:	
pcmcia
description: 	CardBus bridge
product: 	RL5c476 II
vendor: 	Ricoh Co Ltd
physical id: 	
1
bus info: 	
pci@0000:02:01.0
version: 	b3
width: 	64 bits
clock: 	33MHz
capabilities: 	pcmcia bus_master cap_list
configuration:	
driver	=	yenta_cardbus
latency	=	176
maxlatency	=	5
mingnt	=	128
module	=	yenta_socket
resources:	
iomemory	:	b00603020-b0060301f
id:	
firewire
description: 	FireWire (IEEE 1394)
product: 	R5C552 IEEE 1394 Controller
vendor: 	Ricoh Co Ltd
physical id: 	
1.1
bus info: 	
pci@0000:02:01.1
version: 	08
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	ohci1394
latency	=	64
maxlatency	=	4
mingnt	=	2
module	=	ohci1394
id:	
system:0
description: 	SD Host controller
product: 	R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
vendor: 	Ricoh Co Ltd
physical id: 	
1.2
bus info: 	
pci@0000:02:01.2
version: 	17
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	sdhci-pci
latency	=	64
module	=	sdhci_pci
id:	
system:1
description: 	System peripheral
product: 	R5C592 Memory Stick Bus Host Adapter
vendor: 	Ricoh Co Ltd
physical id: 	
1.3
bus info: 	
pci@0000:02:01.3
version: 	08
width: 	32 bits
clock: 	33MHz
capabilities: 	pm cap_list
configuration:	
latency	=	0
id:	
system:2
description: 	System peripheral
product: 	xD-Picture Card Controller
vendor: 	Ricoh Co Ltd
physical id: 	
1.4
bus info: 	
pci@0000:02:01.4
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pm cap_list
configuration:	
latency	=	0
id:	
network:1
description: 	Wireless interface
product: 	PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:02:02.0
logical name: 	
eth1
version: 	05
serial: 	00:15:00:4c:04:07
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	ipw2200
driverversion	=	1.2.2kmprq
firmware	=	ABG:9.0.2.6 (Mar 22 2005)
ip	=	192.168.0.102
latency	=	64
link	=	yes
maxlatency	=	24
mingnt	=	3
module	=	ipw2200
multicast	=	yes
wireless	=	IEEE 802.11g
id:	
isa
description: 	ISA bridge
product: 	82801FBM (ICH6M) LPC Interface Bridge
vendor: 	Intel Corporation
physical id: 	
1f
bus info: 	
pci@0000:00:1f.0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	isa bus_master
configuration:	
latency	=	0
id:	
ide
description: 	IDE interface
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
vendor: 	Intel Corporation
physical id: 	
1f.1
bus info: 	
pci@0000:00:1f.1
logical name: 	
scsi0
version: 	04
width: 	32 bits
clock: 	33MHz
capabilities: 	ide bus_master emulated
configuration:	
driver	=	ata_piix
latency	=	0
id:	
disk
description: 	ATA Disk
product: 	IC25N040ATCS05-0
vendor: 	Hitachi
physical id: 	
0.0.0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	CS4O
serial: 	CLP429F4JBUN4A
size: 	37GiB (40GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	cccdcccd
id:	
volume:0
description: 	EXT3 volume
vendor: 	Linux
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
logical name: 	
/
version: 	1.0
serial: 	e12fa553-034f-4769-93c6-ae848ca7a537
size: 	35GiB
capacity: 	35GiB
capabilities: 	primary bootable journaled extended_attributes large_files ext3 ext2 initialized
configuration:	
created	=	2010-01-28 16:03:43
filesystem	=	ext3
modified	=	2010-01-29 11:31:56
mount.fstype	=	ext3
mount.options	=	rw,relatime,errors=remount-ro,data=ordered
mounted	=	2010-01-29 09:11:03
state	=	mounted
id:	
volume:1
description: 	Extended partition
physical id: 	
2
bus info: 	
scsi@0:0.0.0,2
logical name: 	
/dev/sda2
size: 	1608MiB
capacity: 	1608MiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume
description: 	Linux swap / Solaris partition
physical id: 	
5
logical name: 	
/dev/sda5
capacity: 	1608MiB
capabilities: 	nofs
id:	
cdrom
description: 	DVD writer
product: 	CD/DVDW TS-L532U
vendor: 	TSSTcorp
physical id: 	
0.1.0
bus info: 	
scsi@0:0.1.0
logical name: 	
/dev/cdrom
logical name: 	
/dev/cdrw
logical name: 	
/dev/dvd
logical name: 	
/dev/dvdrw
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	AU04
capabilities: 	removable audio cd-r cd-rw dvd dvd-r
configuration:	
ansiversion	=	5
status	=	nodisc
id:	
serial
description: 	SMBus
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	04
width: 	32 bits
clock: 	33MHz
configuration:	
latency	=	0
id:	
network
description: 	Ethernet interface
physical id: 	
1
logical name: 	
pan0
serial: 	5e:56:a4:99:f7:02
capabilities: 	ethernet physical
configuration:	
broadcast	=	yes
driver	=	bridge
driverversion	=	2.3
firmware	=	N/A
link	=	yes
multicast	=	yes

---

