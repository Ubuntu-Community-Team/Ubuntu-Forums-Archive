---
title: "Can't see mountpoints on xserver"
date: 2010-07-08
forum: General Help
---

### Post by braiamp on 2010-07-08
I'm opening this thread following the topic forum organization. The original thread are on [http://ubuntuforums.org/showthread.php?p=9557636](http://ubuntuforums.org/showthread.php?p=9557636).

As above described, I changed all my system root to bind user and getting back to root. But a consequence of that are vary and maybe take some time to get resolved, but the topic of the thread is:

I can't see the mount points on Places for all my drives (included HDD, CD/DVD and USB's). I doesn't use mkdir + mount strategies, because, I had some estrange troubles with, about that later, when I want to use the front end the drives don't mount where is expected. Ex.:
Graphical: Click on Places > Filesystem 1GB = mounted on /media/MYBRAND
on terminal: mount /dev/hda1 /media/usbstick = mounted on /media/usbstic
Graphical: Click on Places > Filesystem 1GB = mounted randomly on /media/usbstick or /media/MYBRAND or doesn't mount.

---

### Post by braiamp on 2010-07-11
Well, I maybe have to change the way that want the answer that I´m   looking for make my system work as expected.
Some of the device files, configuration files, binary link, library or   anyelse that should be in a exact uid, user or group owned? I attach the   last list of the package that I have installed to build my entire   system with apt-build but didn't do for time and energy reasons, on my   HP Pavilion a1104x.

Here is how my system have set the users and groups:
/dev/* = root
/etc/* = root, included Xorg and gdm folder
/*bin = root
/usr/*bin = root
/usr/* = root
/home/* = his respective users and /home by root
/var/log = the syslog user and the user especific for each log file
/var/* = root
/lib/udev = root, maybe it would have another user but yet I don't know
/lib/security = root
/lib/* = root
/* = root
everyelse don't listed = root

Any help would be apreciated.

---

### Post by braiamp on 2010-07-11
I forget it, the attachment.

---

### Post by braiamp on 2010-07-11
Resolved by myself. When I figured out what the init line /usr/lib/gnome-disk-utility/gdu-notification-daemon do, I try to get (in my root user) to run it, i get:

```

root@braiam-desktop:~# /usr/lib/gnome-disk-utility/gdu-notification-daemon

(gdu-notification-daemon:1364): libgdu-WARNING **: Couldn't get daemon properties
======================================================================
Error constructing GduPool: (unspecified error)

This error suggests there's a problem with your udisks or D-Bus installation.
======================================================================

(gdu-notification-daemon:1364): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:1364): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:1364): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:1364): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:1364): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:1364): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gdu-notification-daemon:1364): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gdu-notification-daemon:1364): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
**
libgdu:ERROR:gdu-pool.c:2459:gdu_pool_get_devices: assertion failed: (pool != NULL)
Cancelado
root@braiam-desktop:~# 

```So as said at start udisks or udev have the problem for what I do:
root@braiam-desktop:~# dpkg-reconfigure udisks dbus

---

