---
title: "Testdisk, photorec, and USB drive"
date: 2009-10-01
forum: General Help
---

### Post by kvk on 2009-10-01
Hi folks~

I had a 4GB USB drive suddenly stop being detected yesterday. Plugging it in and running

```

dmesg

```

produces

```

Sep 30 20:32:12 arctos kernel: [43967.735021] usb 1-9: new high speed USB device using ehci_hcd and address 11
Sep 30 20:32:12 arctos kernel: [43967.860883] usb 1-9: New USB device found, idVendor=0930, idProduct=6545
Sep 30 20:32:12 arctos kernel: [43967.860886] usb 1-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 30 20:32:12 arctos kernel: [43967.860888] usb 1-9: Product: USB Flash Memory
Sep 30 20:32:12 arctos kernel: [43967.860889] usb 1-9: Manufacturer:         
Sep 30 20:32:12 arctos kernel: [43967.860891] usb 1-9: SerialNumber: 5B85140000B1
Sep 30 20:32:12 arctos kernel: [43967.860967] usb 1-9: configuration #1 chosen from 1 choice
Sep 30 20:32:12 arctos kernel: [43967.863546] scsi11 : SCSI emulation for USB Mass Storage devices
Sep 30 20:32:17 arctos kernel: [43972.895487] scsi 11:0:0:0: Direct-Access              USB Flash Memory PMAP PQ: 0 ANSI: 0 CCS
Sep 30 20:32:17 arctos kernel: [43972.896070] sd 11:0:0:0: Attached scsi generic sg2 type 0
Sep 30 20:32:18 arctos kernel: [43973.382435] sd 11:0:0:0: [sdc] 7827456 512-byte hardware sectors: (4.00 GB/3.73 GiB)
Sep 30 20:32:18 arctos kernel: [43973.383433] sd 11:0:0:0: [sdc] Write Protect is off
Sep 30 20:32:18 arctos kernel: [43973.387435]  sdc:
Sep 30 20:32:18 arctos kernel: [43973.430741] sd 11:0:0:0: [sdc] Attached SCSI removable disk


```

so the system is able to detect the drive.

Running testdisk, it is able to detect it as well, but returns as no bootable partition. In trying to write a new MBR on the first sector, it says success, but upon removal and re-entry it returns the same error. It is able to check the structure, and returns that the structure is ok.

Using Photorec, it also detects it, and returns

```

    Partition                  Start        End    Size in sectors
   No partition             0   0  1  1018  17 18    7827456 [Whole disk]

```

when it is selected. Proceeding to File Options, it says Photorec will attempt to locate the following file types (producing the default list with all selected), but at this enters the circular file- there is no way to proceed and allow it to detect anything on the drive. Saving the setting and quitting simply return me to the "No partition" lines above.

The drive doesn't appear on the media GUI, and is not present under the /media directory. It's not detected by /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# /dev/sda1
UUID=6fdaa8e1-d209-4e36-9e15-35b461104cee / ext3 relatime,errors=remount-ro 0 1
# /dev/sda2
UUID=2f2ace82-de21-44e4-b019-ba78e063b234 none swap sw 0 0
# cdrom

```

nor is it found running /etc/mtab

```

/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sdb1 /mnt/sdb1 ext3 rw,nosuid 0 0
/dev/hda /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0

```

Does anyone have any suggestions how best to proceed to recover these data?

Thanks so much!

---

### Post by rreese6 on 2009-10-01
Mount it?

[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

or you could try udev to rescan for new devices:
```
sudo udevadm trigger 
```

---

### Post by kvk on 2009-10-01
I guess I should have mentioned that one. :-p

Won't mount from the command line.

---

### Post by rreese6 on 2009-10-01
what happened when you used sudo udevadm trigger?

---

### Post by kvk on 2009-10-02
Nothing at all.

I reviewed the link you provided- it had some new stuff I haven't tried before. Unfortunately, I get a stream of error messages far too long to post, generally about an error in the line

```

sudo mount -t vfat /dev/sdc /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137

```

I've tried a number of version of the mount command, icluding 'pmount', to no avail. It is still listed as a SCSI removable flash drive, but I can't seem to get to it.

Thanks for the link- I'll keep pressing buttons and see what happens. :-p

---

### Post by rreese6 on 2009-10-03
Since none of us are sitting in front of your computer, It might be a better idea if you would post the error messages when running the above mount command.
Also did you make a directory called external in the /media folder?

If your list is long then just tag ">> error.txt" (without quotes) tot he end of your command
then post the error.txt file here as an attachment.

---

