---
title: "Please HELP!!! - No Mouse!!"
date: 2010-07-11
forum: General Help
---

### Post by iexplorer on 2010-07-11
Please help me. I have Xubuntu amd64 installed on my acer 1810t laptop. I made it work, and I attached my USB Dell optical mouse. After that I have no more touchpad (Synaptics touchpad) in Xubuntu, I rebooted many times and I found, taht I have no more touchpad in Windows and no more touchpad in LiveCDs.  I supposed may be some part of my H2O bios was modified by Xubuntu???  What is happened? Please help me!

---

### Post by Penguin Guy on 2010-07-11
Your touchpad may be broken, have you tried it with another computer?

---

### Post by iexplorer on 2010-07-12
Hi. No it was not broken. Finaly I found the solution.   I activated xorg.conf and puted there the lines about both mouses Dell and Synaptics touchpad. It did not work. So after that I reinstalled my bios from backup, and it works now with both the mouse and the touchpad.  So, I can say that Xubuntu (may by *buntu) change bios settings on this laptop (Acer 1810t). I do not know why and how, but it was changed.   I have one more issue, I can not change value in /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor. I have put  echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor echo conservative > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor in my /etc/tc.local, but it did not work. At the same time a line with /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq   changed value perfectly. I do not know why.

---

