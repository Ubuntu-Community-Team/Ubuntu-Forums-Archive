---
title: "Serious (and puzzling) problem with Nvidia card..."
date: 2006-04-26
forum: General Help
---

### Post by Naerymdan on 2006-04-26
Hi,

Let's get it out of the way now: I'm kinda new, but not completely stupid :???: 

I have a 'Chaintech VNF4 Zenith Value Edition' motherboard and a 'XFX GeForce 6800 XT PCIe' video card. 

Everything works fine with the 'nv' driver, as it should.

The problems start when I try using the 'nvidia' ones: All i get is a blank/black screen and absolutely no response from the system.

Here are some more info: 

1 - I use Dapper Drake up-to-date.

2 - I tried using the nvidia-glx package, installing the package directly from [www.nvidia.com](www.nvidia.com) and I also went up to recompile the whole kernel with the drivers (actually worked, all except the video card that is...) and I always get the same problem.

3 - No sound from gdm starting, can't ctrl-alt-F1 or ctrl-alt-backspace, nor log in without monitor (the monitor is correctly detected).

4 - I tried about every trick / walkthrough / tip / help on the subject, with no luck.

Here are the log files that were generated durint one attempt to boot normaly with nvidia-glx activated: Xorg.0.log, kern.log, dmesg, udev and i also included in the file 'others.zip' the log debug, evms-engine.log, messages and syslog.

There are some lines, mainly in 'kern.log' that seems wrong:

> 
PCI: Cannot allocate resource region 3 of device 0000:05:00.0
pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
pnp: 00:00: ioport range 0x4400-0x447f has been reserved
pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
pnp: 00:00: ioport range 0x4800-0x487f has been reserved
pnp: 00:00: ioport range 0x4880-0x48ff has been reserved

and

nvidia: module license 'NVIDIA' taints kernel.
**** SET: Misaligned resource pointer: f7e79b02 Type 07 Len 0
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 74

and lastly,

PCI: Setting latency timer of device 0000:00:0b.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[pcie00]
Allocate Port Service[pcie03]
PCI: Setting latency timer of device 0000:00:0c.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[pcie00]
Allocate Port Service[pcie03]
PCI: Setting latency timer of device 0000:00:0d.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[pcie00]
Allocate Port Service[pcie03]
PCI: Setting latency timer of device 0000:00:0e.0 to 64
pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS



Here are the important parts of my Xorg.conf file:

> 
Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
#   Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "Device"
    Identifier    "NVIDIA GPU GeForce 6800 XT"
    Driver        "nvidia"
    BusID        "PCI:5:0:0"
EndSection

Section "Monitor"
    Identifier    "Samsung SyncMaster"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA GPU GeForce 6800 XT"
    Monitor        "Samsung SyncMaster"
    DefaultDepth    24
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


and that's about it... 

Something that also baffles me is Xorg.0.log; it doesn't end in error or nothing, it just seems to... hang?

Thanks.
Vincent.

---

