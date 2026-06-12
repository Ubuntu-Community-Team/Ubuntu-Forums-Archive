---
title: "Using udev to mount USB storages in my home"
date: 2010-04-01
forum: General Help
---

### Post by uqbar on 2010-04-01
Hi all.
I would like to have my USB stoage devices to be mounted under my $HOME automatically when I insert them.
Those devices have been partitioned, formated with XFS and also given a UUID for this purpose.
I think I should use udev's rules and have also done some attempts like this one:

SUBSYSTEM=="usb", ENV{ID_FS_UUID}=="c195a25a-c03e-4cd8-9d86-9b9219acfeb4", OWNER="uqbar", GROUP="uqbar", RUN+="/bin/mount /dev/%k /home/uqbar/work"

Of course it doesn't work.
Is there any good hint?
I'm running Kubuntu 9.10 and Ubuntu 9.04 and would prefer a solution not tied to a specific desktop.
TIA.

---

### Post by kushal.kumaran on 2010-04-01
There's the usbmount package that seems to do what you need.  I haven't used it myself, though.

---

### Post by uqbar on 2010-04-01
> **kushal.kumaran said:**
> There's the usbmount package that seems to do what you need.  I haven't used it myself, though.

Where's the documentation?

---

### Post by uqbar on 2010-04-01
> **kushal.kumaran said:**
> There's the usbmount package that seems to do what you need.  I haven't used it myself, though.

Moreover:
> 
Warning: The original author does not have enough time any more to actively maintain the USBmount package. It is therefore currently unmaintained.


It looks like more difficult than trying the udev stuff myself.
Thanks anyway.

---

### Post by uqbar on 2010-04-01
It looks like I've found the solution with this udev rule:

KERNEL=="sdb*", SUBSYSTEMS=="scsi", ENV{ID_FS_UUID_ENC}=="c195a25a-c03e-4cd8-9d86-9b9219acfeb4", RUN+="/bin/mount /dev/%k /home/uqbar/work", RUN+="/bin/chown uqbar:uqbar /home/uqbar/work", RUN+="/bin/chmod 0750 /home/uqbar/work"

The only point is that under KDE v4.4.2 the mounted device doesn't show up either in the device notified widget or in the Dolphin file browser.

Later I'll check GNOME as well.

---

### Post by Aessa on 2010-04-05
In KDE4 under advanced system settings there is an Autostart option. This seems to be the GUI way to go. I am looking into this some more for myself soon.

---

### Post by theozzlives on 2010-04-05
In Ubuntu, all I need to do is plug a USB device in and it mounts.

---

### Post by KeyserSoze93 on 2010-04-05
> **theozzlives said:**
> In Ubuntu, all I need to do is plug a USB device in and it mounts.

Yes, but that's using the GUI. The method the user is talking about uses UDEV to mount shares regardless of the GUI running.

I've written a script which automates the process. It sets UDEV up to mount the device as the most recently logged in user, and if no user is logged in, it mounts as root.

It also disables HAL's usb stick mounting, which interferes with it. This works fine for GNOME and KDE3 - I've never run KDE4, so I don't know if it works with that.

[http://tpn.lowtech.org/scripts/fix_udev_hal.sh]("http://tpn.lowtech.org/scripts/fix_udev_hal.sh")

---

