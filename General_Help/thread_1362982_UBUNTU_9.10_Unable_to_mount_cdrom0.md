---
title: "UBUNTU 9.10 Unable to mount cdrom0"
date: 2009-12-23
forum: General Help
---

### Post by adrenalin6 on 2009-12-23
I just upgraded to UBUNTU 9.10 and I can no longer read or burn cds, dvds you name it if it involves a disk. Help would be appreciated!

alo here is the error i get

Unable to mount cdrom0
mount: special device /dev/scd0 does not exist

picture :

[IMG]http://i581.photobucket.com/albums/ss251/v3el_diablo/Screenshot-1-2.png[/IMG]

---

### Post by taurus on 2009-12-23
See if you still have an entry in /etc/fstab for your CD/DVD.

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```
Also have a look at the dmesg.

```
dmesg | more
```
Hit the Space key for the next 24 lines.

---

### Post by adrenalin6 on 2009-12-24
> **taurus said:**
> See if you still have an entry in /etc/fstab for your CD/DVD.

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```Also have a look at the dmesg.

```
dmesg | more
```Hit the Space key for the next 24 lines.

cat /etc/fstab gives 
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4a8f8a0b-1b7e-48b4-8072-8b33b3d3ffca /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7dee1cec-7cdb-45d3-b745-0c6f0bf8f25f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```and dmesg | more says lots of things
but pressing space 24 times tells me 

```

[    1.244796]   alloc irq_desc for 20 on node -1
[    1.203766] pata_jmicron 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IR
Q 17
[    1.203794] pata_jmicron 0000:02:00.0: setting latency timer to 64
[    1.203882] scsi4 : pata_jmicron
[    1.203945] scsi5 : pata_jmicron
[    1.204593] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[    1.204595] ata6: PATA max UDMA/100 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[    1.205044] Fixed MDIO Bus: probed
[    1.205072] PPP generic driver version 2.4.2
[    1.205139] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.205152] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.205161] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.205164] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.205201] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus numbe
r 1
[    1.209118] ehci_hcd 0000:00:1a.7: debug port 1
[    1.209123] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.209128] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdbfffc00
[    1.224020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.224109] usb usb1: configuration #1 chosen from 1 choice
[    1.224143] hub 1-0:1.0: USB hub found
[    1.224156] hub 1-0:1.0: 4 ports detected
[    1.224212]   alloc irq_desc for 23 on node -1


```

I can post the full msg if you want

---

### Post by adrenalin6 on 2009-12-24
Nevermind, im switching to windows

---

### Post by shp.jc on 2009-12-24
I'm having the same problem with a Dell Latitude C400.  It's quite old so I can't switch back to Windows 2000 :(...I have to get ubuntu working.

Thanks for any help you can give.

The exact error message is

Unable to mount cdrom0
mount: special device /dev/scd0 does not exist

I followed the directions given earlier in the thread and got...

scott@scott-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3ae802fa-ddc7-47a4-a5af-61b153088fb0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0b1c1661-e18a-4ab2-a214-8f693ca06cc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
scott@scott-laptop:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4
.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 
2.6.31-16.53-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel


Any advice?

---

