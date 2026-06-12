---
title: "Fix for nvidia and brightness control under 10.10"
date: 2011-01-04
forum: General Help
---

### Post by ikiini on 2011-01-04
I searched a bit and did not find this solution on the forum. So thought i'd add it seeing that i had a bit of trouble getting this to work nice. 

Problem:
I could not change the brightness of my lenovo thinkpad backlight using the hot keys, or the slider in the power management. to get it to work, i would have to change it. the restart x to see the change. Using acpi_listner, i saw that the events were being registered but not effect on brightness. I would also see the graphic indicating that brightness was changing but again, no effect on actual brightness. 


Fix:
take from [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/588877](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/588877). 

to your xorg.conf (/etc/X11/xorg.conf) append to the Device section

Option "RegistryDwords" "EnableBrightnessControl=1"'

then restart X.

Hopefully this helps someone out there.

cheers,

-B

---

