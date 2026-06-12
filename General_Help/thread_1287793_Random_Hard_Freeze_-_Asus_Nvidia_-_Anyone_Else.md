---
title: "Random Hard Freeze - Asus Nvidia - Anyone Else?"
date: 2009-10-10
forum: General Help
---

### Post by grafted_scion on 2009-10-10
I have been trying to fix this random freeze thing for ages now it seems.
Reading a lot of different threads trying to find a solution to the problem.
Whenever hardware is mentioned its Asus & Nvidia, thats what i have.
 P5LD2-FM & Geforce6500

```
cat /proc/interrupts
```Shows:
 ```
          CPU0       CPU1       
  0:        117          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  8:          0          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:     640096          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:    7072467          0   IO-APIC-fasteoi   nvidia
 17:     269192          0   IO-APIC-fasteoi   uhci_hcd:usb3
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:   10613273          0   IO-APIC-fasteoi   uhci_hcd:usb5, HDA Intel
 20:    1590669          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 21:          3          0   IO-APIC-fasteoi   ohci1394
2299:    9175895          0   PCI-MSI-edge      eth0
2300:     948760          0   PCI-MSI-edge      ahci
NMI:          0          0   Non-maskable interrupts
LOC:   31739178   33755583   Local timer interrupts
RES:    1007103    1034741   Rescheduling interrupts
CAL:       2316       5392   Function call interrupts
TLB:     293652     382780   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```From the various logs in /var/log only some pulseaudio errors stand out.

pulseaudio[3386]: asyncq.c: q overrun, queuing locally.
pulseaudio[3386]: protocol-native.c: Failed to push data into queue.
pulseaudio[3315]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
pulseaudio[3315]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense."

Reinstalling pulseaudio seemed to end the errors until next freeze after hard reboot they where back.

Tried nvidia drivers from 173.xx.x to 190.xx.x now i have 185.xx.x.
Tried updating the softwares i use most to latest version, Mozilla, VLC and so on.

My problem persists now i get a hard freeze every 24-48hours before it was many times a day.

Anyone else share my problem with Nvidia & Asus?

---

