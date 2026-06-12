---
title: "Dvd drive Read-Only want to make it Read-Write"
date: 2011-03-22
forum: General Help
---

### Post by Jerry421 on 2011-03-22
Hello fellow buntu'ers I seem to have run into a problem that i cannot fix. I am not the best with Linux but at the same time like to think I am not the worst:P:P, Anyways like stated above my dvd drive is saying its read only and i would like to make it read/write here is some info:

  *-disk                  
       description: ATA Disk
       product: ST3500418AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: CC46
       serial: 9VMRTLT1
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005ce96
  *-cdrom
       description: DVD reader
       product: DVD-ROM SD-M1612
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1806
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
jerry@jerry-desktop:~$ cdrecord --scanbus
scsibus5:
        5,0,0   500) 'TOSHIBA ' 'DVD-ROM SD-M1612' '1806' Removable CD-ROM
        5,1,0   501) *
        5,2,0   502) *
        5,3,0   503) *
        5,4,0   504) *
        5,5,0   505) *
        5,6,0   506) *
        5,7,0   507) *
Also this is my fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5d677593-2780-4900-8040-606dc3de11bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=306cab5d-d51c-4042-b258-584eb3ebdda4 none            swap    sw              0       0

---

### Post by Mark Phelps on 2011-03-23
Maybe I'm misunderstanding your question ... but an optical drive can not be treated like a hard drive.  You can't just write to it, like you can to a hard drive.  You have to "burn" a session to it.

Even with a RW drive, you're still burning individual sessions to the media, you're not actually writing files like you would a hard drive.

There were some apps in MS Windows, years ago, that would allow you to treat an optical drive like a hard drive, but there were LOTS of problems with them -- and I don't think they are around anymore.

---

### Post by SeijiSensei on 2011-03-23
K3b will typically fix problems with drive permissions.

Go to Settings > Configure K3b > Devices and click the Modify Permissions button.  Usually accepting the defaults it offers will work correctly.

---

