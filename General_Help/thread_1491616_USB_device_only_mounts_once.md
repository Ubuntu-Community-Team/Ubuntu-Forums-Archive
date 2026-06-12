---
title: "USB device only mounts once"
date: 2010-05-23
forum: General Help
---

### Post by hwttdz on 2010-05-23
I'm having difficulty getting a usb device (garmin edge 500) to mount.  I believe the behavior is that it mounts the first time after startup but not again.  

dmesg of failed mount:
```
[76991.476050] usb 4-1: new full speed USB device using uhci_hcd and address 5
[76991.638744] usb 4-1: configuration #1 chosen from 1 choice
[76991.641748] scsi11 : SCSI emulation for USB Mass Storage devices
[76991.641825] usb-storage: device found at 5
[76991.641828] usb-storage: waiting for device to settle before scanning
[76994.141619] usb 4-1: USB disconnect, address 5
```

It's not a power issue (I connected it with a 2 prong usb cable in case the port wasn't providing enough power).

---

### Post by hwttdz on 2010-05-28
Help?

---

### Post by raintonr on 2010-06-12
Same issue here. Anyone got any ideas?

I have another machine with kernel 2.6.27.7 and an Edge 500 mounts fine when connected there.

I think the problem started on Kernels 2.6.32.11-99 onwards but cannot be sure.

---

### Post by Paul41 on 2010-06-12
I'm having the same problem. My work around has been manually mounting. The only problem I have doing it this way is that I can't use it in VirtualBox, which means I have to manually upload files.

---

### Post by john newbuntu on 2010-06-12
Does this help? at least a lil bit?
[https://forums.garmin.com/showthread.php?t=5916](https://forums.garmin.com/showthread.php?t=5916)

---

### Post by raintonr on 2010-06-12
> **john newbuntu said:**
> Does this help? at least a lil bit?
[https://forums.garmin.com/showthread.php?t=5916](https://forums.garmin.com/showthread.php?t=5916)

Not really.

How does one do this, 'manual mount' discussed above?

When I 'lsusb' the device doesn't even show in that list :(

---

### Post by hwttdz on 2010-06-22
I've found this little script allows me to mount multiple times.  The important bit seems to be unmounting before removing.  

```
#!/bin/bash
mv /media/GARMIN/Garmin/Activities/* /media/media_lib/training_files/
umount /media/GARMIN
VirtualBox --startvm windows_xp_machine
```

And of course replace my training files directory with something that applies.  I move all the .fit files off the garmin and then import from that directory in virtualbox, it's a shared directory so this becomes convenient.

---

