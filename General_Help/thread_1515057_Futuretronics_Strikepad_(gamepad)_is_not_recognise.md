---
title: "Futuretronics Strikepad (gamepad) is not recognised (Quickshot QS-6238)"
date: 2010-06-21
forum: General Help
---

### Post by Lord Quinny on 2010-06-21
Hello,

I am relative newby to Ubuntu and linux in general.

I just got a Futuretronics FUT-400 Strikepad, which is a rebranded Quickshot QS-6238 gamepad. It's a USB gamepad which works in Windows.

When I connect the gamepad it gives me this error in dmesg.

```

[ 5960.557023] usb 5-1: new low speed USB device using uhci_hcd and address 2
[ 5960.738127] usb 5-1: configuration #1 chosen from 1 choice
[ 5965.783668] generic-usb: probe of 0003:04B4:9191.0004 failed with error -22

```


Can someone please tell me what that error means and how I can get this gamepad working?

Here is the lsusb -v output:

```

Bus 005 Device 002: ID 04b4:9191 Cypress Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0x9191 
  bcdDevice            1.00
  iManufacturer           1 Galy
  iProduct                2 Futuretronics Advance Joypad
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          3 HID - Gamepad
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              4 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval              10
        ** UNRECOGNIZED:  09 21 00 01 00 01 22 6e 00
Device Status:     0x0000
  (Bus Powered)

```

$ uname -r
2.6.32-22-generic

Thanks,
Adam

---

### Post by Lord Quinny on 2010-06-22
*bump*

Can anyone help?

---

### Post by Pq2son2 on 2010-06-22
Hi,

I have the same problem, but with eGalax TouchScreen and I don't know what kind of error is -22. My output it's really similar.

```
[    6.275064] usb 4-2: configuration #1 chosen from 1 choice
[    6.291136] generic-usb: probe of 0003:0EEF:0001.0002 failed with error -22

```

I will wait the responses! Thank you! and good luck!

---

### Post by Lord Quinny on 2010-06-24
*bump*

Please can some knowledgable person help?

---

