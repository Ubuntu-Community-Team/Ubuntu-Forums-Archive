---
title: "need to copy usb drive image (usb copy utility)"
date: 2010-08-25
forum: General Help
---

### Post by marcusdufrane on 2010-08-25
Im pretty sure there is a utility that copies byte for byte for linux that i could use to copy an image of a usb and later write it to another. Cant remember the name of the one i used before but if anyone could help I would be grateful.

---

### Post by dynamo2 on 2010-08-25
To copy the image from usb drive /dev/sdb to the file 'usbdiskimage' in the current directory:
```
dd if=/dev/sdb of=./usbdiskimage
```

To restore the image to another usb disk (same capacity), where /dev/sdc is the device name:
```
dd if=./usbdiskimage of=/dev/sdc
```

might have to sudo those, and make sure the command is correct before hitting return, you wont want to accidentally copy the image to your main hard drive or something!

---

