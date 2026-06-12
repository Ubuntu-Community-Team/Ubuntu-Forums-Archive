---
title: "Grub Error 22 on Boot, Error 15 off Live CD"
date: 2009-08-22
forum: General Help
---

### Post by dwdarkstar on 2009-08-22
[SIZE="2"]picked up a refurbished 64bit ASUS laptop with an unofficial version of Vista, apparently was a floor model at Best Buy.  installed 64bit 9.04 leaving Vista intact for DVDs.  been a primary Ubuntu user for years, loaded all my stuff into the new system, got it set up nice, been running great for two weeks.
  
tonight decided to watch Blow and booted into Vista which was listed as 'Vista Loader' twice in the Grub menu.  should have known better... after a few seconds got a white screen with huge ERROR in red letters.  now restart gives Grub Error 22.  booted live CD and tried to fix via the usual threads: [COLOR="Green"][[COLOR="Green"]http://ubuntuforums.org/showthread.php?t=224351[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351"), [[COLOR="Green"]http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows[/COLOR]]("http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), [[COLOR="Green"]http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/[/COLOR]]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")[/COLOR] not much luck, lots of Error 15's.  and i haven't seen Ubuntu or Linux listed with any partition...
  
i can wipe/reinstall clean but figured it was worth asking if i can salvage my system first. [/SIZE]

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /boot/dev/stage1
find /boot/dev/stage1

Error 15: File not found
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> quit

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1402    11261533+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1403        9010    61105148    7  HPFS/NTFS
/dev/sda3            9011       23509   116463217+   f  W95 Ext'd (LBA)
/dev/sda5           16603       23509    55473148    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,523,129    22,523,067  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     22,523,904   144,734,199   122,210,296   7 HPFS/NTFS
/dev/sda3         144,745,650   377,672,084   232,926,435   f W95 Ext d (LBA)
/dev/sda5         266,723,328   377,669,623   110,946,296   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="RECOVERY" UUID="D476-EF15" TYPE="vfat" 
/dev/sda2: UUID="EC643B00643ACCD8" LABEL="Vista64" TYPE="ntfs" 
/dev/sda5: UUID="16943E64943E4711" LABEL="DATA" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/root type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/root type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /mnt type vfat (rw)
/dev/sda2 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda2: Location of files loaded by Grub: ===================


  23.5GB: boot/grub/stage2

=================== sda5: Location of files loaded by Grub: ===================


 148.5GB: boot/grub/stage2
```

[SIZE="2"]thanxs[/SIZE]

---

### Post by ceciliaFX on 2009-08-23
ok, I'm not SURE if this will help because I had a slightly different issue, so here goes (ya never know)

I had already installed Ubuntu 8.10 some months ago and had windows2000 - making my system mutiboot.

worked just fine, of course. I had left a partition ready for XP, but I didn't get around to installing that until last friday.

so, of course windowsXP messed up my grub, but my friends and I expected it.

well, we load up the live CD and boot ubuntu and from a terminal we type in the grub setup commands like normal.

only we get those "Error 15: File not found" responses.

it took a few moments until  my friend who is WAY smarter than I am in this regard figured out that he needed to NOT be in the GUI, but leave that and go into the basic shell. I forget the key strokes for this, but some clever person here probabaly knows it.

and once we were iin the shell, commands worked great, my grub was fixed and now I have a TRI-boot system

WOOT

---

### Post by dwdarkstar on 2009-08-23
thanxs for the reply ceciliaFX but i decided to just recover the Vista partition with Super Grub Disk and then rebuild the Ubuntu OS has i didn't have much on it anyway.  I will getting an external drive however and begin judicious system back-ups as i go along.  thanxs.

---

### Post by ceciliaFX on 2009-08-23
sure, hope everything works out ok

---

