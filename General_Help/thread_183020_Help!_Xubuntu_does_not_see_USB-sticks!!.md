---
title: "Help! Xubuntu does not see USB-sticks!!"
date: 2006-05-27
forum: General Help
---

### Post by DoktorNo on 2006-05-27
I have serious problem with my Xubuntu: it doesn't show my USB stick in /media, like in "normal" Ubuntu GNOME. AFAIK automounting is handled idependetnly from window menager. BTW: the same thing is with external DVD-ROM: the burning software (graveman) is seeing this as burning device.
Fstab is looking like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
And mtab is like this:
```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-9-386/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

```
Really wired stuff!

---

### Post by Sutekh on 2006-05-27
Try installing the [gnome-volume-manager]("http://packages.ubuntu.com/breezy/gnome/gnome-volume-manager")
```

sudo apt-get install gnome-volume-manager
``` This handles automounting in GNOME.  

Or [ivman](http://packages.ubuntu.com/breezy/utils/ivman) (less GNOME dependancies)
```
sudo apt-get install ivman
```

---

### Post by DoktorNo on 2006-05-27
Or [ivman]("http://packages.ubuntu.com/breezy/utils/ivman") (less GNOME dependancies)
```
sudo apt-get install ivman
```[/quote]
I have ivman already installed. I have run it in Terminal, and it gave me some feedback abiut mounting external DVD ("mount: block device /dev/scd0 is write-protected, mounting read-only
"), DVD is now visible as /media/cdrecorder but i cannot still see my USB stick.

---

### Post by Sutekh on 2006-05-27
Is it recognised by Ubuntu?

Use this code in a Terminal Window (Applications -> Accessories Menu)
```
tail -f /var/log/messages
```
Then plug in your USB stick.  Take note of the output.  Does it seem like the USB is detected?

---

### Post by DoktorNo on 2006-05-27
[quote=Sutekh]Is it recognised by Ubuntu?

Use this code in a Terminal Window (Applications -> Accessories Menu)
```
tail -f /var/log/messages
``` Then plug in your USB stick. Take note of the output. Does it seem like the USB is detected?[/quote] It gives me this:
```
May 27 14:55:11 localhost kernel: [4299304.861000] usb 1-2: new full speed USB device using uhci_hcd and address 5
May 27 14:55:11 localhost kernel: [4299304.972000] scsi3 : SCSI emulation for USB Mass Storage devices
May 27 14:55:11 localhost usb.agent[7800]:      usb-storage: already loaded
May 27 14:55:16 localhost kernel: [4299309.980000]   Vendor:           Model: USB Flash Memory  Rev: 1.04
May 27 14:55:16 localhost kernel: [4299309.980000]   Type:   Direct-Access                 ANSI SCSI revision: 00
May 27 14:55:16 localhost kernel: [4299310.264000] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
May 27 14:55:16 localhost kernel: [4299310.267000] sda: Write Protect is off
May 27 14:55:16 localhost kernel: [4299310.287000] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
May 27 14:55:16 localhost kernel: [4299310.290000] sda: Write Protect is off
May 27 14:55:16 localhost kernel: [4299310.290000]  /dev/scsi/host3/bus0/target0/lun0: p1
May 27 14:55:16 localhost kernel: [4299310.302000] Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
May 27 14:55:16 localhost kernel: [4299310.306000] Attached scsi generic sg0 at scsi3, channel 0, id 0, lun 0,  type 0
May 27 14:55:17 localhost scsi.agent[7846]:      sd_mod: loaded sucessfully (for disk)

```
BTW: is there any method, to convice system to seek /cdrom/ at /media/cdrecorder? I need this to install some packadges that needs CD with Breezy via apt-get.

---

### Post by DoktorNo on 2006-05-27
I restared the windows menager, and something really good happened: the USB-stick is now visible! BIG THX for all!

---

### Post by Sutekh on 2006-05-27
Ok well at least it is detected.  The USB is also given the device node /dev/sda.  So I imagine that there is a mountable partition on /dev/sda1.

I think you need to start the ivman daemon first
```

sudo [FONT=monospace]/usr/bin/ivman[/FONT]
```

---

### Post by Sutekh on 2006-05-27
[quote=DoktorNo]I restared the windows menager, and something really good happened: the USB-stick is now visible! BIG THX for all![/quote] 
Okay you restarted, same effect.  Good stuff!!

---

