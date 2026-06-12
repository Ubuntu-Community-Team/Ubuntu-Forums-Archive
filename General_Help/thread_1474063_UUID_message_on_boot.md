---
title: "UUID message on boot"
date: 2010-05-05
forum: General Help
---

### Post by LinScape on 2010-05-05
Hi, i notice that every time I boot ubuntu theres this message saying that UUID could't mount a filesystem, then i notice that i have no swap activated. So i executed gparted and found out that the swap was not in use. So I used the swapon -a command and the terminal tell me this:

swapon: cannot find the device for UUID=3efaa7cf-e2f0-469b-b5c2-2bb8ef43cf93

how can i fix this and get my swap activated every time I boot just in case i need it?

---

### Post by WorMzy on 2010-05-05
Could you post the contents of /etc/fstab, and the output of 'sudo blkid' please. We can advise you how to proceed from there. :)

---

### Post by LinScape on 2010-05-05
fstab: # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # #                 proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda5 during installation UUID=5a098a3b-ffa9-41d9-83dd-7fa0ad9f9297 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda6 during installation UUID=3efaa7cf-e2f0-469b-b5c2-2bb8ef43cf93 none            swap    sw              0       0 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0   sudo blkid: /dev/sda1: UUID=&quot;805028AD5028ABBA&quot; TYPE=&quot;ntfs&quot;  /dev/sda5: UUID=&quot;5a098a3b-ffa9-41d9-83dd-7fa0ad9f9297&quot; TYPE=&quot;ext4&quot;  /dev/sda6: UUID=&quot;e940e641-77ec-4e2c-a847-88df8e77e08a&quot; TYPE=&quot;swap&quot;

---

### Post by WorMzy on 2010-05-05
Okay, in fstab, the UUID of your swap partition is incorrect. Change the line
```
UUID=3efaa7cf-e2f0-469b-b5c2-2bb8ef43cf93 none swap sw 0 0
```
with this:
```
UUID=e940e641-77ec-4e2c-a847-88df8e77e08a none swap sw 0 0
```

Then it should work. :)

---

### Post by LinScape on 2010-05-05
YES!! It works, thank you. ^_^ Now i have my swap back.

---

