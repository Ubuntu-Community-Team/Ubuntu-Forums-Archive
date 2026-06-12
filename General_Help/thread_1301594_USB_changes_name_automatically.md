---
title: "USB changes name automatically"
date: 2009-10-26
forum: General Help
---

### Post by Marin_ on 2009-10-26
Hi all. Im working with GPS receivers, and to receive data and to send data to them i work in ubuntu (progamming in C), and use Serial port communication via USB.
I open the port, and after read the data in a infinite cycle.
If i run this about 1hour, or 2 hours, the device (in this case USB0) disappear and the communication with receiver ends.
Summarizing, when i turn on the pc, and if i go to filesystem, the device USB0 is there. Then i start the program (communicate with GPS receiver) and 1 hour, 2 hours or less, the program automatically finish and output an errno = 19, what means "no such device". Well if i go to filesystem the device that appears there is not USB0 but USB1. I dont understand why USB0 disappears and turn on USB1.
 
Its important, if anyone could help me to solve this..
 
Thank you

---

### Post by P4man on 2009-10-26
sounds like a problem with the usb controller. Did you check dmesg for errors?

---

### Post by Marin_ on 2009-10-26
How can i use that?

---

### Post by P4man on 2009-10-26
just run dmesg in a terminal. Copy paste any relevant messages. If you its been too long, check the logs in /var/log/messages or view them through system > adminstration > logfile viewer

---

### Post by Marin_ on 2009-10-26
Ok thanks. And what should I expect to see?

---

### Post by Marin_ on 2009-10-26
pedro-desktop kernel: [23383.096051] usb 2-2: USB disconnect, address 2
Oct 26 01:28:17 
pedro-desktop kernel: [23383.096738] ftdi_sio 2-2:1.0: device disconnected
Oct 26 01:28:18 
pedro-desktop kernel: [23383.336022] usb 2-2: new full speed USB device using uhci_hcd and address 3
Oct 26 01:28:18 
pedro-desktop kernel: [23383.527527] usb 2-2: configuration #1 chosen from 1 choice
Oct 26 01:28:18 
pedro-desktop kernel: [23383.534689] ftdi_sio 2-2:1.0: FTDI USB Serial Device converter detected
Oct 26 01:28:18 
pedro-desktop kernel: [23383.534732] usb 2-2: Detected FT232BM
Oct 26 01:28:18 
pedro-desktop kernel: [23383.534836] usb 2-2: FTDI USB Serial Device converter now attached to ttyUSB1


I have this messages there. The time in messages is when the port USB0 convert to USB1

---

### Post by QLee on 2009-10-26
> **Marin_ said:**
> pedro-desktop kernel: [23383.096051] usb 2-2: USB disconnect, address 2
Oct 26 01:28:17 
pedro-desktop kernel: [23383.096738] ftdi_sio 2-2:1.0: device disconnected
Oct 26 01:28:18 
pedro-desktop kernel: [23383.336022] usb 2-2: new full speed USB device using uhci_hcd and address 3
Oct 26 01:28:18 
pedro-desktop kernel: [23383.527527] usb 2-2: configuration #1 chosen from 1 choice
Oct 26 01:28:18 
pedro-desktop kernel: [23383.534689] ftdi_sio 2-2:1.0: FTDI USB Serial Device converter detected
Oct 26 01:28:18 
pedro-desktop kernel: [23383.534732] usb 2-2: Detected FT232BM
Oct 26 01:28:18 
pedro-desktop kernel: [23383.534836] usb 2-2: FTDI USB Serial Device converter now attached to ttyUSB1


I have this messages there. The time in messages is when the port USB0 convert to USB1

Okay, so something (no way to determine what from the info) caused the serial port to lose the connection to USB and then it reconnected. Presumably, this happens due to something about the serial dongle. 

You can probably set a udev rule to make it always take the same port during a reconnect if you can't figure out why it's disconnecting.

---

### Post by Marin_ on 2009-10-26
Hm.. I dont know about udev rules. Can you please write some code?

---

### Post by Marin_ on 2009-10-26
I search about udev, but i dont understand everything. When i associate /dev/ttyUSB0, to a name that i choose like receiver0, when port USB0 changes to USB1 and in the program i run receiver0, it is the same if i run USB0 or not?
How can udev code help me?

---

### Post by Marin_ on 2009-10-26
> **QLee said:**
> Okay, so something (no way to determine what from the info) caused the serial port to lose the connection to USB and then it reconnected. Presumably, this happens due to something about the serial dongle. 

You can probably set a udev rule to make it always take the same port during a reconnect if you can't figure out why it's disconnecting.


I search about udev, but i dont understand everything. When i associate /dev/ttyUSB0, to a name that i choose like receiver0, when port USB0 changes to USB1 and in the program i run receiver0, it is the same if i run USB0 or not?
How can udev code help me?

---

### Post by jhb1608 on 2009-10-26
Please don't double post.

---

### Post by P4man on 2009-10-26
I know nothing about udev, but if you can spare the time, this may help:
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

it has a few examples that may get you started...

---

### Post by capscrew on 2009-10-26
> **Marin_ said:**
> Hi... I dont understand why USB0 disappears and turn on USB1.
 
Its important, if anyone could help me to solve this..
 
Thank you

If you are using Linux (and I assume you are), the drives are ID'd in the ***order of discovery***.  This means that they can (and as you experienced) change the *drive ID*.

You should use the UUID of the drive.  This never changes.  To see the UUID try this```
sudo blkid
```

You should see the UUID for the USB device.  The Drive ID will change but the UUID never does.

An example of this usage is the /etc/fstab file.  I have used UUID's in some of my scripts too.

---

### Post by Marin_ on 2009-10-26
/dev/sda1: UUID="0912-54CC" TYPE="vfat" 
/dev/sda2: UUID="0E7C53CE7C53AEE9" LABEL="Partition_1" TYPE="ntfs" 
/dev/sda5: UUID="6C5CC7385CC6FC38" TYPE="ntfs" 
/dev/sda6: UUID="2db1da9e-91c9-488a-abdb-ad80d77543fc" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="bbbcdb98-d7c0-47c2-8091-24183fffd149"

With sudo blkid i have this.

How can i use that?

I have to open a serial communication to device where i use /dev/ttyUSB0. Instead of this i use another name?

---

### Post by capscrew on 2009-10-26
> **Marin_ said:**
> /dev/sda1: UUID="0912-54CC" TYPE="vfat" 
/dev/sda2: UUID="0E7C53CE7C53AEE9" LABEL="Partition_1" TYPE="ntfs" 
/dev/sda5: UUID="6C5CC7385CC6FC38" TYPE="ntfs" 
/dev/sda6: UUID="2db1da9e-91c9-488a-abdb-ad80d77543fc" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="bbbcdb98-d7c0-47c2-8091-24183fffd149"

With sudo blkid i have this.

How can i use that?

I have to open a serial communication to device where i use /dev/ttyUSB0. Instead of this i use another name?

Ooops, I see now that you are using a serial port (not a block device) named USB0.  What type of device is this?

The UUID is for block devices (block storage media) only I believe.  Sorry for the confusion.

---

### Post by Marin_ on 2009-10-26
The device is a GPS receiver.

Do you know another way to solve the problem?

Im working in ubuntu.

---

### Post by capscrew on 2009-10-26
> **Marin_ said:**
> The device is a GPS receiver.

Do you know another way to solve the problem?

Im working in ubuntu.

Not really, but I have some things I would try.  Remember that the USB serial port is shared (steering is provided by the chip and driver).  

In this order I would try: 
 
Adding a dedicated serial port card for the GPS.

or

2) Removing all other usb devices (keyboard and mouse)

EDIT:  3) Buffer the data stream from the GPS.  Then pick up the data from the buffer rather than directly.

---

### Post by Marin_ on 2009-10-26
> **capscrew said:**
> Not really, but I have some things I would try.  Remember that the USB serial port is shared (steering is provided by the chip and driver).  

In this order I would try: 
 
Adding a dedicated serial port card for the GPS.

or

2) Removing all other usb devices (keyboard and mouse)

Ok thanks for help

---

