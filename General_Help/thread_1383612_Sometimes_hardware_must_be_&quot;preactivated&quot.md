---
title: "Sometimes hardware must be &quot;preactivated&quot; by Windows in dual boot. Why?"
date: 2010-01-17
forum: General Help
---

### Post by jaezcurra on 2010-01-17
Surfing this forum and speaking from my own experience, I have realised that sometimes, some pieces of hardware do not work in Ubuntu, in a dual boot pc, if they have not been used ("preactivated"?) in Windows before.
I have a AIO VGC-LT2S Sony and to have, for instance, the webcam "seen" by Cheese after installing Karmic for the first time (and it seems to me that even after any kernel upgrade), I have to boot previously in Vista, use the webcam and then boot in Ubuntu.  Otherwise, a program like Cheese does not "see" it.
Once "seen" by Ubuntu this hardware works flawlessly.
Why could this happen?

---

### Post by jaezcurra on 2010-01-18
Bump

---

### Post by Hazey on 2010-01-18
Hi,

can you try booting ubuntu three or four times in series without booting vista before? Do you have the same problem then?

Regards,
Hazey

---

### Post by jaezcurra on 2010-01-18
Thanks for the reply.
I'll certainly do that next time I have a new kernel upgrade, as this is the only moment I miss Ubuntu not "seeing" the hardware.
As I currently have 2.6.31-17 installed, I will have to wait till 2.6.31-18 is released.
But my question remains: why can this happen?

---

### Post by 3rdalbum on 2010-01-18
> **jaezcurra said:**
> 
But my question remains: why can this happen?

It's probably firmware. Some devices need the driver to transfer a little piece of code to them, that gets executed on the device. They need this firmware sent to them every time they are turned on.

When you boot into Windows, the Windows driver takes hold of the webcam and pushes the firmware to it. Then when you reboot, the webcam still has power and still has the firmware, so Ubuntu's driver can use it without having the firmware.

When you shut down fully, the webcam loses power and loses the contents of its memory.

You can probably fix this. There might be a firmware file for this camera available on the web. You can drop this into /lib/firmware and it will be sent to the webcam when the Ubuntu driver takes hold of the camera.

---

### Post by jaezcurra on 2010-01-18
Many thanks.  Sounds good. I´ll try all this ASAP.

---

