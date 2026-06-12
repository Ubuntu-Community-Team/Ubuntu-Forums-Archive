---
title: "Automatically copy files from usb drive on insertion?"
date: 2012-03-31
forum: General Help
---

### Post by tstack77 on 2012-03-31
Is there a program that does what the title suggests? I am trying to set up a backup to a non-networked computer that automatically can detect the differences/added files on a usb stick, then copy them with the same file directory on the drive while ignoring duplicates.

Possible?

---

### Post by savanna on 2012-03-31
Yes, using udev rules in /**etc/udev/rules.d**.

First identify the device by doing a **tail -f /var/log/dmesg**, and plugging in and removing the device. Then use **udevinfo** on the device to find more detailed information on the device.

Add a new rule file eg **/etc/udev/rules.d/90_my_usb.rules**. Using the information from **udevinfo** to filter just on your device and call a shell script to rsync across your files.

---

### Post by tstack77 on 2012-03-31
Cool, my project today is learning my way around rsync. Thanks for the point in the right direction!

---

