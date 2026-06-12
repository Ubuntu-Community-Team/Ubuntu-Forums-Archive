---
title: "flush drive unvisible"
date: 2011-03-06
forum: General Help
---

### Post by ubontik on 2011-03-06
After power blackout Ubuntu10.04 doest not see flash drive.

I meant it does not mount.

Any suggestions.

I ran $ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD400AB-00BV Rev: 21.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: LITEON   Model: DVD-ROM LTD163   Rev: GKS3
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  [COLOR="DarkRed"]Vendor: LEXAR    Model: JUMPDRIVE SPORT  Rev: 2000[/COLOR]
  Type:   Direct-Access                    ANSI  SCSI revision: 00 
***********************
So, the flash drive is there but I do not see it in nautilus.

There are no files for usb drive in the following directories.
$ ls /usr/local/bin/backuptousbdrive.sh
gdbus                 glib-genmarshal  gobject-query  gtester-report
gio-querymodules      glib-gettextize  gsettings      
glib-compile-schemas  glib-mkenums     gtester

$ ls /etc/udev/rules.d
70-persistent-cd.rules  70-persistent-net.rules  README

---

### Post by copycat042 on 2011-03-06
open your file manager, and go to the /dev directory.
plug in the usb drive.
a new item should appear.
open a terminal, and try mounting that new device.

this might not work, I'm really new to linux, it just makes sense that it might.

hope it helps. :\

---

