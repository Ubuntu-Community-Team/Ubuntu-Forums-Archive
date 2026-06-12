---
title: "Wired Keyboard and Mouse not working anymore"
date: 2012-08-20
forum: General Help
---

### Post by shade34321 on 2012-08-20
I recently upgraded from 11.10 to 12.04 and other than TwinView problems it seemed to be working. While trying to fix the TwinView issues, I rebooted the computer and the keyboard and mouse no longer worked. 

I can hit <kbd>F12</kbd> during boot to pick boot device but once the login screen hits neither work. When I `ssh` into the machine, `lsusb` shows that both the keyboard and mouse are seen. 

Any suggestions on getting them working?

After looking in the Xorg.0.log file I see this. 

[    60.280] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/event2)  
[    60.280] (II) No input driver specified, ignoring this device.  
[    60.280] (II) This device may have been added with another device file.  
[    60.280] (II) config/udev: Adding input device Logitech Optical USB Mouse (/dev/input/mouse0)  
[    60.280] (II) No input driver specified, ignoring this device.  
[    60.280] (II) This device may have been added with another device file.  
[    60.280] (II) config/udev: Adding input device Dell Dell QuietKey Keyboard (/dev/input/event3)  
[    60.280] (II) No input driver specified, ignoring this device.  
[    60.280] (II) This device may have been added with another device file.

---

