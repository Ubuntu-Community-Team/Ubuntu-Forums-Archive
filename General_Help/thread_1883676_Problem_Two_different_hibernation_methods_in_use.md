---
title: "Problem: Two different hibernation methods in use?"
date: 2011-11-19
forum: General Help
---

### Post by paaitken on 2011-11-19
I've searched this forum and Google to no avail.

Lenovo X61, Ubuntu 11.10, Gnome Shell, latest tuxonice kernel (but no hibernate-script), laptop-mode enabled on battery and set to manage auto hibernate on critical battery (HIBERNATE_COMMAND=/usr/sbin/pm-hibernate). I have it set to the same battery percentage values as the power manger in gsettings (managed through dconf-editor)

/usr/lib/pm-utils/defaults has HIBERNATE_MODE commented out, which means it uses kernel defaults. There are no extra configurations in /etc/pm/config.d/.

/etc/default/acpi-support has SUSPEND_METHODS="dbus-pm dbus-hal pm-utils", this has not been modified.

Hibernate and suspend work fine, both from the menu (Gnome shell extended status menu), and from the power button. Resume is fine too.

Here's the strange thing. If I hibernate via the menu or the power button, the screen locks, dims, and hibernates. Upon resume, I am asked for my password. This is how I like it.

However, if autohibernation is triggered by a critical battery level the screen does NOT lock, does NOT dim, it hibernates just fine. Upon resume it returns to the desktop with no password prompt! The same behaviour happens if I use $ pm-hibernate from the terminal.

Screen locks are disabled in dconf org>gnome>desktop>lockdown and in the all settings>screen gui. 

What gives? Are the menu and power buttons using a different hibernate method?

There's a bug report at RedHat [https://bugzilla.redhat.com/show_bug.cgi?id=698135#c8](https://bugzilla.redhat.com/show_bug.cgi?id=698135#c8) that describes a problem, I got to it from here [https://wiki.archlinux.org/index.php/GNOME#Screen_is_not_locked_after_resume](https://wiki.archlinux.org/index.php/GNOME#Screen_is_not_locked_after_resume).

However there are no screen locking options in dconf org>gnome>power-manager that I can see.

Anyone come across a solution to this yet?

Thanks in advance!

---

