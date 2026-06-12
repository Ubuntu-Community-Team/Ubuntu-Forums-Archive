---
title: "New to Ubuntu: Problems with Sleep Time and Brightness"
date: 2012-09-23
forum: General Help
---

### Post by ashwin1729 on 2012-09-23
I have been having a couple of issues with New Ubuntu 12.04 installation...firstly, my brightness was flickering and I could not do anything with the laptop unless I restarted it.
I went online and searched for it and found this

Sudo gedit /etc/default/grub[INDENT] GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" [/INDENT] Changed it to:
 [INDENT] GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" [/INDENT]sudo update-grub


now i do not have the brightness flicker, but the problem is the brightness seems to be set at a level 2 and i can not increase or decrease it...when the laptop is charging, however the brightness is automatically increased to full level...can any one help me please?


also,


in the power settings, even though i increased the suspend time from 10 mins to 30 mins, the computer keep suspending at 10 mins...a solution to this also would help..




Laptop Specs: 

Samsun Laptop
I3 second generation processor
Intel HD 3000 graphics..
4 Gb ram

---

