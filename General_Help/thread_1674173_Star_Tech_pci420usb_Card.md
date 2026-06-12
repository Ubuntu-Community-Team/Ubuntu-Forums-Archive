---
title: "Star Tech pci420usb Card"
date: 2011-01-23
forum: General Help
---

### Post by MiCK.ca on 2011-01-23
I recently installed a startech PCI usb expansion card...All went well and all external devices connected show up without a hitch. However a day ago The card/devices just STOPPED. 

I rebooted and no avail. Rebooted a second time got a IRQ 19 failure error. Then on a third try It showed up and worked fine... This has happened twice. 

Here's my IRQ print after running cat /proc/interrupts


           CPU0       CPU1       
  0:        132          3   IO-APIC-edge      timer
  1:          0        146   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 14:         58       6012   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 17:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 18:        593       6383   IO-APIC-fasteoi   uhci_hcd:usb5, ICE1712
 19:       3407        721   IO-APIC-fasteoi   ehci_hcd:usb2, ohci1394
 20:          2      11714   IO-APIC-fasteoi   sata_nv
 21:          0          0   IO-APIC-fasteoi   sata_nv
 22:          0          2   IO-APIC-fasteoi   ohci_hcd:usb3, nouveau
 23:      22543       6474   IO-APIC-fasteoi   ehci_hcd:usb1
 26:       3577        109   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     409155     404086   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      63526      64439   Rescheduling interrupts
CAL:         86        174   Function call interrupts
TLB:        355        491   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          2          2   Machine check polls
ERR:          1
MIS:          0

after a lspci I get the following

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:0a.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel

I am assuming that the second to the last entry is the pci usb card. Is there a way to home in more deriectly to find and troubleshot the problem and see if its module or IRQ?

thanks

---

### Post by MiCK.ca on 2011-01-23
Update:

I went into the bios and checked some things. One: my "Primary Video Adapter" was set for "PCI" and not onboard as it is...(that should have freed up a IRQ) Two: PS/2 mouse was set to auto. I changed this to disable as my mouse is in a USB port and the BIOS indicated that this freed up IRQ 12. 

If there was a IRQ conflict then perhaps this may have fixed it...time will time till the next STOPPage.

---

