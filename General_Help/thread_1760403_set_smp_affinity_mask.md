---
title: "set smp_affinity mask"
date: 2011-05-16
forum: General Help
---

### Post by anoll on 2011-05-16
Hi all,

I am trying to change the default affinity mask that is given in:
/proc/irq/xx/smp_affinity

My search on the web revealed that simply changing the content of the file should make this possible
E.g.: echo "0x" > /proc/irq/1/smp_affinity

That works well for some interrupts, but not for all. For example, if I try interrupt 40 on my system I get the following error message

echo "f0" > /proc/irq/40/smp_affinity
bash: echo: write error: Input/output error

Trying to open /proc/irq/40/smp_affinity results in the following error:
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)
Fatal error (6)Aborted

My question is, if changing the mask is possible for all irq? Or, can't I change due to the bug in glibc?
If it's only the bug, how can I circumvent it?

Here are some system details. 
Linux version 2.6.39-0-generic (buildd@platinum) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #5~20110427-Ubuntu SMP Wed Apr 27 17:41:08 UTC 2011
          CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
  0:         44          0          0     414118          0          0          0          0   IO-APIC-edge      timer
  1:          0          0          0         33          0          0          0          0   IO-APIC-edge      i8042
  8:          0          0          0          1          0          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0        628          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          0       3979          0          0          0          0   IO-APIC-edge      i8042
 16:          0          0          0          0          0          0     161949          0   IO-APIC-fasteoi   mmc0, hda_intel, nvidia
 17:         36          0          0          0          0          0          0          0   IO-APIC-fasteoi 
 19:          0         61          0          0          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, mmc1
 23:          0          0          0          0          0          0          0        224   IO-APIC-fasteoi   ehci_hcd:usb1
 40:     310232          0          0          0          0          0          0          0  HPET_MSI-edge      hpet2
 41:          0     270283          0          0          0          0          0          0  HPET_MSI-edge      hpet3
 42:          0          0     249423          0          0          0          0          0  HPET_MSI-edge      hpet4
 43:          0          0          0     249378          0          0          0          0  HPET_MSI-edge      hpet5
 44:          0          0          0          0     248369          0          0          0  HPET_MSI-edge      hpet6
 45:          0          0      27206          0          0          0          0          0   PCI-MSI-edge      ahci
 46:          0          0          0          0      50257          0          0          0   PCI-MSI-edge      eth0
 47:          0          0          0         39          0          0          0          0   PCI-MSI-edge      firewire_ohci
 48:          0          0          0      70417          0          0          0          0   PCI-MSI-edge      xhci_hcd
 49:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 50:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 51:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 52:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 53:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 54:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 55:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 56:          0          0          0          0          0      13420          0          0   PCI-MSI-edge      iwlagn
 57:          0          0          0          0          0        151          0          0   PCI-MSI-edge      hda_intel


Many thanks for your help!

Cheers,
Albert

---

