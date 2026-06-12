---
title: "Unable to mount CDRom or CDRW"
date: 2006-04-16
forum: General Help
---

### Post by pracslipkerm on 2006-04-16
I am running 5.10. I have had things all running well but tonight I tried to burn a CD and found that neither my cd burner or cdrom are working. When I try to open them from nautilus I get 'no media found'. Any help would be fantastic.
Cheers Steve :-)

---

### Post by bscbrit on 2006-04-16
Which program are you using to burn the CDs?  Have you tried running it using sudo - you shouldn't have to, but it might simply be a problem with permissions and this might work when a simple user name doesn't.  Can you see your drives in the output of:

sudo lshw | less

For example: running the command on my machine gives me an output that includes the following: 

```

    *-cdrom:0
                   description: DVD writer
                   product: SAMSUNG DVD R/RW SH-W08A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1S30
                   serial: 54RI404418
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r
              *-cdrom:1
                   description: CD-R/CD-RW writer
                   product: PHILIPS CDRW2412A
                   vendor: Philips
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 0.010000
                   serial: 5VO1215DL13748
:

```

---

### Post by pracslipkerm on 2006-04-16
Here is the output of
sudo lshw|less
 *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom:0
                   description: CD-R/CD-RW writer
                   product: ARW4420
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.1k
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
              *-cdrom:1
                   description: IDE CD-ROM
                   product: GCR-8523B
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: 1.03
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
Inserting a CD used to bring up an icon on the desktop and auto mount but now it doesn't and sudo mount -a doesn't work either. I also tried going through Nautilus but that is where I get the message no media found.
Cheers Steve :-)

---

### Post by bscbrit on 2006-04-17
*-cdrom:0
description: CD-R/CD-RW writer
product: ARW4420
physical id: 0
bus info: ide@1.0
logical name: /dev/hdc
version: 1.1k
capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw

...indicates that your computer knows about the CD drive, and even acknowledges that it is a CD writer.

Can you show me the content of /etc/fstab please.

---

### Post by dcstar on 2006-04-17
[QUOTE=pracslipkerm]
......
Inserting a CD used to bring up an icon on the desktop and auto mount but now it doesn't and sudo mount -a doesn't work either. I also tried going through Nautilus but that is where I get the message no media found.
Cheers Steve :-)[/QUOTE]
Open a terminal window, put in a CD, and then enter this command:
```
dmesg
```
and post the output of the last lines here.

---

### Post by pracslipkerm on 2007-01-14
Sorry about the extremely long delay in replying - I have been without my computer for many months (a very long story) but anyway here is the output of dmesg after inserting a cd
```
Unknown OutputIN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=136 TOS=0x00 PREC=0x00 TTL=64 ID=738 DF PROTO=UDP SPT=631 DPT=631 LEN=116
Unknown OutputIN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=136 TOS=0x00 PREC=0x00 TTL=64 ID=740 DF PROTO=UDP SPT=631 DPT=631 LEN=116
Unknown OutputIN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=136 TOS=0x00 PREC=0x00 TTL=64 ID=742 DF PROTO=UDP SPT=631 DPT=631 LEN=116

```
And here is fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
/dev/hdb4       /home           ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /suse/boot      ext3    defaults        0       2
/dev/hda2       /suse/root      reiserfs        defaults        0       1
/dev/hda3       /suse/zips      reiserfs        defaults        0       2

```
Any help would be fantastic - I really miss my cd drives...

---

