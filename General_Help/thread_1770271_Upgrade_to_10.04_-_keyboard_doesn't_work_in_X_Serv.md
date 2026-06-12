---
title: "Upgrade to 10.04 - keyboard doesn't work in X Server"
date: 2011-05-29
forum: General Help
---

### Post by vvd416 on 2011-05-29
After I finished upgrading Xubuntu from 9.10 to 10.04, I discovered that my keyboard stopped working in X Server. The upgrade process was running smoothly until the last moment, when it produced some error, which I, unfortunately, did not write down. 

Anyway, the upgrade has completed; uname shows kernel version 2.6.32-31. Now the keyboard works fine if I select a recovery mode at startup, but if I type 'start gdm' from the shell or select the default option in GRUB while booting, the keyboard becomes unavailable right from the login screen. I can log on using the virtual keyboard, but that's all I can do; the keyboard is still dead.

In the Xorg.0.log I found the following piece, which might be relevant to the case:

(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching `kbd'

Attached is the complete log file.

My questions are:
- Is this issue known? 
- If yes, then is there any way of enabling the keyboard in GUI without reinstalling the system?

---

### Post by Toz on 2011-05-29
Do you have **xserver-xorg-input-evdev** installed? You can check by opening a terminal window and typing in```
apt-cache policy xserver-xorg-input-evdev
```

Can you also post back the contents of your /etc/X11/xorg.conf file?

---

### Post by vvd416 on 2011-05-29
Thank you very much for reply.
Attached are the output of the command and the xorg.conf file. 
Please let me know if I can help you with any other piece of information.

---

### Post by Toz on 2011-05-29
In your xorg.conf file, comment out the AutoAddDevices option like this:```
#    Option         "AutoAddDevices" "False"
``` and try again.

---

### Post by vvd416 on 2011-05-29
Thank you ever so much.
It works like a charm; keyboard has been enabled.

---

### Post by Toz on 2011-05-29
You're welcome. If you don't mind, can you please mark this post as solved? (Thread Tools->Mark This Thread As Solved). Thanks.

---

