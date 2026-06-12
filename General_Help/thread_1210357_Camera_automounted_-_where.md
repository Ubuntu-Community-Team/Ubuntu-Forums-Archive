---
title: "Camera automounted - where?"
date: 2009-07-11
forum: General Help
---

### Post by drhex on 2009-07-11
In other linuxes I've tried, I could retrieve files from my digital camera by pluggning it in to a USB port and running

gphoto2 --get-all-files

(the camera works by PTP only, not as a usb mass storage device).

Now, when I plug the camera into an ubuntu 9.04 system a camera icon pops up on the desktop. If I try gphoto2, it complains that the camera is already in use. Right-clicking the camera icon and selecting "unmount volume" helps, but I am looking for a solution that does not require manual mousework.

If the camera is "mounted", then it should be possible to read the files from there, but neither of

df
ls /media
cat /etc/mtab

shows anything extra after plugging in the camera even though the desktop icon is there.

---

### Post by Lampi on 2009-07-11
Use dmesg instead

---

### Post by drhex on 2009-07-11
These lines were added to the dmesg output. Doesn't say much about where the camera might be mounted

```
[1051255.188041] usb 1-10: new high speed USB device using ehci_hcd and address 17
[1051255.380652] usb 1-10: configuration #1 chosen from 1 choice
```

---

### Post by drhex on 2009-07-11
Found it - the PTP data is mounted under ~/.gvfs
and is apparently controlled by a process called 
/usr/lib/gvfs/gvfs-gphoto2-volume-monitor

---

