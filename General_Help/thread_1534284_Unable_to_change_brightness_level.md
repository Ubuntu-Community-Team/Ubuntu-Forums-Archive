---
title: "Unable to change brightness level"
date: 2010-07-19
forum: General Help
---

### Post by partyhard on 2010-07-19
Hi. I'm using Ubuntu 10.04 64 bit on by t510 and can't change the brighness level. The gui for the brightness level appears but it doesn't actually change the brightness on my screen. I heard that using nvclock would fix the problem (using nvclock -S -(or +) 5 as a command) but that doesn't work either. Apparently it's because my nvidia card is too new (nvidia nvs3100m). 

Anyone know how to fix this?

---

### Post by oustiti on 2010-07-20
You can probably set it from the command line (and create a desktop link to do it) or look in to remapping your function keys.

I'm not sure for your modelf but if you dig in /proc/acpi/ you should be able to find some sort of video control and a brightness setting.

Then you can do something like this :

echo -n 50 > /proc/acpi/video/VGA/LCD/brightness

which would set it to 50% brightness.

---

### Post by partyhard on 2010-07-20
Ok... 

By searching the web I found two methods that supposedly fix the problem:

1) Append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the  Device-Section of xorg.conf. This works but when I lower the brightness  my computer starts making a high pitched noise (similar to cpu whining  which I have when on battery or using my usb ports).

2) Disable vt-d from bios.

I have no idea how to do 2). Anybody here knows?

---

### Post by cherep on 2010-09-03
maybe this will help
[http://ubuntuforums.org/showthread.php?t=1503569](http://ubuntuforums.org/showthread.php?t=1503569)

---

### Post by mirzmaster on 2011-01-10
> **partyhard said:**
> Ok... 

By searching the web I found two methods that supposedly fix the problem:

1) Append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the  Device-Section of xorg.conf. This works but when I lower the brightness  my computer starts making a high pitched noise (similar to cpu whining  which I have when on battery or using my usb ports).

2) Disable vt-d from bios.

I have no idea how to do 2). Anybody here knows?

Thank you!  The xorg.conf modification worked for my Lenovo T510 with Nvidia NVS 3100M.

---

