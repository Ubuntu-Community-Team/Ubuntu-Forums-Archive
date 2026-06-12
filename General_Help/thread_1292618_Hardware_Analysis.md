---
title: "Hardware Analysis"
date: 2009-10-16
forum: General Help
---

### Post by xtremo on 2009-10-16
Can anybody recommend an utility for hardware analysis on Jaunty.....along the lines of Sisoft Sandra, Everest etc?

It's looking like I may have to flash the bios so I want to be 100% certain of the specs.

Many thanks!

---

### Post by Vermind on 2009-10-16
Open a terminal and type:
```
sudo lshw > hardware.txt
gedit hardware.txt
```
Alternative: paste this text into the terminal and press enter.
Note: This file will contain information on all of your hardware. That is a lot of info. BIOS and MB info should be in the beginning. Example:
```
periptero
    description: Notebook
    product: HP Pavilion dv6500 Notebook PC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF7321MZT
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4637-3332-314D-5A54-001B2480C9C2
  *-core
       description: Motherboard
       product: 30D2
       vendor: Quanta
       physical id: 0
       version: 79.13
       serial: None
       slot: Bank 2,3
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.09 (06/11/2007)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
```
Hope this helps.

---

### Post by mocoloco on 2009-10-16
hardinfo.  Sudo apt-get install hardinfo.

---

### Post by xtremo on 2009-10-16
Cheers guys!

---

### Post by justleen on 2009-10-16
hwmgr is usefull too

---

