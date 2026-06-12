---
title: "where to set X driver?"
date: 2012-07-13
forum: General Help
---

### Post by yuanzhoulu on 2012-07-13
Upgraded to 12.04 recently. My xorg.conf is blank! All there is is some

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

Where do I change the setting to change between nvidia and noveau? I don't want to do any uninstalls, just want to switch between them freely.

thanks

---

### Post by Toz on 2012-07-13
Configuration directives are now stored in /usr/share/X11/xorg.conf.d

See: [https://wiki.ubuntu.com/X/Config/]("https://wiki.ubuntu.com/X/Config/")

---

### Post by Rexilion on 2012-07-14
And beware, freely switching is not possible.

You have to make sure of the following area's before/after switching:

Make sure that the default 3D library's  match the correct driver.
- update-alternatives --list i386-linux-gnu_gl_conf
- update-alternatives --list i386-linux-gnu_egl_conf
Make sure that the correct kernel modules are loaded/unloaded:
- lsmod

You cannot combine kernel modules and 3D library's across nouveau and nvidia.

---

### Post by markbl on 2012-07-14
I've been switching from nouveau to nvidia with a simple "sudo aptitude install nvidia-current" + reboot. Switch back to nouveau with "sudo aptitude purge nvidia-current" + reboot.

---

