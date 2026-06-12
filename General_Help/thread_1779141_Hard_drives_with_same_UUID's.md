---
title: "Hard drives with same UUID's"
date: 2011-06-10
forum: General Help
---

### Post by dkolars on 2011-06-10
I switched all my drives to use UUID insted of "hdc", "hdd", "hde", etc.

I've added 2 USB HDD's to the system, both 1Tb Iomega Drives.  Turns out they have the same UUID numbers... 

One is labelled "Backup_3", and the other "Extra_Drive".

I use Krusader for drive/file management, and under /media see all the drives...

So, when rebooting, I now see that there are those drives shown, PLUS the drive "Backup_3_"... the contents of that are the same as "Extra_Drive", as they are the same drive!  I can access them both equally, and deleting a file on either on deletes it on the other (they're the same drive!)...

Is there a way to change the UUID of one of the drives and have that change remain permanent, or is the UUID burned into the HDD?  I do not unplug the drives, so they are always in the same location, and should keep the same name at all times.

I also wonder if on the next re-boot, if the system will decide to duplicate the other drive?  This could get dangerous as far as the data storage is concerned!!

Or, can I simply use the /dev/hdx1 instead of the UUID for that drive?  :confused:

Thanks...

---

### Post by jocko on 2011-06-10
Weird. It should be almost impossible to get the same UUID on two partitions.
Maybe your drives came already formatted from the factory, and iomega by some reason just copies the same file system (which would give them the same UUID) to their drives instead of actually formatting them (which would almost never give the same UUID)...
Or have you at some point cloned the file system of one drive to the other?

This should generate a new random uuid for an ext2/3/4 partition:
```
tune2fs -U random /dev/[COLOR=Blue]sdXY[/COLOR]
```It's probably a good idea to only have one of the problematic drives plugged in when you do this, and make sure you use the correct /dev/[COLOR=Blue]sdXY[/COLOR] device (they can sometimes change between boots).
I don't know if there is anything you can do on an ntfs or fat partition, other than reformatting it and loose all data...

---

### Post by dkolars on 2011-06-10
Well, here's what I get from 'sudo blkid':
[I]
/dev/sda5: LABEL="HD1" UUID="e98bf6c1-2056-47f4-8ad9-455c7e7fa529" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="bb687805-94d4-46de-8bd8-8d4c772848d8" TYPE="swap" 
/dev/sdb1: LABEL="HD2" UUID="6E8D21700D34AB95" TYPE="ntfs" 
/dev/sdg1: LABEL="Backup_Drive" UUID="1290888490886FD1" TYPE="ntfs" 
/dev/sdh1: LABEL="Disk_3" UUID="B67C20167C1FD04B" TYPE="ntfs" 
/dev/sdi1: LABEL="Backup_3" UUID="844019F84019F222" TYPE="ntfs" 
/dev/sdj1: LABEL="Extra_Drive" UUID="844019F84019F222" TYPE="ntfs" 
/dev/sdk1: LABEL="Music_&_Video" UUID="7EB08942B08901BF" TYPE="ntfs"[/I] 

As you can see sd1 & sdj1 have the same UUID...  sdj1 is empty...  so I could format it.    I've done nothing to the drives other than plug them in!

Another weird thing is Ubuntu is assigning g-k (/dev/sdg1...) for the drives, instead of c-g (/dev/sdc1, etc.).  Dunno why it's skipping the next letters in line???

---

### Post by nomko on 2011-06-10
> **jocko said:**
> Weird.
Not that weird. IF he cloned 1 disc to the other disc using the command dd, then the UUID will also be cloned.
 
 
 
Assuming it is an ext4-family filesystem:
```
uuidgen
tune2fs -U <output of uuidgen> /dev/sdb1
```

Or if the topic starter is confident uuidgen is going to work:
```
tune2fs -U `uuidgen` /dev/sdb1
```

---

### Post by srs5694 on 2011-06-10
First, jocko and nomko are both assuming that the drive uses ext2/3/4fs, but the blkid output clearly indicates that these are NTFS drives. Thus, using tune2fs will not work. As a side note, the numbers reported as UUIDs on NTFS drives aren't technically UUIDs, they're just serial numbers. They can be used in much the same way, but the probability of getting a duplicate NTFS serial number by chance is higher than the probability of getting a duplicate UUID by chance. The explanation that the manufacturer is delivering drives with identical UUIDs because they're just cloning a master filesystem makes still more sense, though.

I just checked my installed Linux NTFS utilities, and I didn't see anything that could change a UUID, so I don't think it's possible to do so "surgically." My recommendation is to back up one of the disks, create a fresh filesystem on it, and restore the data. That's a bit of a pain, but it should do the trick. If the drives are being used *only* from Linux, this procedure is advisable anyhow because it's much better to use a Linux-native filesystem for a Linux-only disk than to use NTFS for this purpose. The NTFS-3g driver that Ubuntu uses, although anecdotally reliable, is a product of reverse engineering and so might do things wrong. There are no good Linux-based NTFS filesystem maintenance tools, so if a problem develops, it may be a pain to repair the disk. The NTFS-3g driver is also slow compared to native Linux filesystem drivers.

---

### Post by dkolars on 2011-06-11
OK... so, I took the empty 1.5 Tb drive and formatted it to ext3.  Unfortunately, I made an error when I changed the settings in the fstab file, and system would NOT boot!!  Was able to boot from live CD, edit fstab, and now can re-boot... BUT, if I leave the newly formatted ext3 drive turned on, system hangs with the "Continue to wait, Skip booting, etc." message...  When I turn off that drive, boots just fine, but will not see that drive (when I turn it back on) as well as one other existing drive that it was seeing just fine before!

Plus, instead of doing the drives "logically", and starting with "sdc1" and continuing thru "sdg1" for the 5 external drives, it starts with "sdg1" and (used to) go thru "sdk1".

I would LOVE (DEARLY LOVE) for the Linux file system to be as nice as Windows was when it came to drives!!   It surely isn't!!

I'd like to be able to have my drives be loaded the same all the time, and not have all the trouble with them being re-named by Linux, not loading, etc... It is very frustrating, to say the least, and I'm a retired IT person... I thought I was done with the frustrations at this level!!

So, I now have 2 fewer HDD's accessible to me than I had a couple of days ago.  I'm going to re-name all the drives again to what I want, hunt the web to find ALL the correct things to put in the fstab file, attempt to re-format the missing ext3 drive back to NTFS, and hope this crap ends!! :o Thanks for all the assists. :D  DK

---

### Post by srs5694 on 2011-06-11
> **dkolars said:**
> I would LOVE (DEARLY LOVE) for the Linux file system to be as nice as Windows was when it came to drives!!   It surely isn't!!

ROTFL! In the mid-1990s, I became increasingly frustrated with the way DOS, Windows, and OS/2 handled disks and partitions. It was one of the reasons I switched to Linux. I think part of the reason for your current frustration is that you simply don't yet understand the Linux way of doing things, and you're trying to fit what you do understand into a Windows mental model. That's not a good fit. Once you begin to grok the Linux way (really the Unix way) of doing it, it'll be much better.

Unfortunately I can't offer you any specific advice because you haven't offered any specific details of what's gone wrong. You haven't posted your /etc/fstab file, for instance, or a list of the device nodes for your disk devices (as "ls /dev/sd*" would produce). In fact, if you want to get help for this, I recommend you download and run the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) Once it's run, post the RESULTS.txt file that it produces, but be sure to put a [noparse]```
[/noparse] tag before the file's contents and a [noparse]
```[/noparse] tag afterwards; without those tags, it'll be difficult to read because the formatting will get messed up.

---

### Post by dkolars on 2011-06-14
srs5694 --  finally back at the computer for a bit...  I would preface this with the thought that all my troubles started when I "upgraded" from 9.10 to 10.04?????????

My last experience with Windoze (aside from XP at home) was NT 4.0... I  maintained about 35-40 desktops on 3 different networks at the Univ  here... I NEVER had any problems like this with HDD's!!  I retired in  2000, so that was a while ago!  Been using computers since Commodore 64,  DOS 2.0...

Here's the story...  I have 2 - 500 Gb internal drives.  HD1 & HD2... HD1 contains the file system, and apparently has a lot of empty space that I can't access ( according to gParted, I'm using 48.60 GB and there is 398.47 Gb unused space that I can't access?) -- HD2 is a data disk.

I had 3 external HDD's... one of them died, but it turned out that the controller in the case went bad... so then I couldn't boot without hitting the "S" in the "Continue to wait, Skip mounting, Manual..." message.  Got a new enclosure for the HDD, and am back in business..  At the same time, I got 2 Iomega 1.5 Tb drives and attempted to add them to the system...  

I had been naming my external drives "Ext1", "Ext2", etc.  until someone on this forum pointed out that Linux uses those names for "stuff"... so, I renamed the drives to be what they contained:  "Disk_3", "Backup_3", "Extra_Drive", etc. etc.

I found that:
#1) Ubuntu would assign them different drive designations than what my fstab file said... I had the drives as sda1 thru sdg1... Linux persists in doing HD1 as sda1, HD2 as sdb1, then SKIPS to sdg1 for Disk_3, thru sdk1 for the last HDD;

#2) Ubuntu would rename the drives and NOT use the data that was in the fstab file, so "Backup_3" became "Backup_3_", "Disk_3" became "Disk_3_", etc. etc.  BUT, it would do it willy-nilly, not the same at every re-boot, etc.  And, of course, the /media sub-dir is getting filled with all the names that I AND Linux created, and looking at them, one has not idea which one is valid...  I use Krusader double-pane file manager for moving, copying, deleting, etc.;

#3)  The 2 Iomega HDD's had (according to Linux) the same UUID number, so one of those was ALWAYS named differently, OR did not mount.

So, that said, now I see that there are no more duplicate UUID's (?)... I did nothing to change one of them...

And, I re-did my fstab to mount the drives:
sda1 = HD1
sdb1 = HD2
sdc1 = HD3 (1 Tb, used to be Disk_3)
sdd1 = HD4 (1.5 Tb, used to be Extra_Drive)
sde1 = HD5 (1.5 Tb, used to be Backup_3)
sdf1 = HD6 (1 Tb, used to be Backup_Drive)
sdg1 = HD7 (1 Tb, used to be Music_&_Video)

Haven't changed the labels in gParted yet, but IF & WHEN this works will do that!

Just re-booted, and Ubuntu did not mount HD4, said only root could do that.  So, I did this:
[I]sudo mount /dev/sdd1 /media/HD4
[sudo] password for dkolars: 
fuse: mount failed: Device or resource busy
[/I]
Hello?  There is nothing using that drive!!  IT IS EMPTY!!

<rant>Another of my pet peeves... the inability to do anything of a maintenance nature easily!!  When I get the above error message, I am at a loss to figure out why that happens...  So, I end up re-booting a lot, futzing with various files, and spending countless hours on the web reading "stuff" about Linux/Ubuntu/etc.</rant>

Another thing:  at boot-up, I'm giving the option of starting Windows XP... I originally had a double boot, but I deleted Windows... Ubuntu thinks it's still there, as there is also a line below that references its existence???

So, as per your suggestion, here is the result of running the Boot Info Script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.
 => Windows is installed in the MBR of /dev/sdk.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdk1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *             63   976,768,064   976,768,002   5 Extended
/dev/sda5                 126   937,585,592   937,585,467  83 Linux
/dev/sda6         937,585,656   976,768,064    39,182,409  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63 2,930,272,064 2,930,272,002   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63 2,930,272,064 2,930,272,002   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdk _____________________________________________________________________

Disk /dev/sdk: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdk1    *             63 1,953,520,127 1,953,520,065   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        e98bf6c1-2056-47f4-8ad9-455c7e7fa529   ext3       HD1
/dev/sda6        bb687805-94d4-46de-8bd8-8d4c772848d8   swap       
/dev/sdb1        6E8D21700D34AB95                       ntfs       HD2
/dev/sdc1        B67C20167C1FD04B                       ntfs       Disk_3
/dev/sdd1        04284DB8731F569F                       ntfs       
/dev/sde1        844019F84019F222                       ntfs       Backup_3
/dev/sdf1        1290888490886FD1                       ntfs       Backup_Drive
/dev/sdk1        7EB08942B08901BF                       ntfs       Music_&_Video

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/HD2               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/HD3               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/HD4               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1        /media/HD5               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdf1        /media/HD6               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdk1        /media/Music_&_Video     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e98bf6c1-2056-47f4-8ad9-455c7e7fa529

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-33-generic
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-33-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-33-generic (recovery mode)
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro  single
initrd        /boot/initrd.img-2.6.32-33-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-32-generic
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-32-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-32-generic (recovery mode)
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro  single
initrd        /boot/initrd.img-2.6.32-32-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-31-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic (recovery mode)
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro  single
initrd        /boot/initrd.img-2.6.32-31-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.31-23-generic
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.31-23-generic (recovery mode)
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 ro  single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Chainload into GRUB 2
root        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/grub/core.img

title        Ubuntu 10.04.2 LTS, memtest86+
uuid        e98bf6c1-2056-47f4-8ad9-455c7e7fa529
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=e98bf6c1-2056-47f4-8ad9-455c7e7fa529 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=bb687805-94d4-46de-8bd8-8d4c772848d8 none swap sw 0 0
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sdb1 /media/HD2 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdc1 /media/HD3 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdd1 /media/HD4 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sde1 /media/HD5 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdf1 /media/HD6 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdg1 /media/HD7 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0

#/dev/sdg1 /media/Backup_Drive ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0

#/dev/sdb1 /media/HD2 ntfs-3g defaults,locale=en_US.UTF-8,uid=1000,gid=1000,umask=000 0 0
#/dev/sdc1
#UUID=B67C20167C1FD04B /media/Disk_3 ntfs-3g defaults,auto,locale=en_US.UTF-8,uid=1000,gid=1000,umask=000 0 0
#/dev/sdd1
#UUID=7EB08942B08901BF /media/Music_Video ntfs-3g defaults,auto,locale=en_US.UTF-8,uid=1000,gid=1000,umask=000 0 0
#/dev/sde1
#UUID=844019F84019F222 /media/Backup_3 ntfs-3g defaults,auto,locale=en_US.UTF-8,uid=1000,gid=1000,umask=000 0 0
#/dev/sdf1
#UUID=04284DB8731F569F /media/Extra_Drive ext3 defaults,auto,locale=en_US.UTF-8,uid=1000,gid=1000,umask=000 0 0
#/dev/sdg1
#UUID=1290888490886FD1 /media/Backup_Drive ntfs-3 defaults,auto,locale=en_US.UTF-8,uid=1000,gid=1000,umask=000 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.075240135 = 15.113174016   boot/grub/core.img                             1
  26.109450340 = 28.034808832   boot/grub/menu.lst                             1
  26.078310966 = 28.001373184   boot/grub/stage2                               2
  26.100798607 = 28.025519104   boot/initrd.img-2.6.31-23-generic              4
  26.124854088 = 28.051348480   boot/initrd.img-2.6.32-31-generic              3
  26.038744926 = 27.958889472   boot/initrd.img-2.6.32-32-generic              4
  26.021243095 = 27.940097024   boot/initrd.img-2.6.32-33-generic              4
  26.011523247 = 27.929660416   boot/vmlinuz-2.6.31-23-generic                 3
  26.105410576 = 28.030471168   boot/vmlinuz-2.6.32-31-generic                 2
  26.050829887 = 27.971865600   boot/vmlinuz-2.6.32-32-generic                 2
  26.042510033 = 27.962932224   boot/vmlinuz-2.6.32-33-generic                 2
  26.021243095 = 27.940097024   initrd.img                                     4
  26.038744926 = 27.958889472   initrd.img.old                                 4
  26.042510033 = 27.962932224   vmlinuz                                        2
  26.050829887 = 27.971865600   vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sdg sdh sdi sdj   

```

Will be interested to hear your thoughts on all of this...  Thanks.... DK

---

### Post by dkolars on 2011-06-20
OK, was out of town for the weekend, computer shut down.. Re-started it, and get big mess!!

fstab says:
```
/dev/sdb1 /media/HD2 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdc1 /media/HD3 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdd1 /media/HD4 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sde1 /media/HD5 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdf1 /media/HD6 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
/dev/sdg1 /media/HD7 ntfs-3g defaults,locale=en_US.UTF-8,nobootwait 0 0
```System boots up, 1 HDD is listed by it's UUID, the others are mounted on /dev/sdg1 thru /dev/sdk1 instead of /dev/sdc1 thru /dev/sdg1, and the mount points are, again, some of the right names (!) with the added underscore tacked onto the end:  "Disk_3_" instead of "Disk_3", and even those are wrong according to the fstab file, as it should be HD3 as the mount point with "Disk_3" as the label.

Does ANYONE have any idea what the problem is?????????:confused::confused::confused::confused:

Is it 10.04?
    I never had any problems like this with 9.10...
Is it my fstab file?
   If so, can someone point me to a site with a definitive answer/example/explanation?  I've perused countless sites and newsgroups already, but maybe didn't know what I was looking for or missed it?

Any other thoughts?  

Windows NT = plug in a new drive, it said "Oh, a new drive, I'd like to call it 'x' (the next letter in line)... Yes or no?"  And it was that easy.  AND, it remembered it!!!!

I don't miss much about Windoze, but this experience with the drives is making me miss that part of it!!!

TIA!!  dk

---

### Post by dkolars on 2011-06-20
Just rebooted after changing the Label to match the mount point:  HD3 should mount on /media/HD3, etc. and should go from sda1 (HD1) to sdg1 (HD7)...

Here's what I got:
HD1 & HD2 are just fine... they're listed by UUID, if that matters...

Once again, starts with sdg1 and goes thru sdk1????

name     Mount Point  Label
sdg1      HD7             HD3
sdh1      HD4_           HD4
sdi1       HD7_           HD7
sdj1       HD6_           HD6
sdk1      HD5_           HD5

So, Ubuntu has, once again, created sub-dirs in the /media sub-folder, and given them the names that it wants to...  WTF????

---

### Post by idoitprone on 2011-06-20
you have grub legacy which mean you have to manually update you grub menu

/boot/grub/menu.lst

remember to back up
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
``````
gksu gedit /boot/grub/menu.lst
```delete windows and your done


If i were you, I would change the mount point in the fstab by uuid. Those sda or hda is meant for the kernel to not confuse itself. They always change, but uuid stay pretty constant. Of course there is the problem with the same uuid

---

### Post by vhradice on 2011-06-20
Confession first - I use Fedora and am looking to change.  knowledge is Fedora based.  My fstab has references to the drive names (LABEL=PART1_C, PART1_D, SATA1, SATA2).  Does Ubuntu support that option in fstab?  If so, that might help instead of UUIDs.

---

### Post by idoitprone on 2011-06-20
> **vhradice said:**
> Confession first - I use Fedora and am looking to change.  knowledge is Fedora based.  My fstab has references to the drive names (LABEL=PART1_C, PART1_D, SATA1, SATA2).  Does Ubuntu support that option in fstab?  If so, that might help instead of UUIDs.

it should be the same. 

the op can take a look in the first feild paragraph and use ```
man fstab
```. If it in the doc. They must also support it

---

### Post by oldfred on 2011-06-20
If you have external drives, BIOS may mount them differently. We also have seen BIOS mount external drives as sda before internal and have seen mixed IDE/SATA where BIOS seems to randomly bring them up. It is not really a Ubuntu issue but a BIOS issue. And that is why you need to use UUID or labels. (few use labels but LABEL=label is valid).

You also are seeing the second mount under hd1_ as when you mount in /media or /home it will also show a second mount but it will not work as it is already mounted.

To show labels or UUID:
ls -l /dev/disk/by-uuid
ls /dev/disk/by-label -lah
UUID & labels
sudo blkid 

Duplicate mounts of partitions in Nautilus left panel
use /dev/disk/by-uuid/xxxxx...
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by dkolars on 2011-06-20
idoitprone - thanks... got rid of the Windoze choice!

I switched the fstab file to reference the UUID's, & found a couple of typos in the fstab file!  "ntfs-3" instead of "ntfs-3g", etc. etc.  Gee, what a difference that made for one of the drives...  So, now everything is mounting on boot up.

But, it still persists in doing the external drives sequentially starting with "sdg1" instead of "sdc1"...  different logic involved, no doubt, and as long as all is mounting, I'll have to let it be... I gots work to do!!  Thanks  all...:P

---

### Post by srs5694 on 2011-06-20
Part of the problem is that Ubuntu can mount drives in any of three ways. I suspect you're seeing the first two methods in play:


[list]
[*]**By /etc/fstab entry** -- Entries in /etc/fstab can mount a drive in a more-or-less permanent way, so that a given drive is always mount at, say, /media/foo. The problem is that "a given drive" depends on a unique way to identify the drive. The /dev/sd?? entries are subject to change for any number of reasons -- even truly random reasons like the order in which the drives are detected by the kernel as each one takes random time to be recognized. That's why most distributions, including Ubuntu, now favor UUID= or LABEL= entries in /etc/fstab. You can mount drives anywhere you like with this method -- in a subdirectory of /media, in a subdirectory of /home, in some made-up location (/pizmet/goom, say), or whatever.
[*]**By a file manager's automounter** -- Nautilus and other file managers will mount drives when you try to access them, if they aren't already mounted. Such mounts get put under /media, named either after the filesystem's name (if it's got one) or a UUID value (if there's no name).
[*]**By manual mounting** -- You can mount partitions using the text-mode "mount" command, as in "mount /dev/sdc1 /mnt". This method is used by old-school power users, but isn't much liked by recent Windows converts. I'm guessing you're not using this method.
[/list]


As a general rule, for removable disks that you regularly plug in and unplug during a session, you're best off relying on the file manager's automounter. Give the filesystem a descriptive name and it will be mounted at a consistent location based on that name when you plug it in or try to access it. For this to work, you may need to remove or comment out any /etc/fstab entry for the filesystem in question. (Be sure *not* to remove entries for your main Linux installation, though!)

If the disk is always plugged in, OTOH, IMHO it's better to use /etc/fstab, since it's much more flexible. This method is also preferable if you need access to the disk through something other than a standard GUI login, such as a file server that runs on the computer. (Such a process won't trigger the automounter in a GUI file manager.) The caveat, though, is that since you're seeing drive identifiers change, you can't rely on /dev/sd?? device names to identify your disks; you've got to use UUID= or LABEL= notation.

Incidentally, those /dev/sd?? names are not mount points, as you've referred to them; they're device identifiers. Those files give access to the hardware on a low level. You should be using them (and caring about them) only insofar as you need to reference them in /etc/fstab or use them with disk utilities like mount, mkfs, fdisk, and GParted. In day-to-day use, if everything is set up correctly, it doesn't matter what those device identifiers are.

---

### Post by dkolars on 2011-06-21
Thanks for the reply... yes, I'm using the /etc/fstab, as I never unplug the drives.  I edit lots of music and videos, so have drives for storage of "stuff" until I can get to it and burn it to DVD/CD's...  

OK, I've resigned myself to the fact that the device identifiers are not going to conform to any pattern that ~I~ want :-)  As long as they mount, I don't care!! But, in the process of attempting to sort this all out, it seemed like another thing that was acting hinkey, and perhaps needed to be dealt with...  Glad to know it's not a concern in the grand scheme of things!!

Thanks again!  dk

---

