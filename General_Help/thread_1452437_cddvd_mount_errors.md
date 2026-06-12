---
title: "cd/dvd mount errors"
date: 2010-04-11
forum: General Help
---

### Post by truthseer0 on 2010-04-11
hey all, having some cd troubles here. had them since i installed Xubuntu but never honestly cared. lets start out with, i have two cd/dvd drives, /dev/sr0 and sr1. my fstab is this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0b52afda-62c6-4670-b6ee-30a41ee0976b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=4d1c33bf-b968-4577-bbb5-e2e602322f4d /boot           ext3    relatime        0       2
# /dev/sda3
# UUID=27e49790-65a5-4f70-ac6a-905a0f02b83b /home           ext3    relatime        0       2
/dev/sda3 /home ext3 relatime 0 2
# /dev/sda4
UUID=e366a4b5-2340-4493-a158-bf73510fb1e8 none            swap    sw              0       0
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sr1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/home/gravemind/Videos	ext4	defaults 0 0


when i try to mount from terminal i get:

> mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

and from dmesg|tail after trying to mount and failing, i get:
> [34467.749652] ISOFS: Unable to identify CD-ROM format.
[34685.990339] UDF-fs: No anchor found
[34685.990342] UDF-fs: No partition found (1)
[34686.163667] ISOFS: Unable to identify CD-ROM format.
[35492.974472] UDF-fs: No anchor found
[35492.974475] UDF-fs: No partition found (1)
[35493.114914] ISOFS: Unable to identify CD-ROM format.
[35548.340658] UDF-fs: No anchor found
[35548.340661] UDF-fs: No partition found (1)
[35548.482955] ISOFS: Unable to identify CD-ROM format.


i've had problems withall the cds i've tried, i'll go collect some more later and try them, but so far i've tried game DVDs and mp3 data cd's. sr1 works perfectly fine, automounts and the whole nine yards, it's just sr0. any tips, suggestions, etc.?

thank you

also, sorry, i've been on linux for over a year now but i STILL feel like a total noob when a problem arises that i can't fix myself.

attached is a picture of the error it spits out at me from the GUI when attempting to automount.

---

### Post by truthseer0 on 2010-04-12
anybody? any ideas? anything at all?

---

### Post by truthseer0 on 2010-04-13
i've tried google, i've tried my to linux savvy friends, i could ask a third who tried gentoo but if Ted didn't know the answer i doubt Isaac will (Ted = most senior in linux years, Isaac = gentoo buddy)

any ideas, any help, even a "i have no idea" would be nice. just *A* response would be awesome at this point

---

### Post by kuckunniwi on 2010-04-14
> **truthseer0 said:**
> i've tried google, i've tried my to linux savvy friends, i could ask a third who tried gentoo but if Ted didn't know the answer i doubt Isaac will (Ted = most senior in linux years, Isaac = gentoo buddy)

any ideas, any help, even a "i have no idea" would be nice. just *A* response would be awesome at this point

I've been having the same problem (I must warn, I'm completely new to Linux. I've looked around a lot before submitting any questions).

I have two drives on my P-III 1Ghz 512Mb RAM, a DVD drive & a CD-RW. They are connected and wired correctly (PINS OK),and as has apparently happened to others, **I installed Xubuntu 9.10 using one of these drives**, and now the system recognizes neither of them. For the record, I have a Windows partition on this PC, and both drives are detected and fully operational in Windows.

Both devices are physically detected and listed in lshw as *ready*:

> 
*-cdrom:0

                description: DVD reader

                product: ODD-DVD SD-M1802

                vendor: TOSHIBA

                physical id: 1

                bus info: scsi@1:0.0.0

                logical name: /dev/cdrom

                logical name: /dev/dvd

                logical name: /dev/scd0

                logical name: /dev/sr0

                version: 1030

                capabilities: removable audio dvd

                configuration: ansiversion=5 status=ready

              *-medium

                   physical id: 0

                   logical name: /dev/cdrom

           *-cdrom:1

                description: CD-R/CD-RW writer

                physical id: 0.1.0

                bus info: scsi@1:0.1.0

                logical name: /dev/cdrom1

                logical name: /dev/cdrw1

                logical name: /dev/scd1

                logical name: /dev/sr1

                capabilities: audio cd-r cd-rw

                configuration: status=ready




In System > Users and groups > Properties > User privileges "Use CD-ROM" is checked.

When trying to mount manually in Xubuntu, I get the message:

> mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 


dmesg | tail gives me:

> 
[ 2173.260468] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2173.260478] sr 1:0:0:0: [sr0] Add. Sense: Invalid field in cdb
[ 2173.260490] end_request: I/O error, dev sr0, sector 2496
[ 2173.260616] UDF-fs: No anchor found
[ 2173.260622] UDF-fs: No partition found (1)
[ 2173.295410] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2173.295424] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 2173.295435] sr 1:0:0:0: [sr0] Add. Sense: Invalid field in cdb
[ 2173.295448] end_request: I/O error, dev sr0, sector 64
[ 2173.295562] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16


The fstab info is: 

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=32517bb3-04d8-4ec5-ad7f-d3fa6cf00c9f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4e3da0d5-645d-424f-a1bb-6f10bdaf907a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Does anyone have any idea how to solve this problem? I'm just switching over from Windows, and am happily running Ubuntu 9.10 on my laptop and would love to get my desktop fully operational.

Thanks in advance! If I find any useful info elsewhere, I'll be sure to post it. 

Peace!

---

### Post by dwarfolo on 2010-04-14
Beware that you can't and you do not need to mount audio CDs.

Are the CDs you're trying to mount burned with Vista for chance?

---

### Post by truthseer0 on 2010-04-15
> **dwarfolo said:**
> Beware that you can't and you do not need to mount audio CDs.

Are the CDs you're trying to mount burned with Vista for chance?

in my case no. i tried a cd i burned back on ubuntu 9.10 when i was using Gnome (had to reinstall for various reasons) and didn't work on xubuntu 9.10. and now i'm running into even more problems! now i dont' have a desktop after updating something, but the update had nothing to do with xfce stuff... so confused... 

but somehow, dvdrom fixed itself??? mounted several cds now perfectly fine, don't know what original problem was, but if anyone can post for the guy after me that'd be great, and afterwards i'll move to "[solved]"

---

