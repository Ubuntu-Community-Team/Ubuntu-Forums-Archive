---
title: "System settings crash"
date: 2011-10-18
forum: General Help
---

### Post by itix on 2011-10-18
I think that the system settings is the gnome-control-center but I am not sure.

Anyway, I accidentally changed my UI to HighContrast (wanted to switch back to radiant since I didn't like the bright one, whatever it is called) and the entire x-session crashed and restarted. After that I can not start system settings anymore and my .x-session-errors is full of gnome-control-deamon output about half my computer missing :/

> (gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/product_name: Failed to open file '/sys/class/dmi/id/product_name': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_name: Failed to open file '/sys/class/dmi/id/board_name': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/product_version: Failed to open file '/sys/class/dmi/id/product_version': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_version: Failed to open file '/sys/class/dmi/id/chassis_version': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_version: Failed to open file '/sys/class/dmi/id/board_version': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/sys_vendor: Failed to open file '/sys/class/dmi/id/sys_vendor': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_vendor: Failed to open file '/sys/class/dmi/id/chassis_vendor': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_vendor: Failed to open file '/sys/class/dmi/id/board_vendor': No such file or directory
(gnome-settings-daemon:1052): color-plugin-WARNING **: failed to get edid: unable to get EDID for output


---

