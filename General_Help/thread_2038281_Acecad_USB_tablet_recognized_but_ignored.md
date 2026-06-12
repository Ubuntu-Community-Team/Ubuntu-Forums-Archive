---
title: "Acecad USB tablet recognized but ignored"
date: 2012-08-06
forum: General Help
---

### Post by RavanH on 2012-08-06
Hi all, 

Trying to use an older USB tablet and stylus control as mouse pounter device, I find that it does not seem to work anymore. In older Ubuntu versions than the latest two (I'm guessing, it might be three) it used to work out of the box, plug and play...

In the logs I notice **"No input driver specified, ignoring this device."** Yet the evdev driver seems to be loaded just like it used to.

Is there any way to get this device to work as a mouse pointer again?

Thanks for any thoughts or tips :)

**Xorg.0.log**
```

[ 16332.464] (II) config/udev: Adding input device Acecad USB Tablet (/dev/input/mouse2)
[ 16332.464] (II) No input driver specified, ignoring this device.
[ 16332.464] (II) This device may have been added with another device file.
[ 16332.465] (II) config/udev: Adding input device Acecad USB Tablet (/dev/input/event12)
[ 16332.465] (**) Acecad USB Tablet: Applying InputClass "evdev tablet catchall"
[ 16332.465] (II) Using input driver 'evdev' for 'Acecad USB Tablet'
[ 16332.465] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 16332.465] (**) Acecad USB Tablet: always reports core events
[ 16332.465] (**) evdev: Acecad USB Tablet: Device: "/dev/input/event12"
[ 16332.465] (--) evdev: Acecad USB Tablet: Vendor 0x460 Product 0x4
[ 16332.465] (--) evdev: Acecad USB Tablet: Found absolute axes
[ 16332.465] (--) evdev: Acecad USB Tablet: Found x and y absolute axes
[ 16332.465] (--) evdev: Acecad USB Tablet: Found absolute tablet.
[ 16332.465] (II) evdev: Acecad USB Tablet: Configuring as tablet
[ 16332.465] (**) evdev: Acecad USB Tablet: YAxisMapping: buttons 4 and 5
[ 16332.465] (**) evdev: Acecad USB Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 16332.465] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input14/event12"
[ 16332.465] (II) XINPUT: Adding extended input device "Acecad USB Tablet" (type: TABLET, id 13)
[ 16332.465] (II) evdev: Acecad USB Tablet: initialized for absolute axes.
[ 16332.465] (**) Acecad USB Tablet: (accel) keeping acceleration scheme 1
[ 16332.465] (**) Acecad USB Tablet: (accel) acceleration profile 0
[ 16332.465] (**) Acecad USB Tablet: (accel) acceleration factor: 2.000
[ 16332.465] (**) Acecad USB Tablet: (accel) acceleration threshold: 4
.

```

**kern.log**
```

kernel: [16332.244297] usb 6-2: new low-speed USB device number 4 using uhci_hcd
kernel: [16332.416377] input: Acecad USB Tablet as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input14

```

**sys.log**
```

kernel: [16332.244297] usb 6-2: new low-speed USB device number 4 using uhci_hcd
kernel: [16332.416377] input: Acecad USB Tablet as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input14
mtp-probe: checking bus 6, device 4: "/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2"
mtp-probe: bus: 6, device: 4 was not an MTP device

```

The strange thing is that *one time*, in sys.log I saw this reported:
```

kernel: [15643.440832] input: Acecad USB Tablet as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input12
kernel: [15643.441115] usbcore: registered new interface driver usb_acecad
kernel: [15643.441118] acecad: v3.2:USB Acecad Flair tablet driver
kernel: [15643.445013] usbcore: registered new interface driver usbhid

```
Even though it is NOT a Flair tablet...

---

### Post by RavanH on 2012-08-06
Additional info:

```

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 006 Device 003: ID 0460:0004 Ace Cad Enterprise Co., Ltd Tablet (5x3.75)

```

```

~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Acecad USB Tablet                       	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]

```

---

### Post by RavanH on 2012-08-06
Boy, do I feel stupid :blush: ... Put the battery in the stylus upside down! Reversed it and it does work now :)

Sorry to bother you all. 

To the mods: this thread can be deleted after you've finnished laughing ;)

---

