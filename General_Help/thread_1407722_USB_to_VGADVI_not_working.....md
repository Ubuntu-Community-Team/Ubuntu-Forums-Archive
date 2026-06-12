---
title: "USB to VGA/DVI not working...."
date: 2010-02-15
forum: General Help
---

### Post by maghajan on 2010-02-15
Hi everyone, 

I just bought a Tritton See2 Xtreme USB to DVI external video adapter and was hoping to use it as a primary display for my computer. The reason I want to use it as a primary display is because my current computer has a very weak video card and I cannot add any internal video cards; so external is my only option. I tried doing many google searches and edited my xorg.conf file a variety of ways, but still have no luck.

Here my output from "lsusb" command:
[FONT="Courier New"]
Bus 001 Device 008: ID 0711:0950 Magic Control Technology Corp. 
Bus 001 Device 007: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 006: ID 413c:0000 Dell Computer Corp. 
Bus 001 Device 005: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 002: ID 413c:a001 Dell Computer Corp. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/FONT]

Here is the output from my Xorg.0.log file after plugging the device in:

[FONT="Courier New"]
II) config/hal: removing device Dell Dell USB Optical Mouse
(II) Dell Dell USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Dell Dell USB Optical Mouse
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event3"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Dell USB Optical Mouse: (accel) set acceleration profile 0
(II) Dell Dell USB Optical Mouse: initialized for relative axes.[/FONT]

The computer is a Dell Poweredge 1950, hence the weak built-on video card, but 8GB RAM and 8-core processor. Can't be re-purposed as a server so I am re-purposing it as a desktop instead and therefore need more video.  Any help is greatly appreciated!!!

---

