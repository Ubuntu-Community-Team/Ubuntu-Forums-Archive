---
title: "firefox crashes the system, then it cannot detect a hard drive"
date: 2011-09-03
forum: General Help
---

### Post by wirrr on 2011-09-03
I was using firefox for quite some time, then it started crashing my system. Eventually the system would crash as soon as you tried to start firefox. When it crashed, the system stopped detecting the hard drive. Ctrl+Alt+SysRq was required to reboot, and after rebooting the computer still did not detect a hard drive. After cold booting it was fine.
I purged the partition of the firefox package, deleted ~/.mozilla, and then reinstalled from the repository. Now it does not crash the system when it starts, but after a short while it does, in the same way.
Once when it crashed, I copied the error messages from the terminal by hand. It was basically like this: 

java version "1.6.0_22"
(3 lines, appears to be working OK)

(<unknown>:2120): Gtk-CRITICAL **: IA_gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed

(<unknown>:2120): Gtk-CRITICAL **: IA_gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed

(firefox-bin:2024): LIBDBUSMENU-GTK-CRITICAL ***: dbusmenu_menuitem_property_set_shortcut: assertion 'gtk_accelerator_valid (key, modifier))' failed
(firefox-bin:2024): LIBDBUSMENU-GTK-CRITICAL ***: dbusmenu_menuitem_property_set_shortcut: assertion 'gtk_accelerator_valid (key, modifier))' failed
(firefox-bin:2024): LIBDBUSMENU-GTK-CRITICAL ***: dbusmenu_menuitem_property_set_shortcut: assertion 'gtk_accelerator_valid (key, modifier))' failed

java version "1.6.0_22"... (same thing)

(<unknown>:2120): Gtk-CRITICAL **: IA_gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed

(<unknown>:2120): Gtk-CRITICAL **: IA_gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed


Some people have suggested a hardware problem. However, I started using Chromium and there is no problem. Windows Vista is installed on the same system, and it does not crash.

---

### Post by sanderj on 2011-09-03
... and your question is ... ?

---

### Post by wirrr on 2011-09-03
Why did Firefox start crashing the system? Is it just hogging resources? Why does it not detect the hard drive, even after reboot? Is there a way to get Firefox up and running again? What do the error messages tell you?

---

### Post by jonovanbelle on 2011-09-03
Hi! 
I had the exact same problem with my computer (and it was getting worse), searched on fora and many suggested hard drive problem because it said something like this: 

[various changing numbers] ata1.01: status: {DRDY ERR} [various changing numbers] ata1.01 ERROR: {unc}
Removed Firefox now and computer seems to be starting up immediately without any errors. 
Anyway, thanks for your post, it helped me.

---

### Post by sanderj on 2011-09-04
> **wirrr said:**
> Why did Firefox start crashing the system? Is it just hogging resources? Why does it not detect the hard drive, even after reboot? Is there a way to get Firefox up and running again? What do the error messages tell you?

I would run memtest86 (it's in the Ubuntu boot menu) for a few hours, and see what it says.
I don't think firefox can cause a drive not to be seen. It could be the other way around: drive problem => firefox (or OS) crashes => reboot => drive still not seen.
On a running system, you can have a look at /var/log/syslog.
And you can check the status of your harddisk with SMART-tools, see [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

In the meantime, use Chrome instead of Firefox.

Summary: memtest86, SMART-tools, Chrome.

---

### Post by wirrr on 2011-09-04
sanderj, thank you.

---

### Post by lovinglinux on 2011-09-05
Try to disable Global Menu Bar Integration extension in Firefox.

---

