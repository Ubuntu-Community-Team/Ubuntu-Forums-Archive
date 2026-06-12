---
title: "Centon USB Memory Stick not working"
date: 2009-07-21
forum: General Help
---

### Post by virmundi on 2009-07-21
Hello,
I posted this question in Hardware and Laptop. However, upon reflection, I think this is a better location for it.

I recently purchased a Centon Datastick Pro 8 GB memory stick. My windows pcs find this drive. However, Ubuntu does not automount this drive. It automounts other drives, just not this one.

I have no idea why. I've tried to follow other similiar posts found in the forums, but to no avail. 

Here's some technical data that might help:
cat /proc/scsi/scsi
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD6400AAKS-7 Rev: 01.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: PLDS     Model: DVD+-RW DH-16A6S Rev: YD11
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: CENTON   Model: DS Pro           Rev: 0.00
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: TEAC     Model: USB   HS-CF Card Rev: 4.08
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi5 Channel: 00 Id: 00 Lun: 01
  Vendor: TEAC     Model: USB   HS-xD/SM   Rev: 4.08
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi5 Channel: 00 Id: 00 Lun: 02
  Vendor: TEAC     Model: USB   HS-MS Card Rev: 4.08
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi5 Channel: 00 Id: 00 Lun: 03
  Vendor: TEAC     Model: USB   HS-SD Card Rev: 4.08
  Type:   Direct-Access                    ANSI  SCSI revision: 00

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e89df262-7a82-4227-a916-9ea0ae11a6ce /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=74d31a46-ad26-4eca-939b-ae8d4d3ec857 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I see the drive in the proc results. I just don't know what do to get it to work. I've tried to mount it. When I did get that to happen, I was unable to write to the drive.

Please help. 

Thanks for your time,
JPD

---

### Post by virmundi on 2009-07-25
Anyone? I guess I'm the only one facing this problem.:confused:

---

### Post by fjgaude on 2009-07-25
All my USB flash drives auto mount when I look for them in File Browser and then they show on the desktop as an icon. It usually takes about 30 seconds or so for the mounting to occur.

Can you show us what this command shows:

```
sudo fdisk -l
```

You should see the USB at the bottom of the list of devices. You would mount the USB using the **/dev/sdxx** that shows for it.

---

### Post by virmundi on 2009-07-28
Thanks for the reply. 

I got the drive to mount now with the correct permissions. I took the information gleaned from fdisk -l and updated the entry into /etc/fstab file. However, the drive does not auto mount. How do I get this feature to work?

---

