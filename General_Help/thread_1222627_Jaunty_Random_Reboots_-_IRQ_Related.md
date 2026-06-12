---
title: "Jaunty Random Reboots - IRQ Related?"
date: 2009-07-25
forum: General Help
---

### Post by Greenwell on 2009-07-25
Hi All,
Every now and then, my Jaunty will have a random reboot. This can happen 5 hours after starting to work, 1 hour, 5 minutes or even while the system is still loading.

I've done a lot of research and it seems to be a hardware problem. From my research I have a suspicion that it might have to do with IRQ conflicts, unfortunately I am a total newb and have no idea how to fix this. 

Here is my IRQ information, can anyone tell me if I have a conflict here, and how I can fix it? I do see two or three services mapped to the same IRQ in three cases. 

```

cat /proc/interrupts 

           CPU0       CPU1       
  0:     358094       2841   IO-APIC-edge      timer
  1:        820          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:      12211         72   IO-APIC-fasteoi   acpi
 12:     168267       1608   IO-APIC-edge      i8042
 14:      20691         23   IO-APIC-edge      ata_piix
 15:       5465         21   IO-APIC-edge      ata_piix
 16:      27389        166   IO-APIC-fasteoi   uhci_hcd:usb5, radeon@pci:0000:01:00.0
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 20:         13          0   IO-APIC-fasteoi   ohci1394, yenta, yenta
 22:      38178        313   IO-APIC-fasteoi   HDA Intel
 23:         72          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
2295:      55000        254   PCI-MSI-edge      iwl3945
2296:        250         14   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:      80944     347183   Local timer interrupts
RES:      97055     106432   Rescheduling interrupts
CAL:        113        123   Function call interrupts
TLB:       1411        775   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

 lsusb
Bus 001 Device 003: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

