---
title: "Automounting and 2.6.15.1"
date: 2006-02-23
forum: General Help
---

### Post by Skye on 2006-02-23
I recently upgraded to kernel 2.6.15.1 in order to avoid some acpi bugs I was having under the default 2.6.12-10-386 ubuntu kernel.  Unfortunately, after the upgrade, gnome's automounting capibilites no longer work as expected.

For example, under the old kernel, when I plugged in a USB drive or cd/dvd disk, gnome would recognize whatever it is, and mount it for me, an icon for the drive would appear both on the desktop and in the "Computer" window on the places menu, and I would be able to browse the media.

But now, when I plug in a cd, dvd, or usb drive, nothing appear to happen- no automount, no icon on the desktop or under "Computer."  But, the device still mounts.  If it go to /media/usbdisk or /media/cdrom0, I can see the contents of whatever is plugged in.  Furthermore, the "Removable Drives and Media" menu in System -> Prefrences changes whether or not the drive is actually mounted- when turned on, the drive mounts, but gnome doesn't see it as mounted; when turned off, nothing at all happenes.

The last thing that's screwy is if I click on the "Disk Mounter" panel applet to mount either the cd or usb drive after pluggin it in, I get the following errors:

(Usb drive)

Unable to mount the selected Volume.
Error: Device /dev/sda1 is already mounted to /media/usbdisk
Error: Could not execute pmount

(CD/DVD disk)

Unable to mount selected volume.
Warning: Device /dev/hdc is already handled by /etc/fstab, supplied label is ignored.
mount: block device /dev/hdc is write protected, mounting read-only
mount: /dev/hdc is already mounted or /media/cdrom0 busy
mount: acording to mtab, /dev/hdc is already mounted on /media/cdrom0
Error: could not execute pmount

I suspect I did something wrong when recompiling the kernel, but the fact that it still works, if only partically, is very confusing to me.

Has anyone ever encountered this or a similar problem?  Does anyone have any idea how to fix it?  Thanks!

---

### Post by GTvulse on 2006-02-23
[quote=Skye]I recently upgraded to kernel 2.6.15.1 in order to avoid some acpi bugs I was having under the default 2.6.12-10-386 ubuntu kernel. Unfortunately, after the upgrade, gnome's automounting capibilites no longer work as expected.
[/quote]

That's unavoidable. The kernel (as of 2.6.14) has abandoned hotplug and moved the functionality to udev. Breezy's version of udev is not up-to-date enough to work properly with the new kernel events.

On mounts showing up on the desktop, gnome is also at fault there. In Dapper, icons are not showing up. I do hope that will be fixed soon enough before official release.

---

### Post by Skye on 2006-02-23
Ah, ok.  Would it be possible to upgrade udev, or would doing that just cause breakage and headaches?

---

### Post by GTvulse on 2006-02-24
[QUOTE=Skye]Ah, ok.  Would it be possible to upgrade udev, or would doing that just cause breakage and headaches?[/QUOTE]
It is more bother and causes more breakage than you would probably be willing to afford. Dapper is very stable now and will be more and more each day since feature freeze went into effect last weekend. I'd use it instead of Breezy in your case.

---

