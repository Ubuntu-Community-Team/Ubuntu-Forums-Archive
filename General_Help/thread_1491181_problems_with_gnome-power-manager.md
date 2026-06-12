---
title: "problems with gnome-power-manager"
date: 2010-05-23
forum: General Help
---

### Post by miatawnt2b on 2010-05-23
My laptop won't suspend or hibernate after lucid upgrade, and after searching in the logs, I found this in /var/log/messages.

```

May 23 06:39:25 fred-MacBook gnome-session[1832]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
May 23 06:39:25 fred-MacBook gnome-session[1832]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
May 23 06:39:25 fred-MacBook gnome-session[1832]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files


```


If I try and run gnome-power-manager directly, I get the following errors.

```

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x25abc20'

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

(gnome-power-manager:2704): devkit-power-gobject-WARNING **: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

```

Any ideas how I can get this working?
-J

---

### Post by miatawnt2b on 2010-05-24
bump

---

### Post by wojox on 2010-05-24
Do you have a swap partition?

---

### Post by miatawnt2b on 2010-05-24
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       59805   480176944+  83  Linux
/dev/sda3           59805       60802     8003906+  82  Linux swap / Solaris

```

The interesting thing is that gparted lists the partitions as sda1, sda3, and sda4.  This machine used to have an sda2, though that partition was removed (under karmic) and the Linux partition was grown into its space.


I also noticed that power management preferences does not list a battery tab. Even if I boot without the charger, Ubuntu thinks it's on AC power.
 
-J

---

### Post by afrodeity on 2010-05-25
```
(gnome-power-manager:2311): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8a3a0e0'
```

I get the above .xsession error

---

### Post by wojox on 2010-05-25
You initially installed from a LiveCD and didn't do a Minimal Install correct?

Check this thread out [http://ubuntuforums.org/showthread.php?t=1471374](http://ubuntuforums.org/showthread.php?t=1471374)

---

### Post by miatawnt2b on 2010-05-27
Correct.  The orig install was a complete install from LiveCD.  Upgrade was through the net.
-J

---

