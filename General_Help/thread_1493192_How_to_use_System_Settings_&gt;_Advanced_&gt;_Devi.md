---
title: "How to use System Settings &gt; Advanced &gt; Device Actions"
date: 2010-05-25
forum: General Help
---

### Post by tdn on 2010-05-25
I am trying to use the Device Actions under System Settings > Advanced to automatically copy image files from my CF-card from my camera. I home someone has a few minutes to help me. I am not sure how do identify my device.

 I have watched udevadm monitor, while I insert the card into the card reader. One of the lines that appear is this: UDEV  [1274814950.587968] add      
/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/host5/target5:0:0/5:0:0:0/block/sdc/sdc1 (block)

---

### Post by betlog on 2010-07-16
I am attempting to plug in a Canon PowerShot S3 IS, and absolutely NOTHING happens when I do. Previous ubuntus would immediately launch some action... 10.04 does nothing.
 Because of this I have also been lookign for documentation on how to use the Device Actions screen. It looks to me like there needs to be a diagnostic tool linked to the Device Actions menu if things arent just automagically recognised and the user queried.
 
Is udevadm the only tool we need to be using here, surely theres somehting a little more informative?

Is there some documentation resource or thread on this that I have been unable to find so far?


$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1279282863.898451] add      /devices/pci0000:00/0000:00:0b.1/usb1/1-1 (usb)
KERNEL[1279282863.901297] add      /devices/pci0000:00/0000:00:0b.1/usb1/1-1/1-1:1.0 (usb)
UDEV  [1279282863.902798] add      /devices/pci0000:00/0000:00:0b.1/usb1/1-1 (usb)
UDEV  [1279282863.905669] add      /devices/pci0000:00/0000:00:0b.1/usb1/1-1/1-1:1.0 (usb)
KERNEL[1279282868.520904] remove   /devices/pci0000:00/0000:00:0b.1/usb1/1-1/1-1:1.0 (usb)
KERNEL[1279282868.521067] remove   /devices/pci0000:00/0000:00:0b.1/usb1/1-1 (usb)
UDEV  [1279282868.521528] remove   /devices/pci0000:00/0000:00:0b.1/usb1/1-1/1-1:1.0 (usb)
UDEV  [1279282868.524885] remove   /devices/pci0000:00/0000:00:0b.1/usb1/1-1 (usb)

So the system knows it's there... it just doesn't do anyhting about it.

Suggestions please.

---

### Post by betlog on 2010-07-17
ok let me rephrase that:
where can I find an app to interrogate the kinds of match names that a 'Device Actions" filter wants the user to input?

---

