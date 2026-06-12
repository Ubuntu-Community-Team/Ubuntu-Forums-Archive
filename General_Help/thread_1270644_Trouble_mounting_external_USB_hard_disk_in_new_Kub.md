---
title: "Trouble mounting external USB hard disk in new Kubuntu 8.04"
date: 2009-09-19
forum: General Help
---

### Post by TheMatt on 2009-09-19
Hey guys, I have a small problem. When I try to mount my external USB HDD in Konqueror I get this error

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so 
```

I also get this:

```
mattmodica@Dothan:/media$ sudo mount sda1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: can't find sda1 in /etc/fstab or /etc/mtab
mattmodica@Dothan:/media$
```

The disk mounted fine in 6.06. Any ideas? Thanks!

---

### Post by infurnus on 2009-09-20
What is the File system that is on your usb drive?

then we can specify it in our mount command 

#$ mkdir /media/usbstick
#$ mount /dev/sda1 /media/usbstick

If it is still giving you issue about the FS type try -t <type>. Use man mount to find out the types.

Also, as a beginner it is easier/quicker to sometimes leave the drive in and cleanly reboot your computer. Especially if it is NTFS and was not cleanly unmounted in windows.

EDIT: also it would be helpful of you posted `dmesg | tail`  ^_^

---

### Post by TheMatt on 2009-09-20
The hard disk is FAT32. I also have an SD card reader which is giving the same problem when I insert a card formated as FAT. The drive was plugged in when I booted up. Also hers is dmesg | tail

```
mattmodica@Dothan:~$ dmesg | tail
[17254792.288000] sdc: assuming drive cache: write through
[17254792.316000] SCSI device sdc: 4001792 512-byte hdwr sectors (2049 MB)
[17254792.324000] sdc: Write Protect is off
[17254792.324000] sdc: Mode Sense: 38 00 00 00
[17254792.324000] sdc: assuming drive cache: write through
[17254792.324000]  sdc: sdc1
[17254792.348000] sd 3:0:0:1: Attached scsi removable disk sdc
[17254792.348000] sd 3:0:0:1: Attached scsi generic sg2 type 0
[17254792.360000] usb-storage: device scan complete
[17254800.736000] FAT: Unrecognized mount option "flush" or missing value

```

---

