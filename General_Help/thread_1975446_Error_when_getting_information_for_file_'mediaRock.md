---
title: "Error when getting information for file '/media/Rock': No such file"
date: 2012-05-07
forum: General Help
---

### Post by SuperFreak on 2012-05-07
I am getting the following message when I try to mount an external NTFS drive through USB 3.0
Error when getting information for file '/media/': No such file
I also get another message (see screen shot)
It seems to work OK with USB 2.0

Any ideas?

---

### Post by SuperFreak on 2012-05-08
bump

It seems as though Ubuntu recognizes there is a USB 3.0 connection but I can't mount the drive

```
david@david-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f9:01f5 Brother Industries, Ltd 
Bus 002 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 002 Device 004: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 005: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 002 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
david@david-desktop:~$ 

```

Would anyone be able to help me get my USB 3.0 drive to mount?

---

### Post by SuperFreak on 2012-05-09
bump

usb drive will work for mouse and usb key(non boot) but not for my drive. It will show the drive in Places for an instant and then it disappears

 I am able to use the rear USB 3 connectors not the front. I guess that's better than nothing

---

