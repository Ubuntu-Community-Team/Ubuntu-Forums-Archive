---
title: "Bootcdwrite tips / tutorials"
date: 2010-04-15
forum: General Help
---

### Post by seangee on 2010-04-15
I have a headless server which is primarily a NAS using 4 1Tb disks in RAID5 (3 + spare). It is also my DNS, proxy and DAAP server and I use Unison for synchronisation. I am currently using a USB stick to boot from (yes I have a backup).

I decided to give bootcdwrite a go to see what would happen, my first attempt was good enough for a recovery / emergency disk but not for a working system. My RAID was mounted and  available on the network but I did get repeated IO errors on the root system. Critically I could not access sudo - and had to resort to pulling the plug to restart. Not something I want to do too often as the fileserver is live!

I'll be happy to write up a tutorial once I have completed  this but in the meantime any tips would  be very useful :)

Here is my basic conf:
```
SRCDISK=/

# Define the kernel which is used
KERNEL=vmlinuz

# additional options for the kernel
APPEND=""

# path to initrd
INITRD="initrd.img"
RAMDISK_SIZE=16384

# typ is CD or DVD (left default setting and it worked fine on a CD)
TYP=DVD

# specify one or more CD devices to boot from, first is default
# "auto" try to find the bootcd on all SCSI and IDE CDROMS
CDDEV="auto /dev/hda /dev/hdb /dev/hdc /dev/hdd /dev/scd0 /dev/scd1"

# do some checks or not
DO_CHECK=yes

# contents of my raid
NOT_TO_CD="/storage/*"

# exclude some files or directories from loading to ram
# Because most people's home and root dir are to large to include 
# in RAM, subdirectories can be excluded:
NOT_TO_RAM="$(find $SRCDISK/home $SRCDISK/root -maxdepth 1 -mindepth 1 -type d)"

# I want clients to think its the same machine
SSHHOSTKEY=no

# use fixed ip.
UDEV_FIXNET="yes"

# This is my RAID
TO_FSTAB="/dev/md0 /storage ext4 defaults 0 1"

DISABLE_CRON="etc/cron.daily/find etc/cron.daily/standard etc/cron.daily/security"



```

---

### Post by seangee on 2010-04-16
Quick update: Setting NOT_TO_RAM = "" fixed the IO issues and everything now works. Still have a fair bit to do to make sure that what needs to be on persistent storage is - e.g. DAAP index. Also at the moment the system logs seem to be suspended so I will have to turn them back on.

Next test will be to see if I can accurately re-create the bootable USB from the CD

---

