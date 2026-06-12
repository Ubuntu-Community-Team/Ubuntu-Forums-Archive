---
title: "cannot save xserver settings"
date: 2010-12-26
forum: General Help
---

### Post by aspiring geek on 2010-12-26
hi, i use a system whose configuration is AMD64 3000+, 512mb RAM, Gigabyte motherboard with nvidia 6100 chipset. I installed Ubuntu 10.04 LTS with windowsxp. The graphics driver is a third party driver from nvidia. now if i make changes in the xserver settings and save the file in default location it does not boot in the same setting next time.
Also is there a driver out there for my HP 2050 inkjet mfd? Thanx

---

### Post by efflandt on 2010-12-27
NVidia settings are in 2 places.  **/etc/X11/xorg.conf** has general system settings.  And specific personal settings are in **~/.nvidia-settings-rc**

It could be that settings in your ~/.nvidia-settings-rc are overriding what you are trying to set in xorg.conf.

---

### Post by Stainesy on 2010-12-27
I suspect you need to adopt root privileges temporarily to save the settings.

---

### Post by aspiring geek on 2010-12-27
well, is there a way to rectify that? Thanks for responding so promptly. My first time on any forum and it is already turning out to be a pleasant one. Thanks

---

### Post by aspiring geek on 2010-12-27
I did that but it doesn't help.

---

### Post by tredegar on 2010-12-27
Run nvidia-settings from your GUI
Configure it the way you want.
In left pane, click NV- settings Config
click Save current config
Accept the default name and location in your home dir.

Make a script:

```
#!/bin/bash
# reload the nv settings
nvidia-settings -l
```

Save it somewhere, Make it executable, and autostart at login.

You should be done.

---

### Post by tredegar on 2010-12-27
For your printer go [here]("http://www.openprinting.org/printers")
If it's a "HP 2050 Business Inkjet" then it looks like it is supported (& why I *always* buy HP) by the **hplip** driver (in the repositories, just install it with the package manager) and **cups** (already installed).

Then it's just a matter of plugging in the printer, System, Admin, Printing, Add Printer and following your nose.

Get back with specific details if you have problems.

---

