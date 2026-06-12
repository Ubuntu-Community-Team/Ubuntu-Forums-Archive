---
title: "USB Mouse and keyboard issues"
date: 2010-04-30
forum: General Help
---

### Post by sunoccard on 2010-04-30
i just did a clean install up to 10.4, but this issue has been occurring long before then. I have a USB Mouse and Keyboard, and for some reason They seem to not want to cooperate. When i get to the login screen everything works fine, but once i log in, well neither work properly anymore. The mouse will move but will only occasionally recognize clicks, and icons will flicker when the mouse hovers over them. The keyboard has the issue of not recognizing all my key strokes, it will only pick up every 5th or 6th stroke.

I do have a work around where i unplug my mouse during boot until after login, but with a dual boot system it's become a large hassle. I've already made sure that legacy support was enabled in my bios.

---

### Post by happyhamster on 2010-05-01
- Could you perhaps show the output of:

lsusb

- And:

dmesg | grep usb

- And:

cat /proc/interrupts

- The first command lists all usb hardware, the second looks in your log for usb related stuff, and the third if there are interrupt-related errors.

---

### Post by sunoccard on 2010-05-01
This data may be a bit flawed because I implemented my workaround in order to get it.


> ian@Mk-I-VER-XII:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 006 Device 002: ID 1532:0109 Razer USA, Ltd Lycosa Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 004 Device 002: ID 050d:0200 Belkin Components 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1058:1003 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> 

ian@Mk-I-VER-XII:~$ dmesg | grep usb
[    0.704645] usbcore: registered new interface driver usbfs
[    0.704645] usbcore: registered new interface driver hub
[    0.704645] usbcore: registered new device driver usb
[    0.892841] usb usb1: configuration #1 chosen from 1 choice
[    0.912839] usb usb2: configuration #1 chosen from 1 choice
[    0.976861] usb usb3: configuration #1 chosen from 1 choice
[    1.044096] usb usb4: configuration #1 chosen from 1 choice
[    1.104085] usb usb5: configuration #1 chosen from 1 choice
[    1.164077] usb usb6: configuration #1 chosen from 1 choice
[    1.224086] usb usb7: configuration #1 chosen from 1 choice
[    1.341275] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.670666] usb 1-2: configuration #1 chosen from 1 choice
[    1.800075] usb 1-3: new high speed USB device using ehci_hcd and address 4
[    1.951920] usb 1-3: configuration #1 chosen from 1 choice
[    1.957505] usbcore: registered new interface driver usb-storage
[    1.957511] usb-storage: device found at 4
[    1.957512] usb-storage: waiting for device to settle before scanning
[    2.610016] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    2.866254] usb 3-1: configuration #1 chosen from 1 choice
[    3.170021] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    3.361657] usb 4-1: configuration #1 chosen from 1 choice
[    3.680020] usb 4-2: new full speed USB device using ohci_hcd and address 3
[    3.872760] usb 4-2: configuration #1 chosen from 1 choice
[    4.200027] usb 6-2: new full speed USB device using ohci_hcd and address 2
[    4.421509] usb 6-2: configuration #1 chosen from 1 choice
[    6.950161] usb-storage: device scan complete
[    7.902378] usbcore: registered new interface driver hiddev
[    7.903414] input: PWC snapshot button as /devices/pci0000:00/0000:00:12.0/usb3/3-1/input/input3
[    7.903490] usbcore: registered new interface driver Philips webcam
[    7.905609] input: Belkin Belkin n52te as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input4
[    7.905677] generic-usb 0003:050D:0200.0001: input,hidraw0: USB HID v1.10 Keyboard [Belkin Belkin n52te] on usb-0000:00:12.1-1/input0
[    7.914562] input: Belkin Belkin n52te as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input5
[    7.914647] generic-usb 0003:050D:0200.0002: input,hidraw1: USB HID v1.10 Mouse [Belkin Belkin n52te] on usb-0000:00:12.1-1/input1
[    7.917139] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    7.917141] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    7.919804] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input6
[    7.919875] generic-usb 0003:1532:0109.0003: input,hidraw2: USB HID v1.10 Keyboard [Razer Razer Lycosa] on usb-0000:00:13.1-2/input0
[    7.926206] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.1/input/input7
[    7.926272] generic-usb 0003:1532:0109.0004: input,hidraw3: USB HID v1.10 Device [Razer Razer Lycosa] on usb-0000:00:13.1-2/input1
[    7.926291] usbcore: registered new interface driver usbhid
[    7.926293] usbhid: v2.6:USB HID core driver
[    8.062586] usb 4-2: reset full speed USB device using ohci_hcd and address 3
[    8.081988] Registered led device: rt2500usb-phy0::radio
[    8.082003] Registered led device: rt2500usb-phy0::quality
[    8.083108] usbcore: registered new interface driver rt2500usb
[    8.282498] lirc_mceusb[3]: SMK eHome Infrared Transceiver on usb4:3
[    8.282593] usbcore: registered new interface driver lirc_mceusb
[    8.676563] usbcore: registered new interface driver snd-usb-audio
[   40.660016] usb 6-3: new low speed USB device using ohci_hcd and address 3
[   40.854284] usb 6-3: configuration #1 chosen from 1 choice
[   40.861365] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.0/input/input9
[   40.861452] generic-usb 0003:045E:00CB.0005: input,hidraw4: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:13.1-3/input0


> ian@Mk-I-VER-XII:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:         27          0          0          2   IO-APIC-edge      timer
  1:          0          0          0          2   IO-APIC-edge      i8042
  4:          0          0          0          2   IO-APIC-edge    
  6:          0         49          0         27   IO-APIC-edge      floppy
  7:          1          0          0          0   IO-APIC-edge      parport0
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          0          4   IO-APIC-edge      i8042
 14:          0          0          0          0   IO-APIC-edge      pata_atiixp
 15:          0          0         14       4529   IO-APIC-edge      pata_atiixp
 16:       7975          0         22       8248   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
 17:          0          0      18483       1345   IO-APIC-fasteoi   ehci_hcd:usb1
 18:          0          0          1      11923   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7, nvidia
 19:          0          0          0          4   IO-APIC-fasteoi   ehci_hcd:usb2
 22:          0       8400          5       3320   IO-APIC-fasteoi   ahci, ohci1394
 27:          0          0          0          0   PCI-MSI-edge      eth0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      23534      15660      10444       6436   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:     147064     112106      87570      57390   Rescheduling interrupts
CAL:       1028       1189       1184        325   Function call interrupts
TLB:       1475       1054       1211        991   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          2          2          2          2   Machine check polls
ERR:          1
MIS:          0

---

### Post by happyhamster on 2010-05-01
- Does the same thing happen with the Belkin n52te disconnected? 

- What you could try in any case is to re-attach mouse and key-board, but choosing different usb-slots than before. You'll need to reboot as well (giving the kernel the chance to completely re-map the hardware).

- If that doesn't work, could you perhaps show the output of:

lspci -v

- and again:

cat /proc/interrupts

(The last one because the output might have changed after re-attaching stuff and rebooting.) Good luck.

---

