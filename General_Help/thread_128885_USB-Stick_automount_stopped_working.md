---
title: "USB-Stick automount stopped working"
date: 2006-02-12
forum: General Help
---

### Post by Owdy on 2006-02-12
When i put my usb-stick in, it gives me an error. It worked fine before. If i manually mount it, it works.  What happend to that automount thingy?

---

### Post by sup on 2006-02-12
looks to me that something could be wrong with /etc/fstab ... could you post it here?

what does sudo mount -a gives back?

---

### Post by Owdy on 2006-02-12
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda2       /media/windows-d  vfat defaults,users,umask=0000
/dev/sda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

>  what does sudo mount -a gives back? Nothing

---

### Post by sup on 2006-02-12
when you plug in your usb stick, how it identifies itself (df or sudo fdisk -l if it does not mount)?

---

### Post by Owdy on 2006-02-12
```
Levy /dev/sdb: 512 Mt, 512753664 tavua
56 päätä, 32 sektoria/ura, 558 sylinteriä
Yksiköt = 1792 * 512 = 917504 -tavuiset sylinterit
    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/sdb1   *           1         559      500592    6  FAT16
Osiolla 1 on eri fyysiset/loogiset loppukohdat:
     fyysinen=(838, 55, 32) looginen=(558, 39, 32)

``` Its finnish language, sorry :D

And in nautilus, there is that Kingston DataTraveler 2.0 icon, but when i click it, it gives that error i posted.

---

### Post by Owdy on 2006-02-13
Maybe i should report a bug?

---

### Post by chettyk on 2006-02-13
This happens to me from time to time. Usually, the USB stick will auto-mount without a problem. Now and then -- typically when I am in a real hurry -- it refuses to auto-mount. I got over the problem by adding a line in the /etc/fstab

```
/dev/sda1	/media/usb1	vfat	rw,user,noauto,sync,noatime	0	0
```

In your case, I think that the device will probably have to be /dev/sdb1

Note that I created a mount point 'usb1' under /media . You could designate some other mount point. Just make sure the mount point exists before you change the fstab file.

Also, the file system for my USB stick is vfat so that I can use it with Windows machines as well. Maybe someone else will be able to advise you whether vfat would work with the FAT16 format of your USB stick.

After I made these changes, whenever the USB stick does not auto-mount, all I have to do is open a terminal and type the command:

```
mount /media/usb1
```

---

### Post by Owdy on 2006-02-13
Like i sayd, i know how to manually mount it. I just wonder why that automount wouldnt work anymore. It worked before and it still should be. :)

---

### Post by Owdy on 2006-02-13
I tested that yourway. It works of source, but now i got 2 usb stick icons under computer:/// . That created one and that orginal what isnt working anymore.

---

### Post by Owdy on 2006-02-13
What this telss you?

```
osku@Koti:~$ dmesg | tail -20
[4322390.963000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4322390.963000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4322390.963000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.
[4322390.969000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4322390.969000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4322390.969000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.
[4322390.976000] HFS+-fs: unable to find HFS+ superblock
[4322390.982000] HFS+-fs: unable to find HFS+ superblock
[4322390.988000] VFS: Can't find a HFS filesystem on dev sdb.
[4322390.993000] VFS: Can't find a HFS filesystem on dev sdb.
[4322391.000000] VFS: Can't find ext3 filesystem on dev sdb.
[4322391.006000] VFS: Can't find ext3 filesystem on dev sdb.
[4322391.011000] VFS: Can't find an ext2 filesystem on dev sdb.
[4322391.017000] VFS: Can't find an ext2 filesystem on dev sdb.
[4322391.024000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[4322391.030000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[4322391.037000] XFS: bad magic number
[4322391.037000] XFS: SB validate failed
[4322391.043000] XFS: bad magic number
[4322391.043000] XFS: SB validate failed

```

---

### Post by chettyk on 2006-02-14
[QUOTE=Owdy]I tested that yourway. It works of source, but now i got 2 usb stick icons under computer:/// . That created one and that orginal what isnt working anymore.[/QUOTE]

That suggests that the system is in fact correctly recognising your USB stick. If so, perhaps you ought to check the menu at System > Preferences > Removable Drives and Media > Storage. For me, in that menu, the following options are enabled:
- Mount removable drives when hot-plugged
- Mount removable media when inserted
- Browse removable media when inserted

With this, my USB stick is normally recognised and auto-mounted.

---

### Post by Owdy on 2006-02-14
[quote=chettyk]That suggests that the system is in fact correctly recognising your USB stick. If so, perhaps you ought to check the menu at System > Preferences > Removable Drives and Media > Storage. For me, in that menu, the following options are enabled:
- Mount removable drives when hot-plugged
- Mount removable media when inserted
- Browse removable media when inserted

With this, my USB stick is normally recognised and auto-mounted.[/quote] Same here, but it isnt working. 
[https://launchpad.net/distros/ubuntu/+bug/31341]("https://launchpad.net/distros/ubuntu/+bug/31341")

---

### Post by ozorba on 2006-02-14
This script works for me when KDE does not see the USB storage devices.

Cheers,
OZ

---

### Post by ozorba on 2006-02-14
> **ozorba]This script works for me when KDE does not see the USB storage devices.

Cheers,
OZ[/QUOTE]

I swear that I have uploaded a shell script. However, it is not here. 

Here is the long one.

[QUOTE]
#!/bin/bash
# Skript to rescan SCSI bus, using the 
# scsi add-single-device mechanism
# (w) 1998-03-19 Kurt Garloff <kurt@garloff.de> (c) GNU GPL
# (w) 2003-07-16 Kurt Garloff <garloff@suse.de> (c) GNU GPL
# $Id: rescan-scsi-bus.sh,v 1.15 2004/05/08 14:47:13 garloff Exp $

setcolor ()
{
  red="\e[0 said:**
>  [host [host ...]]"
    echo "Options:"
    echo " -l activates scanning for LUNs 0-7    [default: 0]"
    echo " -w scan for target device IDs 0 .. 15 [default: 0-7]"
    echo " -c enables scanning of channels 0 1   [default: 0]"
    echo " -r enables removing of devices        [default: disabled]"
    echo "--remove:        same as -r"
    echo "--nooptscan:     don't stop looking for LUNs is 0 is not found"
    echo "--color:         use coloured prefixes OLD/NEW/DEL"
    echo "--hosts=LIST:    Scan only host(s) in LIST"
    echo "--channels=LIST: Scan only channel(s) in LIST"
    echo "--ids=LIST:      Scan only target ID(s) in LIST"
    echo "--luns=LIST:     Scan only lun(s) in LIST"  
    echo " Host numbers may thus be specified either directly on cmd line (deprecated) or"
    echo " or with the --hosts=LIST parameter (recommended)."
    echo "LIST: A[-B][,C[-D]]... is a comma separated list of single values and ranges"
    echo " (No spaces allowed.)"
    exit 0
fi

expandlist ()
{
    list=$1
    result=""
    first=${list%%,*}
    rest=${list#*,}
    while test ! -z "$first"; do 
	beg=${first%%-*};
	if test "$beg" = "$first"; then
	    result="$result $beg";
    	else
    	    end=${first#*-}
	    result="$result `seq $beg $end`"
	fi
	test "$rest" = "$first" && rest=""
	first=${rest%%,*}
	rest=${rest#*,}
    done
    echo $result
}

if test ! -d /proc/scsi/; then
  echo "Error: SCSI subsystem not active"
  exit 1
fi	

# defaults
unsetcolor
lunsearch="0"
idsearch=`seq 0 7`
channelsearch="0"
remove=""
optscan=1
if test -d /sys/class/scsi_host; then 
  findhosts_26
else  
  findhosts
fi  

# Scan options
opt="$1"
while test ! -z "$opt" -a -z "${opt##-*}"; do
  opt=${opt#-}
  case "$opt" in
    l) lunsearch=`seq 0 7` ;;
    w) idsearch=`seq 0 15` ;;
    c) channelsearch="0 1" ;;
    r) remove=1 ;;
    -remove)      remove=1 ;;
    -hosts=*)     arg=${opt#-hosts=};   hosts=`expandlist $arg` ;;
    -channels=*)  arg=${opt#-channels=};channelsearch=`expandlist $arg` ;; 
    -ids=*)   arg=${opt#-ids=};         idsearch=`expandlist $arg` ;; 
    -luns=*)  arg=${opt#-luns=};        lunsearch=`expandlist $arg` ;; 
    -color) setcolor ;;
    -nooptscan) optscan=0 ;;
    *) echo "Unknown option -$opt !" ;;
  esac
  shift
  opt="$1"
done    

# Hosts given ?
if test "@$1" != "@"; then 
  hosts=$*; 
fi

echo "Scanning hosts $hosts channels $channelsearch for "
echo " SCSI target IDs " $idsearch ", LUNs " $lunsearch
test -z "$remove" || echo " and remove devices that have disappeared"
declare -i found=0
declare -i rmvd=0
for host in $hosts; do 
  dosearch; 
done
echo "$found new device(s) found.               "
echo "$rmvd device(s) removed.                 "




This was given to be by a friend of mine. I think he got it from Red Hat, I am not sure though.

Cheers,
OZ

---

### Post by chettyk on 2006-02-14
[QUOTE=Owdy]What this telss you?

```
osku@Koti:~$ dmesg | tail -20
[4322390.963000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4322390.963000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4322390.963000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.
[4322390.969000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4322390.969000] NTFS-fs error (device sdb): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4322390.969000] NTFS-fs error (device sdb): ntfs_fill_super(): Not an NTFS volume.
[4322390.976000] HFS+-fs: unable to find HFS+ superblock
[4322390.982000] HFS+-fs: unable to find HFS+ superblock
[4322390.988000] VFS: Can't find a HFS filesystem on dev sdb.
[4322390.993000] VFS: Can't find a HFS filesystem on dev sdb.
[4322391.000000] VFS: Can't find ext3 filesystem on dev sdb.
[4322391.006000] VFS: Can't find ext3 filesystem on dev sdb.
[4322391.011000] VFS: Can't find an ext2 filesystem on dev sdb.
[4322391.017000] VFS: Can't find an ext2 filesystem on dev sdb.
[4322391.024000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[4322391.030000] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[4322391.037000] XFS: bad magic number
[4322391.037000] XFS: SB validate failed
[4322391.043000] XFS: bad magic number
[4322391.043000] XFS: SB validate failed

```[/QUOTE]

When I mount my USB stick, my dmesg output is very different:

```
~$ dmesg |tail -20
[4306912.689000] usb 4-3: new high speed USB device using ehci_hcd and address 8[4306912.807000] hub 4-3:1.0: USB hub found
[4306912.808000] hub 4-3:1.0: 1 port detected
[4306913.044000] usb 4-3.1: new high speed USB device using ehci_hcd and address 9
[4306913.128000] scsi3 : SCSI emulation for USB Mass Storage devices
[4306913.132000] usb-storage: device found at 9
[4306913.132000] usb-storage: waiting for device to settle before scanning
[4306918.133000]   Vendor: USB       Model: 2.0 Flash Drive   Rev: 1.00
[4306918.133000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4306918.141000] SCSI device sda: 1015808 512-byte hdwr sectors (520 MB)
[4306918.145000] sda: Write Protect is off
[4306918.145000] sda: Mode Sense: 00 26 00 00
[4306918.145000] sda: assuming drive cache: write through
[4306918.156000] SCSI device sda: 1015808 512-byte hdwr sectors (520 MB)
[4306918.159000] sda: Write Protect is off
[4306918.159000] sda: Mode Sense: 00 26 00 00
[4306918.159000] sda: assuming drive cache: write through
[4306918.159000]  /dev/scsi/host3/bus0/target0/lun0: p1
[4306918.165000] Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
[4306918.170000] usb-storage: device scan complete

```

I have no idea what to make of it all. Sorry.

---

### Post by Who on 2006-02-14
There is another topic in these forums where a lot of people talk about the same problem with automounting - in short - it breaks, and on a regular basis. A  bug has been filed in launchpad
[https://launchpad.net/distros/ubuntu/+bug/29888](https://launchpad.net/distros/ubuntu/+bug/29888)

[http://ubuntuforums.org/showthread.php?t=116334&page=2](http://ubuntuforums.org/showthread.php?t=116334&page=2)
is a link to the other thread

---

### Post by chettyk on 2006-02-15
The strange thing with my system is that more often than not my USB stick will get properly auto-mounted. But there are times when that doesn't happen and I have to manually mount it. I have given up trying to understand the phenomenon and coped by adding a line in my fstab file so that I can easily mount the stick manually if need be.

---

### Post by damo21 on 2006-02-16
I have the SAME problem.... it looks like a bug.  It's trying to automount the entire drive at /dev/sda instead of /dev/sda1 where the partition actually starts. 

You can reproduce the error if you type:
mount /dev/sda -t vfat /media/usb

instead of the correct version:
mount /dev/sda1 -t vfat /media/usb

I wish this could be fixed...

---

### Post by Owdy on 2006-02-16
[https://launchpad.net/distros/ubuntu/+bug/31341](https://launchpad.net/distros/ubuntu/+bug/31341)

---

