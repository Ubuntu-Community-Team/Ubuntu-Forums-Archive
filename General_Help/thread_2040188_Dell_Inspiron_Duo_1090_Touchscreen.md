---
title: "Dell Inspiron Duo 1090: Touchscreen"
date: 2012-08-10
forum: General Help
---

### Post by aligozukara on 2012-08-10
hi,
firstly sorry for my bad english. &#305; write from turkey
&#305;'m very neew on ubuntu.
&#305; have &#305;nstalled ubuntu 12.04 on dell inspiron duo 1090
but my touchscreen and accelerator dosn't work
&#305; read every forums but &#305; can't find
please help me step by step to installing the drivers
thanks

---

### Post by aligozukara on 2012-08-10
hi,
firstly sorry for my bad english. &#305; write from turkey
&#305;'m very neew on ubuntu.
&#305; have &#305;nstalled ubuntu 12.04 on dell inspiron duo 1090
but my touchscreen and accelerator dosn't work
&#305; read every forums but &#305; can't find
please help me step by step to installing the drivers
thanks

---

### Post by johnathansmith on 2012-08-10
Hi, try this. It's for 11.10 but should also work for your release 
[Topic]("http://ubuntuforums.org/showthread.php?t=1628232&page=8")
```
Login and open termina
Type sudo gedit /etc/default/grub
find the line that says 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0x0eef:0x725e:0x40"

Save and close geditor. 
Run sudo update-grub
Reboot.. Everything is working 

```

You should also look [here = calibration of touchscreen under 12.04 ubuntu]("http://thefanclub.co.za/how-to/how-ubuntu-1204-touchscreen-calibration")

---

### Post by aligozukara on 2012-08-11
thank you but now is a new problem;
the touchscreen work only 1 minutes. after then stopped working. &#305; had calibrated.
and accelerator dosn't work. please help me step by step

---

