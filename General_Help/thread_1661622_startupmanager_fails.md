---
title: "startupmanager fails"
date: 2011-01-06
forum: General Help
---

### Post by mjpatey on 2011-01-06
Hi, all-

Just installed "startupmanager" in order to control some of the variables having to do with GRUB.  Upon running the package, I get a tiny GNOME window saying "Performing pre-configuration tasks," along with the following terminal output:

> mjpatey@bunters:~$ startupmanager
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load
xrandr: Failed to get size of gamma for output default
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Grub2 detected
Usplash not detected
Splashy not detected
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
mjpatey@bunters:~$ 


...and it exits with the above error.

Any idea how to resolve this?  Thanks, all!

-Mark

---

