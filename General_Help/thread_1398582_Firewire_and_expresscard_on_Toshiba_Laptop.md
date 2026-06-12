---
title: "Firewire and expresscard on Toshiba Laptop"
date: 2010-02-04
forum: General Help
---

### Post by aib007 on 2010-02-04
Hi, I would like to ask for a little help. I have a TC desktop konnect 6 firewire interface that is connected through an expresscard to my Toshiba Satellite. I am have tried all the possible commands but unfortunately ubuntu studio doesn't see it. I am quite new and unexperienced so this turned out into a really painful and traumatizing experience. The expresscard however is detected, but I cannot figure out how to make ubuntu see my soundcard. Here is what I copied from the system report: 

XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
Property    Value
info.subsystem    pci
info.product    XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
info.udi    /org/freedesktop/Hal/devices/pci_104c_8231
info.vendor    Texas Instruments
info.parent    /org/freedesktop/Hal/devices/pci_8086_2843
pci.product    XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge
pci.vendor_id    4172
pci.vendor    Texas Instruments
pci.product_id    33329
pci.device_protocol    0
pci.device_subclass    4
pci.subsys_vendor_id    0
pci.device_class    6
pci.subsys_product_id    0
pci.linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0
linux.hotplug_type    2
linux.subsystem    pci
linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0
XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
Property    Value
info.subsystem    pci
info.product    XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
info.vendor    Texas Instruments
info.parent    /org/freedesktop/Hal/devices/pci_104c_8231
info.linux.driver    ohci1394
info.udi    /org/freedesktop/Hal/devices/pci_104c_8235
pci.product    XIO2200(A) IEEE-1394a-2000 Controller (PHY/Link)
pci.vendor_id    4172
pci.vendor    Texas Instruments
pci.product_id    33333
pci.device_protocol    16
pci.device_subclass    0
pci.subsys_vendor_id    22136
pci.device_class    12
pci.subsys_product_id    4660
pci.linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/0000:04:00.0
linux.hotplug_type    2
linux.subsystem    pci
linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/0000:04:00.0 
 

Please if anybody knows what I could do, give me some advice. 
I already tried to use the sudo modprobe pciehp command, and it says module not detected, also CONFIG_HOTPLUG_PCI_PCIE=y means the module should be in the kernel. I would realy like to focus on making some music, so please give any sugestions. Thank you.

---

