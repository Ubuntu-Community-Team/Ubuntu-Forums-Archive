---
title: "Accessing encrypted home partition via Live USB (Encrypted hard drive)"
date: 2012-08-08
forum: General Help
---

### Post by mhsy on 2012-08-08
Hello,

For some reason, my laptop wasn't able to resume from suspend this morning. It turns out it had lots of inode errors which fsck wasn't able to fix (but e2fsck was).

After that, the computer was running terribly slowly (~20 minutes from decrypt HDD to login screen, and about 15 minutes to log in via tty; it doesn't log in from the gui). Before every command, there was:

```
zle-line-init echoi:1:no such terminfo capability: smkx
```And after every command, there was: 

```
zle-line-finish echoi:1:no such terminfo capability: rmkx
```ls showed there were 2 files: README.txt and Access-Your-Private-Data.desktop, but nothing was working. :confused:

Anyway, I gave up and tried to back up the data from a 12.04 Live USB. I ran the following commands to mount my home and root partition (after logging into the hard drive from nautilus):

```

sudo pvscan
sudo vchange -a y
sudo lvscan
sudo mkdir /media/{root,home}
sudo mount /dev/MS/home /media/home
sudo mount /dev/MS/root /media/root

```I verified that it is the proper one using ```
ls /media/home
```Trying cd though did not work, and permission was denied.

I then tried ```
sudo encryptfs-mount-private
```but it couldn't find any private directories.

So now I am stuck. I think the hard drive may be physically damaged, so I will be getting a new one, but I would like to recover my data as soon as possible.

What am I doing wrong? Am I even using the right method? Any advice is really appreciated. Thanks!

---

### Post by Bucky Ball on 2012-08-08
You need to create a mount point for it and mount it there. Find out what drive it is using Gparted or from a terminal with:

```
sudo blkid
```Briefly, create a directory to mount you drive (in /media or /mnt). Once you've identified the drive, mount it there with something like, presuming your partition is sdb1, say:

```
sudo mount /dev/sdb1 /media/your-mount-directory
```Of course, you need to change the details to match the partition you want to mount and your situation. Good luck. ;)

PS: If you want it to mount at boot you are going to need to change your /etc/fstab file accordingly which we can help with. ALWAYS make a back up of any important file you are going to tweak BEFORE you commence with something like:

```
sudo cp /etc/fstab /etc/fstab.BAK
```

This copies the original file and creates one called fstab.BAK. If you screw things up, then:

```
sudo cp /etc/fstab.BAK /etc/fstab
```

---

### Post by mhsy on 2012-08-08
> **Bucky Ball said:**
> You need to create a mount point for it and mount it there. 

```
sudo mount /dev/sdb1 /media/your-mount-directory
```

Thanks for the reply. This is what I had done earlier. It was under the logical volume /dev/MS/home, and I mounted it under /media/home. GParted only shows /dev/sdb (the USB drive).

---

### Post by Bucky Ball on 2012-08-08
In the right hand top corner of Gparted is a drop-down list with your drives on it. If that is showing sdb, then click it and see if sda is also there. ;)

---

### Post by mhsy on 2012-08-08
Unfortunately, there is nothing else there. What do you suppose caused the whole thing in the first place?

---

### Post by Bucky Ball on 2012-08-08
> **mhsy said:**
> Unfortunately, there is nothing else there. What do you suppose caused the whole thing in the first place?

? Hard to say. Sometimes other things happen when attempting to fix!

What is the output of 'sudo blkid'? Also, you could try downloading and running the Boot-info script. 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That will show you everything you need to know about what's where, including bootable partitions, if there are any.

It is very odd Gparted shows nothing. Not even free space. Wild stab, but are you booting with the USB out? If not, try it. You could check your BIOS is set to boot from the hard drive and see what happens (it could be trying to boot to the stick).

---

### Post by mhsy on 2012-08-09
"sudo blkid" gives:

```
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="5618e503-2e69-437a-b0aa-fc8941a8bf30" TYPE="ext3" 
/dev/sdb1: UUID="2E23-4245" TYPE="vfat" 
```

I am running on the live USB since I can't do anything with the hard drive. The hard drive is encrypted though. Would that affect what gparted sees (even though it is decrypted already)?

I will try running the script tomorrow; I have to sleep for tonight. I will be back in about 16 hours.

---

### Post by mhsy on 2012-08-09
I thought this was significant enough to post now.

This is the result from bootinfoscript:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 1459776 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,620,279    15,620,218   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       5618e503-2e69-437a-b0aa-fc8941a8bf30   ext3       
/dev/sdb1        2E23-4245                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
MS-home
MS-root
MS-swap
udisks-luks-uuid-4c7179d1-49a2-4371-b4bb-58808762b56b-uid999

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/MS-home /media/home              ext4       (rw)
/dev/mapper/MS-root /media/root              ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/dm-3[Input/output error]
ERROR: ddf1: reading /dev/dm-3[Input/output error]
ERROR: ddf1: reading /dev/dm-3[Input/output error]
ERROR: hpt45x: reading /dev/dm-3[Input/output error]
ERROR: isw: reading /dev/dm-3[Input/output error]
ERROR: isw: reading /dev/dm-3[Input/output error]
ERROR: isw: reading /dev/dm-3[Input/output error]
ERROR: jmicron: reading /dev/dm-3[Input/output error]
ERROR: lsi: reading /dev/dm-3[Input/output error]
ERROR: nvidia: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: sil: reading /dev/dm-3[Input/output error]
ERROR: via: reading /dev/dm-3[Input/output error]
ERROR: asr: reading /dev/dm-2[Input/output error]
ERROR: ddf1: reading /dev/dm-2[Input/output error]
ERROR: ddf1: reading /dev/dm-2[Input/output error]
ERROR: hpt37x: reading /dev/dm-2[Input/output error]
ERROR: hpt45x: reading /dev/dm-2[Input/output error]
ERROR: isw: reading /dev/dm-2[Input/output error]
ERROR: isw: reading /dev/dm-2[Input/output error]
ERROR: isw: reading /dev/dm-2[Input/output error]
ERROR: jmicron: reading /dev/dm-2[Input/output error]
ERROR: lsi: reading /dev/dm-2[Input/output error]
ERROR: nvidia: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: sil: reading /dev/dm-2[Input/output error]
ERROR: via: reading /dev/dm-2[Input/output error]
ERROR: asr: reading /dev/dm-1[Input/output error]
ERROR: ddf1: reading /dev/dm-1[Input/output error]
ERROR: ddf1: reading /dev/dm-1[Input/output error]
ERROR: hpt45x: reading /dev/dm-1[Input/output error]
ERROR: isw: reading /dev/dm-1[Input/output error]
ERROR: isw: reading /dev/dm-1[Input/output error]
ERROR: isw: reading /dev/dm-1[Input/output error]
ERROR: jmicron: reading /dev/dm-1[Input/output error]
ERROR: lsi: reading /dev/dm-1[Input/output error]
ERROR: nvidia: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: sil: reading /dev/dm-1[Input/output error]
ERROR: via: reading /dev/dm-1[Input/output error]
ERROR: asr: reading /dev/dm-0[Input/output error]
ERROR: ddf1: reading /dev/dm-0[Input/output error]
ERROR: ddf1: reading /dev/dm-0[Input/output error]
ERROR: hpt37x: reading /dev/dm-0[Input/output error]
ERROR: hpt45x: reading /dev/dm-0[Input/output error]
ERROR: isw: reading /dev/dm-0[Input/output error]
ERROR: isw: reading /dev/dm-0[Input/output error]
ERROR: isw: reading /dev/dm-0[Input/output error]
ERROR: jmicron: reading /dev/dm-0[Input/output error]
ERROR: lsi: reading /dev/dm-0[Input/output error]
ERROR: nvidia: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: sil: reading /dev/dm-0[Input/output error]
ERROR: via: reading /dev/dm-0[Input/output error]
ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
ERROR: asr: reading /dev/dm-3[Input/output error]
ERROR: ddf1: reading /dev/dm-3[Input/output error]
ERROR: ddf1: reading /dev/dm-3[Input/output error]
ERROR: hpt45x: reading /dev/dm-3[Input/output error]
ERROR: isw: reading /dev/dm-3[Input/output error]
ERROR: isw: reading /dev/dm-3[Input/output error]
ERROR: isw: reading /dev/dm-3[Input/output error]
ERROR: jmicron: reading /dev/dm-3[Input/output error]
ERROR: lsi: reading /dev/dm-3[Input/output error]
ERROR: nvidia: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: pdc: reading /dev/dm-3[Input/output error]
ERROR: sil: reading /dev/dm-3[Input/output error]
ERROR: via: reading /dev/dm-3[Input/output error]
ERROR: asr: reading /dev/dm-2[Input/output error]
ERROR: ddf1: reading /dev/dm-2[Input/output error]
ERROR: ddf1: reading /dev/dm-2[Input/output error]
ERROR: hpt37x: reading /dev/dm-2[Input/output error]
ERROR: hpt45x: reading /dev/dm-2[Input/output error]
ERROR: isw: reading /dev/dm-2[Input/output error]
ERROR: isw: reading /dev/dm-2[Input/output error]
ERROR: isw: reading /dev/dm-2[Input/output error]
ERROR: jmicron: reading /dev/dm-2[Input/output error]
ERROR: lsi: reading /dev/dm-2[Input/output error]
ERROR: nvidia: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: pdc: reading /dev/dm-2[Input/output error]
ERROR: sil: reading /dev/dm-2[Input/output error]
ERROR: via: reading /dev/dm-2[Input/output error]
ERROR: asr: reading /dev/dm-1[Input/output error]
ERROR: ddf1: reading /dev/dm-1[Input/output error]
ERROR: ddf1: reading /dev/dm-1[Input/output error]
ERROR: hpt45x: reading /dev/dm-1[Input/output error]
ERROR: isw: reading /dev/dm-1[Input/output error]
ERROR: isw: reading /dev/dm-1[Input/output error]
ERROR: isw: reading /dev/dm-1[Input/output error]
ERROR: jmicron: reading /dev/dm-1[Input/output error]
ERROR: lsi: reading /dev/dm-1[Input/output error]
ERROR: nvidia: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: pdc: reading /dev/dm-1[Input/output error]
ERROR: sil: reading /dev/dm-1[Input/output error]
ERROR: via: reading /dev/dm-1[Input/output error]
ERROR: asr: reading /dev/dm-0[Input/output error]
ERROR: ddf1: reading /dev/dm-0[Input/output error]
ERROR: ddf1: reading /dev/dm-0[Input/output error]
ERROR: hpt37x: reading /dev/dm-0[Input/output error]
ERROR: hpt45x: reading /dev/dm-0[Input/output error]
ERROR: isw: reading /dev/dm-0[Input/output error]
ERROR: isw: reading /dev/dm-0[Input/output error]
ERROR: isw: reading /dev/dm-0[Input/output error]
ERROR: jmicron: reading /dev/dm-0[Input/output error]
ERROR: lsi: reading /dev/dm-0[Input/output error]
ERROR: nvidia: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: pdc: reading /dev/dm-0[Input/output error]
ERROR: sil: reading /dev/dm-0[Input/output error]
ERROR: via: reading /dev/dm-0[Input/output error]
ERROR: asr: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/sda" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/sda" to 4608
ERROR: hpt45x: seeking device "/dev/sda" to 18446744073709545984
ERROR: isw: seeking device "/dev/sda" to 18446744073709550592
ERROR: isw: seeking device "/dev/sda" to 18446744073709551104
ERROR: isw: seeking device "/dev/sda" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/sda" to 18446744073709551104
ERROR: lsi: seeking device "/dev/sda" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/sda" to 18446744073709550592
ERROR: sil: seeking device "/dev/sda" to 18446744073709551104
ERROR: via: seeking device "/dev/sda" to 18446744073709551104
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  /dev/dm-0: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-1: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda2: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-2: read failed after 0 of 4096 at 0: Input/output error
  /dev/dm-3: read failed after 0 of 4096 at 0: Input/output error
  No volume groups found

```

---

### Post by mhsy on 2012-08-09
Is it better if this  is moved to general? It might receive more exposure.

---

### Post by Bucky Ball on 2012-08-09
> **mhsy said:**
> Is it better if this  is moved to general? It might receive more exposure.
You can ask the mods by click 'Report Abuse' on the post in question then saying exactly what you've just posted. It shouldn't really be 'Report Abuse' as all sorts can be legitimately reported. ;)

---

### Post by Iowan on 2012-08-09
Moved by request.

---

