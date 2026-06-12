---
title: "Need help - crash in kernel during boot (but system boots)"
date: 2010-04-27
forum: General Help
---

### Post by foobar66 on 2010-04-27
I have a custom compiled kernel which seems to work OK.
However, during boot, I get:

Apr 27 21:16:14 poni kernel: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:21:70:90:2d:6c
Apr 27 21:16:14 poni kernel: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
Apr 27 21:16:14 poni kernel: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr 27 21:16:14 poni kernel: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr 27 21:16:14 poni kernel: irq 11: nobody cared (try booting with the "irqpoll" option)
Apr 27 21:16:14 poni kernel: Pid: 218, comm: modprobe Not tainted 2.6.32.11+drm33.2-custom #5
Apr 27 21:16:14 poni kernel: Call Trace:
Apr 27 21:16:14 poni kernel: <IRQ>  [<ffffffff81061a98>] __report_bad_irq+0x38/0x87
Apr 27 21:16:14 poni kernel: [<ffffffff81061bfa>] note_interrupt+0x113/0x179
Apr 27 21:16:14 poni kernel: [<ffffffff81062360>] handle_level_irq+0x88/0xcf
Apr 27 21:16:14 poni kernel: [<ffffffff8100d8a6>] handle_irq+0x1f/0x27
Apr 27 21:16:14 poni kernel: [<ffffffff8100d113>] do_IRQ+0x57/0xb7
Apr 27 21:16:14 poni kernel: [<ffffffff8100b853>] ret_from_intr+0x0/0xa
Apr 27 21:16:14 poni kernel: [<ffffffff810390f7>] ? __do_softirq+0x61/0x196
Apr 27 21:16:14 poni kernel: [<ffffffff8100bf9c>] ? call_softirq+0x1c/0x28
Apr 27 21:16:14 poni kernel: [<ffffffff8100d84f>] ? do_softirq+0x33/0x6b
Apr 27 21:16:14 poni kernel: [<ffffffff81038fc8>] ? irq_exit+0x36/0x78
Apr 27 21:16:14 poni kernel: [<ffffffff8100d15c>] ? do_IRQ+0xa0/0xb7
Apr 27 21:16:14 poni kernel: [<ffffffff8100b853>] ? ret_from_intr+0x0/0xa
Apr 27 21:16:14 poni kernel: <EOI>  [<ffffffff812ff964>] ? _spin_unlock_irqrestore+0x8/0xa
Apr 27 21:16:14 poni kernel: [<ffffffff8120b46d>] ? ata_eh_freeze_port+0x38/0x3d
Apr 27 21:16:14 poni kernel: [<ffffffff81202796>] ? ata_host_start+0x113/0x16f
Apr 27 21:16:14 poni kernel: [<ffffffffa002d720>] ? ahci_interrupt+0x0/0x48a [ahci]
Apr 27 21:16:14 poni kernel: [<ffffffff81202fea>] ? ata_host_activate+0x25/0xd7
Apr 27 21:16:14 poni kernel: [<ffffffffa002d700>] ? ahci_init_one+0xfbc/0xfdc [ahci]
Apr 27 21:16:14 poni kernel: [<ffffffff81171f23>] ? kobject_get+0x1a/0x21
Apr 27 21:16:14 poni kernel: [<ffffffff8118495f>] ? local_pci_probe+0x12/0x16
Apr 27 21:16:14 poni kernel: [<ffffffff8118511f>] ? pci_device_probe+0x5d/0x8c
Apr 27 21:16:14 poni kernel: [<ffffffff811e6dec>] ? driver_sysfs_add+0x47/0x6c
Apr 27 21:16:14 poni kernel: [<ffffffff811e6f24>] ? driver_probe_device+0x9a/0x11f
Apr 27 21:16:14 poni kernel: [<ffffffff811e7001>] ? __driver_attach+0x58/0x7c
Apr 27 21:16:14 poni kernel: [<ffffffff811e6fa9>] ? __driver_attach+0x0/0x7c
Apr 27 21:16:14 poni kernel: [<ffffffff811e65ac>] ? bus_for_each_dev+0x4e/0x83
Apr 27 21:16:14 poni kernel: [<ffffffff811e6da3>] ? driver_attach+0x19/0x1b
Apr 27 21:16:14 poni kernel: [<ffffffff811e6a25>] ? bus_add_driver+0xb1/0x200
Apr 27 21:16:14 poni kernel: [<ffffffff811e72c5>] ? driver_register+0x99/0x10a
Apr 27 21:16:14 poni kernel: [<ffffffff81185358>] ? __pci_register_driver+0x53/0xc3
Apr 27 21:16:14 poni kernel: [<ffffffffa0035000>] ? ahci_init+0x0/0x20 [ahci]
Apr 27 21:16:14 poni kernel: [<ffffffffa003501e>] ? ahci_init+0x1e/0x20 [ahci]
Apr 27 21:16:14 poni kernel: [<ffffffff8100905f>] ? do_one_initcall+0x59/0x149
Apr 27 21:16:14 poni kernel: [<ffffffff8105d663>] ? sys_init_module+0xd1/0x232
Apr 27 21:16:14 poni kernel: [<ffffffff8100afab>] ? system_call_fastpath+0x16/0x1b
Apr 27 21:16:14 poni kernel: handlers:
Apr 27 21:16:14 poni kernel: [<ffffffff81216caa>] (iwl_isr_ict+0x0/0x1cd)
Apr 27 21:16:14 poni kernel: [<ffffffff8123355e>] (usb_hcd_irq+0x0/0x60)
Apr 27 21:16:14 poni kernel: last message repeated 3 times
Apr 27 21:16:14 poni kernel: Disabling IRQ #11
Apr 27 21:16:14 poni kernel: scsi0 : ahci
Apr 27 21:16:14 poni kernel: scsi1 : ahci
Apr 27 21:16:14 poni kernel: scsi2 : ahci
Apr 27 21:16:14 poni kernel: scsi3 : ahci
Apr 27 21:16:14 poni kernel: scsi4 : ahci
Apr 27 21:16:14 poni kernel: scsi5 : ahci
Apr 27 21:16:14 poni kernel: ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 11

System continues to boot OK and everything seems to work fine as I expect. I am not sure what the above causes. It looks related to USB, but I am not sure. lsusb gives:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c526 Logitech, Inc. MX Revolution Cordless Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Any suggestion of what might be wrong?

---

### Post by P4man on 2010-04-27
Problem with IRQ 11. I think its just not assigned, so not a real problem. Can you post output of 

cat /proc/interrupts

You may also try what is suggested in your ouput, ie, boot with irqpoll parameter (or try updating your bios).

---

### Post by foobar66 on 2010-04-27
Thanks for your comment. That's already further than I got ...
Output of /proc/interrupts is:

  0:      52560          0    XT-PIC-XT        timer
  1:        205          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  5:       2038          0    XT-PIC-XT        uhci_hcd:usb3, radeon
  6:        614          0    XT-PIC-XT        HDA Intel
  7:          2          0    XT-PIC-XT        ehci_hcd:usb2, uhci_hcd:usb6
  9:        988          0    XT-PIC-XT        acpi
 10:          0          0    XT-PIC-XT        uhci_hcd:usb8
 11:      26641          0    XT-PIC-XT        iwlagn, ehci_hcd:usb1, uhci_hcd:usb4, uhci_hcd:usb5, uhci_hcd:usb7, ahci, HDA Intel, eth0
 12:        106          0    XT-PIC-XT        i8042
NMI:          0          0   Non-maskable interrupts
LOC:      11753      28744   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:       8944        784   Rescheduling interrupts
CAL:         45         83   Function call interrupts
TLB:       1066        933   TLB shootdowns
ERR:          0
MIS:          0

Interrupt 11 is used by wireless device and usb and eth0?
Is that normal condition?

The strange thing is: if I boot with "quiet" option, I do not see the problem in the kern.log. If I boot without "quiet" it occurs in the log?

---

### Post by P4man on 2010-04-27
I suppose it is normal. Im no expert here heh, on my desktop it looks a lot more sane, but here I do have acpi and apic working properly. On my old laptop it looks even worse than for you:

cat /proc/interrupts 
           CPU0       
  0:     263314    XT-PIC-XT        timer
  1:         48    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:      10123    XT-PIC-XT        eth1
  4:          2    XT-PIC-XT      
  5:        118    XT-PIC-XT        Intel 82801DB-ICH4
  7:          1    XT-PIC-XT        parport0
  8:          0    XT-PIC-XT        rtc0
  9:          3    XT-PIC-XT        acpi
 10:          2    XT-PIC-XT      
 **11:     144650    XT-PIC-XT        ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, radeon, yenta, yenta, eth0**
 12:       8520    XT-PIC-XT        i8042
 14:       7449    XT-PIC-XT        ata_piix
 15:          0    XT-PIC-XT        ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         11   Machine check polls
ERR:          0
MIS:          0

usb, vga, ethernet, pc card (wifi).. heh.

---

