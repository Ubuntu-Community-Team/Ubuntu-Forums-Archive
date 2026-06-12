---
title: "Xubuntu won't work."
date: 2012-07-06
forum: General Help
---

### Post by PatrickSK on 2012-07-06
So, I tried to install xubuntu seemed to work fine, I restarted my computer and it loads up fine, but when xubuntu was done loading it just looked like this:

[http://i.imgur.com/OIQ4m.jpg](http://i.imgur.com/OIQ4m.jpg)
(Sorry for picture quality) 

Note: My windows 7 still works fine.

I don't know if there's something wrong with my graphics card..If there is my graphics cards spec is:

Amd Radeon HD 6410D

(Sorry for bad english, i'm from Denmark.)

-Patrick

---

### Post by Merrattic on 2012-07-06
What do get if you press```
CTRL+ALT+F2 (or F1)  ?
```

Should be a command line login prompt. Login and from there you should be able to diagnose your graphics problem. Not sure what the immediate fix is for an ati card but am sure someone will chip in....

---

### Post by PatrickSK on 2012-07-06
Just tried only kinda error I could see was this:

phy0 -> rt2800pci_mcu_status: Error - mcu request failed no response from hardware

---

### Post by Merrattic on 2012-07-06
You need to start with your /var/log/Xorg.0.log

---

