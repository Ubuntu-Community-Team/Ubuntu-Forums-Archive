---
title: "Piranha Magnum mp3 player resetting"
date: 2010-04-03
forum: General Help
---

### Post by Almin on 2010-04-03
Hi, I have a piranha magnum mp3 player which is connected with usb cable. When i connect the player it's resetting.

dmesg output;

```
[11326.752063] usb 2-3: new full speed USB device using ohci_hcd and address 2
[11326.964442] usb 2-3: configuration #1 chosen from 1 choice
[11327.742086] Initializing USB Mass Storage driver...
[11327.742319] scsi2 : SCSI emulation for USB Mass Storage devices
[11327.742665] usbcore: registered new interface driver usb-storage
[11327.742673] USB Mass Storage support registered.
[11327.745326] usb-storage: device found at 2
[11327.745334] usb-storage: waiting for device to settle before scanning
[11332.745259] usb-storage: device scan complete
[11332.752226] scsi scan: INQUIRY result too short (5), using 36
[11332.752240] scsi 2:0:0:0: Direct-Access     PIRANHA                   1.00 PQ: 0 ANSI: 0 CCS
[11332.757610] sd 2:0:0:0: Attached scsi generic sg4 type 0
[11332.770206] sd 2:0:0:0: [sdd] 1981937 512-byte logical blocks: (1.01 GB/967 MiB)
[11332.777206] sd 2:0:0:0: [sdd] Write Protect is off
[11332.777214] sd 2:0:0:0: [sdd] Mode Sense: 00 c0 00 00
[11332.777221] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[11332.803201] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[11332.803213]  sdd:
[11332.897233] sd 2:0:0:0: [sdd] Assuming drive cache: write through
[11332.897247] sd 2:0:0:0: [sdd] Attached SCSI removable disk
[11334.748580] usb 2-3: USB disconnect, address 2
[11341.628046] usb 2-3: new full speed USB device using ohci_hcd and address 3
[11341.840381] usb 2-3: configuration #1 chosen from 1 choice
[11341.955195] scsi3 : SCSI emulation for USB Mass Storage devices
[11341.956970] usb-storage: device found at 3
[11341.956977] usb-storage: waiting for device to settle before scanning
[11346.958098] usb-storage: device scan complete
[11346.965047] scsi scan: INQUIRY result too short (5), using 36
[11346.965062] scsi 3:0:0:0: Direct-Access     PIRANHA                   1.00 PQ: 0 ANSI: 0 CCS
[11346.970037] sd 3:0:0:0: Attached scsi generic sg4 type 0
[11346.980048] sd 3:0:0:0: [sdd] 1981937 512-byte logical blocks: (1.01 GB/967 MiB)
[11346.987038] sd 3:0:0:0: [sdd] Write Protect is off
[11346.987047] sd 3:0:0:0: [sdd] Mode Sense: 00 c0 00 00
[11346.987054] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[11347.013067] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[11347.013083]  sdd:
[11347.112054] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[11347.112067] sd 3:0:0:0: [sdd] Attached SCSI removable disk
[11348.762497] usb 2-3: USB disconnect, address 3
[11355.580054] usb 2-3: new full speed USB device using ohci_hcd and address 4
[11355.792367] usb 2-3: configuration #1 chosen from 1 choice
[11355.815070] scsi4 : SCSI emulation for USB Mass Storage devices
[11355.821628] usb-storage: device found at 4
[11355.821635] usb-storage: waiting for device to settle before scanning
[11360.822071] usb-storage: device scan complete
[11360.829020] scsi scan: INQUIRY result too short (5), using 36
[11360.829035] scsi 4:0:0:0: Direct-Access     PIRANHA                   1.00 PQ: 0 ANSI: 0 CCS
[11360.834239] sd 4:0:0:0: Attached scsi generic sg4 type 0
[11360.853070] sd 4:0:0:0: [sdd] 1981937 512-byte logical blocks: (1.01 GB/967 MiB)
[11360.860051] sd 4:0:0:0: [sdd] Write Protect is off
[11360.860062] sd 4:0:0:0: [sdd] Mode Sense: 00 c0 00 00
[11360.860068] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[11360.887011] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[11360.887024]  sdd:
[11360.981041] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[11360.981054] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[11361.564035] usb 2-3: reset full speed USB device using ohci_hcd and address 4
[11361.744058] usb 2-3: device descriptor read/64, error -62
[11362.028093] usb 2-3: device descriptor read/64, error -62
[11362.308036] usb 2-3: reset full speed USB device using ohci_hcd and address 4
[11362.488035] usb 2-3: device descriptor read/64, error -62
[11362.772025] usb 2-3: device descriptor read/64, error -62
[11363.052033] usb 2-3: reset full speed USB device using ohci_hcd and address 4
[11363.460048] usb 2-3: device not accepting address 4, error -62
[11363.636033] usb 2-3: reset full speed USB device using ohci_hcd and address 4
[11364.044063] usb 2-3: device not accepting address 4, error -62
[11364.044124] usb 2-3: USB disconnect, address 4
[11364.232045] usb 2-3: new full speed USB device using ohci_hcd and address 5
[11364.416084] usb 2-3: device descriptor read/64, error -62
[11364.700042] usb 2-3: device descriptor read/64, error -62
[11364.980070] usb 2-3: new full speed USB device using ohci_hcd and address 6
[11365.160052] usb 2-3: device descriptor read/64, error -62
[11365.444036] usb 2-3: device descriptor read/64, error -62
[11365.724038] usb 2-3: new full speed USB device using ohci_hcd and address 7
[11366.132046] usb 2-3: device not accepting address 7, error -62
[11366.308061] usb 2-3: new full speed USB device using ohci_hcd and address 8
[11366.716038] usb 2-3: device not accepting address 8, error -62
[11366.716073] hub 2-0:1.0: unable to enumerate USB device on port 3

```

lsusb -v output

```
Bus 002 Device 017: ID 10d6:1100 Actions Semiconductor Co., Ltd MPMan MP-Ki 128 MP3 Player/Recorder
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x10d6 Actions Semiconductor Co., Ltd
  idProduct          0x1100 MPMan MP-Ki 128 MP3 Player/Recorder
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      5 SFF-8070i
      bInterfaceProtocol     80 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)

```

---

### Post by Chronon on 2010-04-03
It seems like it's suffering a hardware or firmware failure.  Is there an emergency restore/upgrade feature you can use?

---

### Post by Almin on 2010-04-04
No there's not a emergency or update mode here. But there is a firmware update mode. But the program is in windows program. I have a laptop which is using vista and program isn't working under vista.

---

### Post by Almin on 2010-04-09
No answer?

---

### Post by Chronon on 2010-04-09
You need to consult the documentation for your player and find a way to try to restore the firmware (like a DFU mode).  The main prospect for hope that I can see is if there's a separate DFU (device firmware upgrade) mode that has its own USB stack and is unrelated to the functionality of the main firmware binary.  (This assumes that USB is controlled by a software stack rather than a hardware bridge.  If it's hardware controlled and the USB controller has failed, then your only prospect is to replace the hardware.)

If DFU is available and allows a USB connection then you should try to restore a new firmware.  If it isn't available then I don't see any options.

---

### Post by Almin on 2010-04-09
I upgraded my mp3 player but it's still resetting. I used this mp3 player on mandriva in 2007 or 2008. But it doesn't work in ubuntu 10.04.

---

### Post by Almin on 2010-04-11
I installed 9.04. It didn't restart. I upgraded to 9.10 it stopped working again. I think it's a kernel problem and i want to use the latest version. What should I do?

---

### Post by Chronon on 2010-04-12
I have plenty of UMS devices that work fine in 9.10.  Maybe your device does something non-standard.  It's not clear where the fault is.  

You could report this as a bug, but it might be difficult for developers to address this if they can't reproduce this bug.

--
Edit: You only said that it didn't restart with 9.04.  Did it properly mount and allow access as a UMS device?  If not, it could be that it didn't cause a restart because there was a bug in Jaunty that prevented auto-mounting of UMS devices due to them being improperly detected as MTP devices.

---

### Post by Almin on 2010-04-16
Yes i can acces all of my files and everything i can upgrade the software. How can i fix that?

---

### Post by Chronon on 2010-04-16
If it's worth it to you then you can opt to use Jaunty.  Since you are the only one that seems to be having this problem it seems you have to try to troubleshoot on your end.  Every MSC device I own works just fine in Karmic.

You might want to confirm that your cable hasn't gone bad.  This can happen abruptly at random times.  It could lead to random disconnections. (Does your device normally reset after disconnecting from a USB session?)  

Try connecting to other operating systems, try different cables, etc.  At the very least, these are good things to try to eliminate possible causes.

---

### Post by Almin on 2010-04-16
I tested all of possibilities. I tried it with Windows 7, Ubuntu 9.04 it worked. But it doesn't work on later versions of Ubuntu. What is the problem? I see USB storage device threads on the forum i think there is a bug with usb mass storage device drivers.

---

### Post by Chronon on 2010-04-16
> **Almin said:**
> I tested all of possibilities. I tried it with Windows 7, Ubuntu 9.04 it worked. But it doesn't work on later versions of Ubuntu. What is the problem? I see USB storage device threads on the forum i think there is a bug with usb mass storage device drivers.

That is certainly possible.  It's also possible that there's a bug or failure in the USB controller or software stack of your player.  Do you have any other UMS devices (like external HD or flash drive, etc.)?  If you can't demonstrate how to cause the drivers to fail then there's little chance that a developer can do anything to address this.

---

### Post by Almin on 2010-04-17
I have 3 flash drive too. One of these doesn't work too. It gives the same problem. Its led is blinking when it's connected but it doesn't blinking.

---

### Post by Chronon on 2010-04-17
So, some devices work properly on your system and some don't.  I'm not really sure how to figure out what causes the different behavior (I assume dmesg gives the same output for your mp3 player and the non-working flash drive).

Barring further input I guess it's up to you to decide whether or not it's worthwhile to post a bug report about this.

---

### Post by Almin on 2010-04-17
I post it as a bug. I'm waiting for a solution.

---

