---
title: "Disabling USB Auto-suspend?"
date: 2011-06-02
forum: General Help
---

### Post by aquarys on 2011-06-02
Hello,

I foolishly disregarded the inner me telling me to check on the Internet before configuring anything and enabled the USB auto-suspend Powertop recommends. Now my mouse needs to be clicked once before being deemed active by my computer. Apparently I can configure it by editing something in this directory /sys/class/usb/device/*/device/power/level (according to [this]("http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg00398.html")) but I can't find that directory. What can I do to fix this? 

Thanks

---

### Post by Ev1L on 2011-06-18
same problem here

---

### Post by Sorseg on 2011-07-13
Same thing. Bumping

---

### Post by Erik1984 on 2011-07-13
> **Sorseg said:**
> Same thing. Bumping

Did it too... it said non-input devices but I shoud've checked more. It should be not so hard to turn autosuspend off again. Just don't know how yet, googling in process. 

edit: The correct path seems to be:
```
/sys/bus/usb/devices/yourdevice
```
where your device is in my case usb4, depends on the bus the mouse is connected to. then tere is the power folder and the level file. however it is read-only for all users, even for root. so echoing stuff to that file does not work. Strange enough the mouse seems to behave normal again, but I haven't changed anything.

---

