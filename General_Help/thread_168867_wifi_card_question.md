---
title: "wifi card question"
date: 2006-05-01
forum: General Help
---

### Post by kristof_v on 2006-05-01
hi,

i have the firmware for my wifi card.
and ndiwrapper is set up with the right drivers.
it works, but when i start my system the led's don't start blinking.
i did exactly he same as on my debian system ans on the debian system the led's start blinking when i boot the system.

the led's start blinking when i do dhclient however.
this is dmesg output after dhclient:

[PHP][4294814.166000] eth1: resetting device...
[4294814.166000] eth1: uploading firmware...
[4294814.406000] eth1: firmware version: 1.0.4.3
[4294814.406000] eth1: firmware upload complete
[4294814.641000] eth1: interface reset complete
[4294814.690000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294814.799000] NET: Registered protocol family 17
[4294825.062000] eth0: no IPv6 routers present
[4294825.093000] eth1: no IPv6 routers present
[/PHP]

this is dmesg when i unplug the card:
[PHP][4295263.852000] eth1: hot unplug detected
[4295263.852000] eth1: removing device
[4295263.852000] eth1: islpci_close ()
[4295263.913000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[/PHP]

then when i plug it in again the led's don'y blink anymore
this is dmesg ouput:
[PHP][4295263.852000] eth1: hot unplug detected
[4295263.852000] eth1: removing device
[4295263.852000] eth1: islpci_close ()
[4295263.913000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[/PHP]

what do i have to do to make the led's blink when i insert the card or when the system boots?


grtz

---

