---
title: "plugging in a firewire drive"
date: 2006-01-28
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-01-28
hello again...

...i gave up on the whole server install/sudo apt-get install kdm kde-core thing, and installed kubuntu 5.10 from the cd... it looks good so far, except when i plug in my firewire hard drive (through a dynex pcmcia firewire card), konqueror pops up with a message that says "An error occurred while loading media:/sda1:
The file or folder media:/sda1 does not exist."

i opened the terminal and tried ```
mount /dev/sda1
```but it said "according to mtab, /dev/sda1 is already mounted on /media/ieee1394disk."

so then i went back to konqueror and typed "/media/ieee1394disk" into the address bar, and there was my hard drive!

i realize that merely recognizing an external disk is far more than other distributions could ever hope to accomplish out of the box, but it's annoying when konqueror automatically pops up the wrong folder (/media/sda1 instead of /media/ieee1394disk).

can someone help me change this...?

thanks.

---

