---
title: "Can't mount CD-ROM"
date: 2010-05-21
forum: General Help
---

### Post by Mortesins93 on 2010-05-21
Hello,
I've just installed Ubuntu 8.10 with a Pioneer DVD writer and a CD-ROM reader. The problem is that when i put a CD in either one it doesn't automatically mount and it doesn't even let me mount it manually through the terminal. Using this command:
sudo mount /dev/scd0 /media/cdrom0
I tried mounting it with every logical name listed after typing "sudo lshw -c disk" but it doesn't work and it says: "no support found" (or something like that because i have Ubuntu in Italian). By the way, I am sure that the directory /media/cdrom0 exists.
This is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e005a75f-889e-4984-a1a2-5bb21d7487ea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e9ad6808-019c-4851-b043-2a895c6fbd16 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

while this is the "sudo lshw -c disk":
with the CD inserted in the PIONEER DVD writer:

*-disk                 
       description: ATA Disk
       product: Maxtor 6Y080L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y2A81EBC
       size: 76GiB (81GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1be91be9
  *-cdrom:0
       description: DVD writer
       product: DVD-RW  DVR-111D
       vendor: PIONEER
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom:1
       description: SCSI CD-ROM
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=nodisc
and without the CD:
  *-cdrom:0
       description: DVD writer
       product: DVD-RW  DVR-111D
       vendor: PIONEER
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
while if i put the CD in the SCSI CD-ROM the thing doesn't change and it doesn't see the CD inserted.
By the way in the BIOS setup the Pioneer is Master while the CD-ROM reader is slave. What is the difference between master and slave, and primary and secondary?
What should I do? Why is there only one CD device in the fstab? Why can't i even mount the CD manually?
Please help.

---

### Post by Mortesins93 on 2010-08-08
So i found out that the CD-ROM reader does not work at all while the PIONEER DVD writer works and it automatically mounts when i insert a DVD, but when i insert a CD it doesn't automatically mount and it does not even let me mount it manually. What could the problem be? Can it be an hardware problem? Anything to do with the BIOS? Or is it a problem with my Ubuntu?
Please answer.

---

### Post by soldier1st on 2010-08-08
did you upgrade to the newest ubuntu install 10.04?

---

### Post by Mortesins93 on 2010-08-09
No, but i don't think that is the problem. Do you?

---

