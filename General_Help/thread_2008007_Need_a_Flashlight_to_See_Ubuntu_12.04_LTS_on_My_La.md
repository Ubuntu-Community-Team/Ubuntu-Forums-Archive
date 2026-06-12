---
title: "Need a Flashlight to See Ubuntu 12.04 LTS on My Laptop Screen"
date: 2012-06-21
forum: General Help
---

### Post by Ruination2 on 2012-06-21
Hi experts,

I'm fed up with Windows 7 on my Acer eMachines  E527-2537, so I did an ISO image CD installation of Ubuntu 12.04 LTS.  The installation program ran fine, except it was so dark, I literally  had to shine a flashlight on my screen to see what I was doing. It seems  that the installation was successful, except it's unusably dark. 

Any ideas?

Thanks.

---

### Post by papibe on 2012-06-21
Hi Ruination2. Welcome to the forums!

Try adjusting the brightness setting by opening 'System Settings' and selecting 'Brightness and Lock'.

Tell us how it goes.
Regards.

---

### Post by Ruination2 on 2012-06-21
Thanks for the quick response, papibe. 

Unfortunately, it didn't work. Ubuntu is still running way too dark to see without a flashlight.

---

### Post by alphacrucis2 on 2012-06-21
Might be worth trying to install the proprietary graphics driver if available for your machine via additional drivers.

---

### Post by Ruination2 on 2012-06-21
> **alphacrucis2 said:**
> Might be worth trying to install the proprietary graphics driver if available for your machine via additional drivers.

Thanks, alphacrucis2. But I'm not sure how to go about doing that.

---

### Post by black veils on 2012-06-22
there is an application on the system, called Additional Divers, it is easy to use.

have you tried pressing the keyboard shortcuts for screen brightness? adjust it, then restart computer.

---

### Post by MegaTherion on 2012-06-22
Try adding the following to the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub

```
acpi_backlight=vendor
```

Afterwards run:

```
sudo update-grub
```

Reboot

---

