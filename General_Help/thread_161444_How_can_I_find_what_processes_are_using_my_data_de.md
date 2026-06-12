---
title: "How can I find what processes are using my data devices?"
date: 2006-04-17
forum: General Help
---

### Post by SolidAndShade on 2006-04-17
Every so often, I want to unmount something but I fail and get a "device is busy" notice. Then I'll terminate programs all the way down to a bare desktop and the device will still be busy, requiring me to log out and back in to unmount the device. Is there any way to find out what processes are using the devices so I can find exactly what to terminate? Thanks.

---

### Post by gerbman on 2006-04-17
[QUOTE=SolidAndShade]Every so often, I want to unmount something but I fail and get a "device is busy" notice. Then I'll terminate programs all the way down to a bare desktop and the device will still be busy, requiring me to log out and back in to unmount the device. Is there any way to find out what processes are using the devices so I can find exactly what to terminate? Thanks.[/QUOTE]Issue the following:```
fuser <device, file, etc.>
```I think that will get you what you want.

---

