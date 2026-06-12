---
title: "how to reload a previously ejected usb key?"
date: 2010-09-20
forum: General Help
---

### Post by bluefrog on 2010-09-20
I insert a usb key. it is mounted automatically.
I eject it but leave it plugged in. I do not have access to it anymore.
Is there a way to "reload" it via command line without having to unplug it and plug it again?

---

### Post by bluefrog on 2010-09-20
My problem is that I am trying to force the re-detection of a usb key after it has been ejected (not physically of course...). I was thinking of 
udevadm test --force --action=add /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/host29/target29:0:0/29:0:0:0/block/sdd

but --force is not recognized. Do I have another way to achieve what I want to do?

---

