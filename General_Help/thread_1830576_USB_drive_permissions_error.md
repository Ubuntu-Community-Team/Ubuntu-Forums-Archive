---
title: "USB drive permissions error"
date: 2011-08-21
forum: General Help
---

### Post by stafio on 2011-08-21
I have two users set up on my system, both using KDE. When a USB thumb drive is plugged in, User_1 can pick the action "Open with File Manager" and will be taken to dolphin with a view of the files/directories on the device.

For User_2, clicking "Open with File Manager" results in a message coming up at the bottom of the "Available Devices" popup that says "Could not mount the following device: KINGSTON". Note that the issue happens with other USB drives and SD Cards, so the issue is not with the specific card.

Both of these users are members of the same groups. I'm stumped as to what could possibly be preventing one user from getting into the USB disk devices.

Running: Natty, 64-bit

---

### Post by stafio on 2011-09-18
I should also mention that opening Dolphin first and clicking on the usb drive there would display the eror: > org.freedesktop.udisks.error.permissiondenied

I finally found a fix for this issue, thanks to [srejbi in this other thread]("http://ubuntuforums.org/showpost.php?p=9414308&postcount=21"). 

The solution was to edit the file: /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

Original Contents:
> [Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin
Action=org.gnome.clockapplet.mechanism.*;org.kde.kcontrol.kcmclock.save
ResultActive=yes

#[Disable hibernate by default]
#Identity=unix-user:*
#Action=org.freedesktop.upower.hibernate
#ResultActive=no

Added the following 2 lines after the mounting section's ResultActive=yes line:
> ResultAny=auth_admin
ResultInactive=yes

---

