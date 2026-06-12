---
title: "Bluetooth keyboard/mouse in Oneiric keeps cutting out"
date: 2011-12-20
forum: General Help
---

### Post by stumpalump on 2011-12-20
I need some help troubleshooting bluetooth in Oneiric. I saw some old, closed, posts about people having problems with bluetooth in 11.10 but didn't see any solutions, so I decided to post a new thread.

So, this is my first experience with bluetooth in ubuntu as I never needed the range on my keyboard/mouse before now.

Everything actually paired up perfectly. Bluetooth app seems to work fine. I don't actually lose my pairings ever. My paired devices are always listed upon right-clicking the bluetooth icon in tray.

So what's the problem? They will just all of a sudden stop working! Could be after 1 minute. Could be after 1 hour. Could be after 1 second. I have to battery pull on the two peripherals (sometimes a few times) until they connect back up. I don't have to re-pair them. I don't have to re-type pins. They just connect back up until such time that I lose them again.

I notice that *sometimes* when this happens, I will actually lose the bluetooth icon from the tray for a second then it comes back. This sounds to me like maybe bluez may be segfaulting and restarting itself or something. But, like I said I know nothing about BT in linux.

Please if anyone has any experience with BT in linux and can help me with some troubleshooting steps or maybe how I could track down a bug and report it, I would be very grateful.

Thanks for reading.

EDIT: It should also be noted that I don't always lose both peripherals. Sometimes I lose the mouse. Sometimes I lose the keyboard. Sometimes I lose both. Very very strange.

---

### Post by stumpalump on 2011-12-20
An update:

I was following some steps for Natty on [this]("https://help.ubuntu.com/community/BluetoothSetup") page.

When trying the line

```

sudo bluez-test-device trusted xx:xx:xx:xx:xx:xx yes

```

to add a trusted device, I get this

```


Traceback (most recent call last):
  File "/usr/bin/bluez-test-device", line 158, in <module>
    path = adapter.FindDevice(args[1])
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 143, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.bluez.Error.DoesNotExist: Does Not Exist

```

Can anyone help? I'm almost certain this is software issue. Thanks in advance.

Edit: I followed the steps for Natty even though I'm on Oneiric because that page doesn't have anything for Oneiric yet. Frankly, I'm feeling a little left in the dark with Bluetooth on Oneiric. Can't find any Documentation from Canonical, or anything on the net where people have had problems with BT after beta.

---

### Post by stumpalump on 2011-12-22
Here is output of dmesg when the devices stop working.

```


[77504.526650] input: Rocketfish Bluetooth Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input68
[77504.526874] generic-bluetooth 0005:0A5C:0001.003D: input,hidraw2: BLUETOOTH HID v1.29 Mouse [Rocketfish Bluetooth Mouse] on 00:02:76:0C:37:40
[79615.005847] input: Rocketfish Bluetooth Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input69
[79615.006290] generic-bluetooth 0005:0A5C:0001.003E: input,hidraw2: BLUETOOTH HID v1.29 Mouse [Rocketfish Bluetooth Mouse] on 00:02:76:0C:37:40
[89191.878870] input: Rocketfish Bluetooth Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input70
[89191.879088] generic-bluetooth 0005:045E:8502.003F: input,hidraw2: BLUETOOTH HID v1.1c Keyboard [Rocketfish Bluetooth Keyboard] on 00:02:76:0C:37:40
[89202.193299] input: Rocketfish Bluetooth Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:12/input71
[89202.193528] generic-bluetooth 0005:0A5C:0001.0040: input,hidraw3: BLUETOOTH HID v1.29 Mouse [Rocketfish Bluetooth Mouse] on 00:02:76:0C:37:40
[91091.228406] input: Rocketfish Bluetooth Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input72
[91091.228631] generic-bluetooth 0005:045E:8502.0041: input,hidraw2: BLUETOOTH HID v1.1c Keyboard [Rocketfish Bluetooth Keyboard] on 00:02:76:0C:37:40
[91896.608025] hci_cmd_timer: hci0 command tx timeout
[91905.815671] input: Rocketfish Bluetooth Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:13/input73
[91905.815783] generic-bluetooth 0005:045E:8502.0042: input,hidraw2: BLUETOOTH HID v1.1c Keyboard [Rocketfish Bluetooth Keyboard] on 00:02:76:0C:37:40
[92803.632023] hci_cmd_timer: hci0 command tx timeout
[92822.932645] usb 2-3: USB disconnect, device number 18
[92822.932649] usb 2-3.1: USB disconnect, device number 21
[92822.933259] btusb_bulk_complete: hci0 urb ef144e80 failed to resubmit (19)
[92822.933265] btusb_intr_complete: hci0 urb ef144500 failed to resubmit (19)
[92822.934252] btusb_bulk_complete: hci0 urb ef144e00 failed to resubmit (19)
[92822.934700] btusb_send_frame: hci0 urb ef3b0000 submission failed
[92823.187739] usb 2-3.2: USB disconnect, device number 19
[92823.187996] usb 2-3.3: USB disconnect, device number 20
[92824.444032] usb 2-3: new full speed USB device number 22 using ohci_hcd
[92824.668443] hub 2-3:1.0: USB hub found
[92824.671274] hub 2-3:1.0: 3 ports detected
[92824.974296] usb 2-3.2: new full speed USB device number 23 using ohci_hcd
[92825.102768] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.2/2-3.2:1.0/input/input74
[92825.102882] generic-usb 0003:0A5C:4502.0043: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:02.0-3.2/input0
[92825.177285] usb 2-3.3: new full speed USB device number 24 using ohci_hcd
[92825.307747] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.3/2-3.3:1.0/input/input75
[92825.307890] generic-usb 0003:0A5C:4503.0044: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:02.0-3.3/input0
[92825.517277] usb 2-3.1: new full speed USB device number 25 using ohci_hcd
[92827.972382] input: Rocketfish Bluetooth Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input76
[92827.972490] generic-bluetooth 0005:045E:8502.0045: input,hidraw2: BLUETOOTH HID v1.1c Keyboard [Rocketfish Bluetooth Keyboard] on 00:02:76:0C:37:40
[92835.540730] input: Rocketfish Bluetooth Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:12/input77
[92835.540867] generic-bluetooth 0005:0A5C:0001.0046: input,hidraw3: BLUETOOTH HID v1.29 Mouse [Rocketfish Bluetooth Mouse] on 00:02:76:0C:37:40
[93107.389438] input: Rocketfish Bluetooth Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:12/input78
[93107.389579] generic-bluetooth 0005:0A5C:0001.0047: input,hidraw3: BLUETOOTH HID v1.29 Mouse [Rocketfish Bluetooth Mouse] on 00:02:76:0C:37:40
[93166.752779] input: Rocketfish Bluetooth Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input79
[93166.752889] generic-bluetooth 0005:045E:8502.0048: input,hidraw2: BLUETOOTH HID v1.1c Keyboard [Rocketfish Bluetooth Keyboard] on 00:02:76:0C:37:40

```


Still no ideas? It's really annoying having my input devices cut-out on me like every minute

---

### Post by stumpalump on 2011-12-23
Here is dmesg when the icon actually disappears

```


[11264.340026] hci_cmd_timer: hci0 command tx timeout
[11336.559331] usb 2-3: USB disconnect, device number 10
[11336.559336] usb 2-3.1: USB disconnect, device number 13
[11336.559385] btusb_bulk_complete: hci0 urb f3198b00 failed to resubmit (19)
[11336.560384] btusb_bulk_complete: hci0 urb f3198c80 failed to resubmit (19)
[11336.560391] btusb_intr_complete: hci0 urb f3198580 failed to resubmit (19)
[11336.560754] btusb_send_frame: hci0 urb d0e41b80 submission failed
[11336.815369] usb 2-3.2: USB disconnect, device number 11
[11336.815587] usb 2-3.3: USB disconnect, device number 12
[11337.964039] usb 2-3: new full speed USB device number 14 using ohci_hcd
[11338.188610] hub 2-3:1.0: USB hub found
[11338.191402] hub 2-3:1.0: 3 ports detected
[11338.493400] usb 2-3.2: new full speed USB device number 15 using ohci_hcd
[11338.622920] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.2/2-3.2:1.0/input/input27
[11338.623034] generic-usb 0003:0A5C:4502.0016: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:02.0-3.2/input0
[11338.697419] usb 2-3.3: new full speed USB device number 16 using ohci_hcd
[11338.827881] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.3/2-3.3:1.0/input/input28
[11338.828040] generic-usb 0003:0A5C:4503.0017: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:02.0-3.3/input0
[11339.037400] usb 2-3.1: new full speed USB device number 17 using ohci_hcd
[11343.152631] input: Rocketfish Bluetooth Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/bluetooth/hci0/hci0:11/input29
[11343.152766] generic-bluetooth 0005:045E:8502.0018: input,hidraw2: BLUETOOTH HID v1.1c Keyboard [Rocketfish Bluetooth Keyboard] on 00:02:76:0C:37:40

```

Someone please help. I even tried a fresh install of 11.10 and instead of getting better it got worse. I can't even go a full minute it seems without losing mouse or keyboard.

Someone please post ANY suggestion

---

### Post by Oskar on 2012-01-09
Did you find a solution to this? I'm having the same problems.

---

### Post by henrodon on 2012-01-10
I'm having the same problem in 11.10 following an upgrade, but in my case, it's for a headset (which worked fine before the upgrade). It pairs, it works, it stops working, generally after 2 - 5 minutes. Sometimes it stops working even though the device is still listed in the Bluetooth manager. Sometimes it disappears from the manager. I've tried:
1. another headset.
2. Uninstalling and re-installing the default bluetooth manager.
3. Uninstalling the default manager and installing Blueman.

Any ideas would be welcome, especially ones that don't involve extensive editing of files that I don't really understand very well. I'm hoping for a "Do this and it just works," kind of solution. But I'm really hoping for a solution since I use the headset daily.

---

### Post by stumpalump on 2012-01-12
After booting into windows I concluded that my issue was hardware related. However, if upgrading I'd suggest a fresh install first

---

### Post by mpicher on 2013-01-25
This did it for me:

Scan for devices:

hcitool scan
 Scanning ...
       00:24:7C:2F:92:7C       Logitech K810

Attach device:

hcitool cc 00:24:7C:2F:92:7C && hcitool auth 00:24:7C:2F:92:7C

Then it appeared in my Bluetooth devices window. Then I only needed to turn it on there.

I was getting the same errors as others here.

---

