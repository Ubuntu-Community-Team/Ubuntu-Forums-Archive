---
title: "nVidia Driver Not Persistant"
date: 2009-09-22
forum: General Help
---

### Post by Echo35 on 2009-09-22
Recently, I obtained a new laptop. After installing Windows 7 on the main hard drive, I set up an Ubuntu install on my Jump Drive from PenDriveLinux. It works wonderfully and all, but I have two glaring issues. The first being that it does not save my system clock time zone. The clock is correct, but it constantly defaults to UTC, no matter how many times I set it to EST (This is after a reboot by the way). The other problem I'm having is my nVidia drivers. They work fine, but they do not persist. Every time I boot my laptop, I have to first log into terminal, run nvidia-xconfig, and then log back in normally. If I just boot it, it doesn't use the driver. Its almost as if my xorg.conf file isnt saving after reboot. Is there any way to fix this?

---

### Post by marshmallow1304 on 2009-09-22
Try running the nVidia GUI as root:
```
gksudo nvidia-settings
```

Then set up the settings as you like under "X Server Display Configuration", apply, and make sure to click "Save to X configuration file".

---

### Post by Darkwing-Duck on 2009-09-22
If you want and/or need help setting up your Nvidia drivers I would suggest this HowTo. 

[http://gwos.org/udsf/doku.php/hardware:nvidia](http://gwos.org/udsf/doku.php/hardware:nvidia)

Let us know if you have questions from that.

---

