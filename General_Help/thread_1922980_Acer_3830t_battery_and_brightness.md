---
title: "Acer 3830t battery and brightness"
date: 2012-02-09
forum: General Help
---

### Post by portermiked on 2012-02-09
it took me ages to figure out how to get brightness to work, figured i would post successful results of lots of hunting.

1) ctrl + alt + T, to open terminal 
2) type : **sudo -s** (to get root access)
3) type : **gedit /etc/default/grub** (to launch your grub bootup file)
4) where it says **GRUB_CMDLINE_LINUX_DEFAULT=**, in the quotes put **quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1**
5) on the next line where it says **GRUB_CMDLINE_LINUX=**, put **acpi_backlight=vendor** in the quotes.
6) save the file.
7) update grub with **sudo update-grub**

reboot.

[http://ubuntuforums.org/showthread.php?t=1859945](http://ubuntuforums.org/showthread.php?t=1859945)

follow his instructions to install jupiter and run lm-sensors.

not sure who this will help but the brightness issue took AGES to figure out and hopefully this will save some hair :)


also, REALLY wish i could edit tags cause i dunno bout you but when i google its by model # : /   i understand the abuse issue but you know lol

---

