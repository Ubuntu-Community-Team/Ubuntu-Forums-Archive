---
title: "File SYSTEM QUESTION"
date: 2011-03-13
forum: General Help
---

### Post by Diametric on 2011-03-13
Hello,

Can anyone tell me why (or point me to an explanation) my 1TB USB external HD is listed as /sdc2 - I get that the HAL facitlity detects removable media, but why isn't it sda2? I only have one 80GB sata drive (internal) and no other partitions, other than a swap space.  Just trying to learn the naming convention.

Thank you!

---

### Post by lithopsian on 2011-03-13
There isn't so much a naming convention as an order that the disks are found.  sdc is the third (SCSI) hard drive device to be discovered at boot time.  Note that a great many storage devices are treated as SCSI by the Linux kernel even if they aren't actually SCSI.  On a different boot it may well come back as sdb or something else.  Because of this you are advised to reference drives by their UUID values so that they are always mounted correctly even if they are discovered in a different order and receive different device names.

The number refers top partitions on the same device, so sdc2 would be the second partition on that device.  sdc1 may be an extended partition and so sdc2 may be the first and perhaps only mountable partition.

---

### Post by Diametric on 2011-03-13
> **lithopsian said:**
> There isn't so much a naming convention as an order that the disks are found.  sdc is the third (SCSI) hard drive device to be discovered at boot time.  Note that a great many storage devices are treated as SCSI by the Linux kernel even if they aren't actually SCSI.  On a different boot it may well come back as sdb or something else.  Because of this you are advised to reference drives by their UUID values so that they are always mounted correctly even if they are discovered in a different order and receive different device names.

The number refers top partitions on the same device, so sdc2 would be the second partition on that device.  sdc1 may be an extended partition and so sdc2 may be the first and perhaps only mountable partition.

Wow.  Very cool info - thank you.  I didn't know that Linux handled so many devices as SCSI.  So, why do you say "On a different boot it may well come back as a sdb or something else"?  Does that mean that upon reboot, the USB external label could change, or are you referring to something else?

Cheers,
-Dylan

---

### Post by lithopsian on 2011-03-13
> Does that mean that upon reboot, the USB external label could changeThat's exactly what I'm saying.  This is most likely if you have multiple drives of the same type, for example two USB drives.  You might be able to force it by swapping the USB slots used, but depending on the drives they still might get detected in the same order.  Unplugging the first one to be detected would obviously change the device name of the other one when you rebooted.

---

### Post by Diametric on 2011-03-13
I get it - this allows for a more dynamic "naming convention" and thusly more flexible as opposed to MS where it's more static and restricted.

Awesome.  Thanks again.

---

