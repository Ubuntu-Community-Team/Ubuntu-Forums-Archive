---
title: "File transfer never ends in Karmic"
date: 2009-11-22
forum: General Help
---

### Post by ZeldaFan on 2009-11-22
When I am transferring a file from my HDD to an external media device, like an SD card or my mp3 player, the nautilus file operations window opens showing the progress of the transfer, as usual. However, once the bar hits the ends (as if the file transfer should be complete), it just hangs there and doesn't do anything or disappear like it should. The only way to stop it is to force quit it, but then I am not even sure if its fully transferring my files. Anyone know what the problem is?

---

### Post by khelben1979 on 2009-11-22
Since the transfer is made through the usb port, you should be able to track the process. In doing this you will always know if the transfer has been done or not.

Type in
```
top
```
from a text terminal and take a look at the processes which uses your cpu the most and you should find this process. If the process isn't there, the file transfer is done.

Also, if you're concerned about this, I understand it's gnome related and so maybe you should try KDE instead to see if it works better from there?

---

