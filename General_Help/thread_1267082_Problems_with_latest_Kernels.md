---
title: "Problems with latest Kernels"
date: 2009-09-15
forum: General Help
---

### Post by AKangB on 2009-09-15
Since Ubuntu 7..4 I Have problems with the kernel (or I think so)

In 2.6.17-14-generic Kernel, during the bootsplash (where it cannot be seen), If I push CONTROL+ALT+F1, every 2 minutes it refresh showing "Unexpected IRQ trap vector at 93"

Thats the last kernel that works, in latest kernel when booting, it freeze when "plase wait..." is shown.
If I run tha latest Kernel in fail safe mode, I can see: "[TIMESTAM] Input: AT Translate Set 2 Keyboard as /devices/platform/serio0/input/input3"
when it's freezed, the caps & desp LED on Keyboard start blinking...

Somebody on IRC ask me what have I on IRQ 97 that is spaming it, that's de answer:
```
root@Airis-P4:/home/default# cat /proc/interrupts
           CPU0       CPU1       
  0:        120         0   IO-APIC-edge      timer
  1:       7361        0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          0          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:      69986      0   IO-APIC-edge      i8042
 14:      25064      0   IO-APIC-edge      pata_via
 15:      26109      0   IO-APIC-edge      pata_via
 20:      62164      0   IO-APIC-fasteoi   sata_via
 21:      71788      0   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5
 22:       1778       0   IO-APIC-fasteoi   VIA8237
 23:    1301349     0   IO-APIC-fasteoi   eth0
 24:     822368     0   IO-APIC-fasteoi   nvidia
147:       5515      0      none-<NULL>  
223:          0        0   PCI-MSI-edge      aerdrv
NMI:          0        0   Non-maskable interrupts
LOC:    1552031   1712570   Local timer interrupts
RES:      19053     21321   Rescheduling interrupts
CAL:       1002      1535   function call interrupts
TLB:       4523       4742   TLB shootdowns
SPU:          0        0   Spurious interrupts
ERR:          0
MIS:          0

```NOTHING!

any suggest?

For information, it's a hand-made computer with an Intel Pentium 4 and an AsusRocl mainboard

---

### Post by ukblacknight on 2009-09-15
Do other operating systems, such a other linux distributions or Windows, produce similar results?

---

### Post by AKangB on 2009-09-15
> **ukblacknight said:**
> Do other operating systems, such a other linux distributions or Windows, produce similar results?
Windows runs well, only breaks on any linux with the latest kernel... i'm using Gutsy Kernel now :)

---

