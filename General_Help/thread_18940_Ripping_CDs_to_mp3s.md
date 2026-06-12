---
title: "Ripping CDs to mp3s"
date: 2005-03-09
forum: General Help
---

### Post by jamin_l on 2005-03-09
Gone through the WIKI page: [here](http://www.ubuntulinux.org/wiki/RestrictedFormats)
Looked through the HowTos
Still getting errors.

Running Hoary.
Have the following packages installed: gstreamer0.8-mad, gstreamer0.8-lame, lame, w32codecs, totem-xine

When I try to rip a CD from SoundJuicer, I get this error: *Could not create GStreamer encoder ((null))*

When I try to work with Grip, first it didn't recognize my CD. Now I can't figure out where it's mounting my CDROM.
only place I can tell it should be is: /media/cdrom0 -- but when I open this folder it's empty.

This is the result of the command "mount" in term:
> 
/dev/hdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)


---

### Post by sysrq on 2005-03-09
[QUOTE=jamin_l]Gone through the WIKI page: [here](http://www.ubuntulinux.org/wiki/RestrictedFormats)
Looked through the HowTos
Still getting errors.

Running Hoary.
Have the following packages installed: gstreamer0.8-mad, gstreamer0.8-lame, lame, w32codecs, totem-xine

When I try to rip a CD from SoundJuicer, I get this error: *Could not create GStreamer encoder ((null))*

When I try to work with Grip, first it didn't recognize my CD. Now I can't figure out where it's mounting my CDROM.
only place I can tell it should be is: /media/cdrom0 -- but when I open this folder it's empty.

This is the result of the command "mount" in term:[/QUOTE]
 You don't mount CD's to rip them, the setting for the cd drive in grip should be the device name for your drive, IE /dev/hdc or something along those lines.

---

### Post by jamin_l on 2005-03-09
[QUOTE=sysrq]You don't mount CD's to rip them, the setting for the cd drive in grip should be the device name for your drive, IE /dev/hdc or something along those lines.[/QUOTE]

Which I think should be /media/cdrom0 - but when I entered that entry for it to look for the CD-ROM, then told it to rescan the disk, it didn't see a disc.

---

### Post by sysrq on 2005-03-09
[QUOTE=jamin_l]Which I think should be /media/cdrom0 - but when I entered that entry for it to look for the CD-ROM, then told it to rescan the disk, it didn't see a disc.[/QUOTE]
 /media/cdrom0 is a mount point not a device path, look in /etc/fstab and see what the device path is for that drive, it will be the first entry on that line.

---

### Post by jamin_l on 2005-03-10
[QUOTE=sysrq]/media/cdrom0 is a mount point not a device path, look in /etc/fstab and see what the device path is for that drive, it will be the first entry on that line.[/QUOTE]
 
Result for that appears to be /dev/hda/

---

### Post by jamin_l on 2005-03-10
Thanks very much. Working now :)

---

