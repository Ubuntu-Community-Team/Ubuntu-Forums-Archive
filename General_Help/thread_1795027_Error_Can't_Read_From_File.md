---
title: "Error: Can't Read From File"
date: 2011-07-01
forum: General Help
---

### Post by expphoto on 2011-07-01
I've had this happen twice. I get this after the grub screen (after I select which mode), it hangs, then says "error: can't read from file .... press any key to continue". I press a key, and it just sits there. 

I've tried two installs, it booted after the second, but once I activated the broadcom driver, it did it again. So I had to re-install, again.

This time around, does anyone have any idears on how to prevent that from failing again?

Thanks ya'll!

---

### Post by linuxuser12345 on 2011-07-01
It sounds like your wireless card is causing trouble with your system. Disable the broadcom, and try to install and enable the driver manually once logged in. You might need to use Ndiswrapper.
Restart.

---

### Post by expphoto on 2011-07-01
> **linuxuser12345 said:**
> It sounds like your wireless card is causing trouble with your system. Disable the broadcom, and try to install and enable the driver manually once logged in. You might need to use Ndiswrapper.
Restart.

What's amazing is, if I don't reboot, it works haha. 

Is there anyway I can create some sort of recovery image, so if it fails again, I'm not reinstalling, again. ?

---

### Post by linuxuser12345 on 2011-07-01
```
 $ sudo apt-get install dell-recovery 
```

---

### Post by expphoto on 2011-07-01
> **linuxuser12345 said:**
> ```
 $ sudo apt-get install dell-recovery 
```

Even though it's an HP?

---

### Post by linuxuser12345 on 2011-07-02
It should be fine! The program is made by Dell, even though it isn't made specifically for Dell computers, as I believe.

---

