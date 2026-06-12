---
title: "Touch screen *was* working - now it's not?"
date: 2011-04-06
forum: General Help
---

### Post by BrixtonBiker on 2011-04-06
I have a Zalman HTPC case with a built-in touch screen.
When I first installed the OS (Ubuntu 10.10, 64bit), the touchscreen worked perfectly out of the box, albeit with a reversed x-axis.
It's no longer recognised, and I have no idea why.  (Booting into Windows it still works fine, so I know the device is not suffering a hardware error).
Can anyone advise me on how to troubleshoot this and re-enable support?

Previously, I made a note of this info...
```

usb 1-1-4

I: Bus=0003 Vendor=0f92 Product=0001 Version=0115
N: Name="JASTEC USB Touch Screen Controller"
P: Phys=usb-0000:00:1a.0-1.4/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input2
U: Uniq=
H: Handlers=mouse0 event2
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3
```

Sadly, and stupidly, I didn't make a note of how I found that. (Sorry, bit of a n00b).

Greping dmesg for usb, I can see errors on usb device 0-1.4 (see below)

Any ideas would be gratefully received.
Additionally, if anyone knows how to reverse the x-axis, as uTouch didn't seem to pick up the screen. 
Cheers
D.

```

[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=d508d296-9ae8-4d65-b984-098dc3492b15 ro quiet splash usbhi$
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=d508d296-9ae8-4d65-b984-098dc3492b15 ro quiet splas$
[    0.902644] usbcore: registered new interface driver usbfs
[    0.902650] usbcore: registered new interface driver hub
[    0.902673] usbcore: registered new device driver usb
[    1.324853] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.593642] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.843278] usb 1-1.1: new high speed USB device using ehci_hcd and address 3
[    1.971963] scsi4 : usb-storage 1-1.1:1.0
[    1.972054] usbcore: registered new interface driver usb-storage
[    2.042814] usb 1-1.3: new full speed USB device using ehci_hcd and address 4
[    2.252312] usb 1-1.4: new low speed USB device using ehci_hcd and address 5
[    2.332171] usb 1-1.4: device descriptor read/64, error -32
[    2.521729] usb 1-1.4: device descriptor read/64, error -32
[    2.711359] usb 1-1.4: new low speed USB device using ehci_hcd and address 6
[    2.791112] usb 1-1.4: device descriptor read/64, error -32
[    2.980626] usb 1-1.4: device descriptor read/64, error -32
[    3.170236] usb 1-1.4: new low speed USB device using ehci_hcd and address 7
[    3.589184] usb 1-1.4: device not accepting address 7, error -32
[    3.669132] usb 1-1.4: new low speed USB device using ehci_hcd and address 8
[    4.088091] usb 1-1.4: device not accepting address 8, error -32
[    4.168148] usb 1-1.6: new low speed USB device using ehci_hcd and address 9
[   14.839441] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   14.953089] usbcore: registered new interface driver usbserial
[   14.953348] usbcore: registered new interface driver usbserial_generic
[   14.953350] usbserial: USB Serial Driver core
[   14.962716] usb 1-1.3: Detected FT232RL
[   14.962719] usb 1-1.3: Number of endpoints 2
[   14.962721] usb 1-1.3: Endpoint 1 MaxPacketSize 64
[   14.962723] usb 1-1.3: Endpoint 2 MaxPacketSize 64
[   14.962724] usb 1-1.3: Setting MaxPacketSize 64
[   14.963032] usb 1-1.3: FTDI USB Serial Device converter now attached to ttyUSB0
[   14.963111] usbcore: registered new interface driver ftdi_sio
[   14.963032] usb 1-1.3: FTDI USB Serial Device converter now attached to ttyUSB0
[   14.963111] usbcore: registered new interface driver ftdi_sio
[   14.990331] usbcore: registered new interface driver hiddev
[   14.990680] usbcore: registered new interface driver usbhid
[   14.990683] usbhid: USB HID core driver
[   15.013213] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input2
[   15.013301] logitech 0003:046D:C50C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.6/input0
[   15.018478] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input3
[   15.018603] logitech 0003:046D:C50C.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.6/inp$
[   22.139459] mceusb: disagrees about version of symbol __ir_input_register
[   22.139464] mceusb: Unknown symbol __ir_input_register (err -22)


```

---

### Post by sloggerkhan on 2012-10-21
I'm having a similar issue, but I haven't been able to figure anything out, either.

---

### Post by Pichy28 on 2012-10-23
There can be lots of things happening. I have a similar issue, my touchscreen is creating a mouse event. just like yours. The difference is yours has the ABS set to 3 and mine has it set to f which I suppose is stands for false. I would advice to have a look at xorg.conf and see if you can configure your device there.  You could start by creating a rule to make a new symlink to identify your device and then calibrate it at xorg.conf. If you could also give me any suggetion, I would apreciate it because I'm having a similar issue. Regards

---

