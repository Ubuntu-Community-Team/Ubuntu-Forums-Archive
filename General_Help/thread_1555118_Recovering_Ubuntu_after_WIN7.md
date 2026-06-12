---
title: "Recovering Ubuntu after WIN7"
date: 2010-08-17
forum: General Help
---

### Post by schoft on 2010-08-17
Hi. I tried to follow this guide ( [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) ) BUt its way too complicated for me. I tought i was doing it right but im getting these error messages:

root@ubuntu:~# sudo grub-install --root-directory=/media/de76f14f-2988-4e21-a3fb-a491e19c7341 /dev/sdb
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

My setup:

```
                Boot Info Script 0.55    dated February 15th, 2010                    
 
 ============================= Boot Info Summary: ==============================
 
  => Windows is installed in the MBR of /dev/sda
  => Windows is installed in the MBR of /dev/sdb
 
 sda1: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows XP
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows XP
     Boot files/dirs:   /boot.ini /ntldr
 
 sdb1: _________________________________________________________________________
 
     File system:       ext4
     Boot sector type:  -
     Boot sector info:  
     Operating System:  Ubuntu 9.10
     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
 sdb2: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  
     Boot files/dirs:   /bootmgr /Boot/BCD
 
 sdb3: _________________________________________________________________________
 
     File system:       ntfs
     Boot sector type:  Windows Vista/7
     Boot sector info:  No errors found in the Boot Parameter Block.
     Operating System:  Windows 7
     Boot files/dirs:   /Windows/System32/winload.exe
 
 sdb4: _________________________________________________________________________
 
     File system:       Extended Partition
     Boot sector type:  -
     Boot sector info:  
 
 sdb5: _________________________________________________________________________
 
     File system:       swap
     Boot sector type:  -
     Boot sector info:  
 
 =========================== Drive/Partition Info: =============================
 
 Drive: sda ___________________ _____________________________________________________
 
 Disk /dev/sda: 500.1 GB, 500107862016 bytes
 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Disk identifier: 0xc922c922
 
 Partition  Boot         Start           End          Size  Id System
 
 /dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS
 
 
 Drive: sdb ___________________ _____________________________________________________
 
 Disk /dev/sdb: 160.0 GB, 160041885696 bytes
 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Disk identifier: 0x36e1f639
 
 Partition  Boot         Start           End          Size  Id System
 
 /dev/sdb1                  63   114,527,384   114,527,322  83 Linux
 /dev/sdb2    *    114,528,256   114,733,055       204,800   7 HPFS/NTFS
 /dev/sdb3         114,733,056   299,804,671   185,071,616   7 HPFS/NTFS
 /dev/sdb4         299,805,030   312,576,704    12,771,675   5 Extended
 /dev/sdb5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris
 
 
 blkid -c /dev/null: ____________________________________________________________
 
 Device           UUID                                   TYPE       LABEL                         
 
 /dev/loop0                                              squashfs                                 
 /dev/sda1        0010841710841636                       ntfs       Lokaal station                
 /dev/sdb1        de76f14f-2988-4e21-a3fb-a491e19c7341   ext4                                     
 /dev/sdb2        A288A40588A3D5D7                       ntfs       System Reserved               
 /dev/sdb3        C262AA6962AA61C1                       ntfs                                     
 /dev/sdb5        4d330b9d-fa13-4428-b8dc-5117cd064835   swap                                     
 
 ============================ "mount | grep ^/dev  output: ===========================
 
 Device           Mount_Point              Type       Options
 
 aufs             /                        aufs       (rw)
 /dev/sr0         /cdrom                   iso9660    (rw)
 /dev/loop0       /rofs                    squashfs   (rw)
 /dev/sdb1        /media/de76f14f-2988-4e21-a3fb-a491e19c7341 ext4       (rw,nosuid,nodev,uhelper=devkit)
 /dev/sdb3        /media/C262AA6962AA61C1  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
 /dev/sdb2        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
 /dev/sda1        /media/Lokaal station    fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
 
 
 ================================ sda1/boot.ini: ================================
 
 [boot loader] 
 timeout=30 
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 [operating systems] 
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
 
 =========================== sdb1/boot/grub/grub.cfg: ===========================
 
 #
 # DO NOT EDIT THIS FILE
 #
 # It is automatically generated by /usr/sbin/grub-mkconfig using templates
 # from /etc/grub.d and settings from /etc/default/grub
 #
 
 ### BEGIN /etc/grub.d/00_header ###
 if [ -s /boot/grub/grubenv ]; then
   have_grubenv=true
   load_env
 fi
 set default="0"
 if [ ${prev_saved_entry} ]; then
   saved_entry=${prev_saved_entry}
   save_env saved_entry
   prev_saved_entry=
   save_env prev_saved_entry
 fi
 insmod ext2
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
 if loadfont /usr/share/grub/unicode.pf2 ; then
   set gfxmode=640x480
   insmod gfxterm
   insmod vbe
   if terminal_output gfxterm ; then true ; else
     # For backward compatibility with versions of terminal.mod that don't
     # understand terminal_output
     terminal gfxterm
   fi
 fi
 if [ ${recordfail} = 1 ]; then
   set timeout=-1
 else
   set timeout=10
 fi
 ### END /etc/grub.d/00_header ###
 
 ### BEGIN /etc/grub.d/05_debian_theme ###
 set menu_color_normal=white/black
 set menu_color_highlight=black/white
 ### END /etc/grub.d/05_debian_theme ###
 
 ### BEGIN /etc/grub.d/10_linux ###
 menuentry "Ubuntu, Linux 2.6.31-21-generic" {
         recordfail=1
         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
     set quiet=1
     insmod ext2
     set root=(hd0,1)
     search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
     linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro   quiet splash
     initrd    /boot/initrd.img-2.6.31-21-generic
 }
 menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
         recordfail=1
         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
     insmod ext2
     set root=(hd0,1)
     search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
     linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro single 
     initrd    /boot/initrd.img-2.6.31-21-generic
 }
 menuentry "Ubuntu, Linux 2.6.31-14-generic" {
         recordfail=1
         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
     set quiet=1
     insmod ext2
     set root=(hd0,1)
     search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
     linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro   quiet splash
     initrd    /boot/initrd.img-2.6.31-14-generic
 }
 menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
         recordfail=1
         if [ -n ${have_grubenv} ]; then save_env recordfail; fi
     insmod ext2
     set root=(hd0,1)
     search --no-floppy --fs-uuid --set de76f14f-2988-4e21-a3fb-a491e19c7341
     linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 ro single 
     initrd    /boot/initrd.img-2.6.31-14-generic
 }
 ### END /etc/grub.d/10_linux ###
 
 ### BEGIN /etc/grub.d/20_memtest86+ ###
 menuentry "Memory test (memtest86+)" {
     linux16    /boot/memtest86+.bin
 }
 menuentry "Memory test (memtest86+, serial console 115200)" {
     linux16    /boot/memtest86+.bin console=ttyS0,115200n8
 }
 ### END /etc/grub.d/20_memtest86+ ###
 
 ### BEGIN /etc/grub.d/30_os-prober ###
 if [ ${timeout} != -1 ]; then
   if keystatus; then
     if keystatus --shift; then
       set timeout=-1
     else
       set timeout=0
     fi
   else
     if sleep --interruptible 3 ; then
       set timeout=0
     fi
   fi
 fi
 ### END /etc/grub.d/30_os-prober ###
 
 ### BEGIN /etc/grub.d/40_custom ###
 # This file provides an easy way to add custom menu entries.  Simply type the
 # menu entries you want to add after this comment.  Be careful not to change
 # the 'exec tail' line above.
 ### END /etc/grub.d/40_custom ###
 
 =============================== sdb1/etc/fstab: ===============================
 
 # /etc/fstab: static file system information.
 #
 # Use 'blkid -o value -s UUID' to print the universally unique identifier
 # for a device; this may be used with UUID= as a more robust way to name
 # devices that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 # / was on /dev/sda1 during installation
 UUID=de76f14f-2988-4e21-a3fb-a491e19c7341 /               ext4    errors=remount-ro 0       1
 # swap was on /dev/sda5 during installation
 UUID=4d330b9d-fa13-4428-b8dc-5117cd064835 none            swap    sw              0       0
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
 /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
 
 =================== sdb1: Location of files loaded by Grub: ===================
 
 
   13.0GB: boot/grub/core.img
   13.0GB: boot/grub/grub.cfg
     .2GB: boot/initrd.img-2.6.31-14-generic
   38.4GB: boot/initrd.img-2.6.31-21-generic
     .2GB: boot/vmlinuz-2.6.31-14-generic
     .2GB: boot/vmlinuz-2.6.31-21-generic
   38.4GB: initrd.img
     .2GB: initrd.img.old
     .2GB: vmlinuz
     .2GB: vmlinuz.old
``` :mad:

---

### Post by schoft on 2010-08-17
Bump :p

---

### Post by ranch hand on 2010-08-17
Well, first off, did you check your device  map?  Should be /boot/grub/device.map.

A good place to start.

---

### Post by schoft on 2010-08-17
I did not. Let me check :D

```
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0010841710841636" LABEL="Lokaal station" TYPE="ntfs" 
/dev/sdb1: UUID="de76f14f-2988-4e21-a3fb-a491e19c7341" TYPE="ext4" 
/dev/sdb2: UUID="A288A40588A3D5D7" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdb3: UUID="C262AA6962AA61C1" TYPE="ntfs" 
/dev/sdb5: UUID="4d330b9d-fa13-4428-b8dc-5117cd064835" TYPE="swap" 
``````
root@ubuntu:~# cat /etc/fstab 
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
```

---

### Post by schoft on 2010-08-17
> **ranch hand said:**
> Well, first off, did you check your device  map?  Should be /boot/grub/device.map.

A good place to start.

```
# cat device.map
(hd0)    /dev/sda
```

---

### Post by wilee-nilee on 2010-08-17
Assuming here that as of now XP is booting even though spread between two HD with the boot and OS.

What you need is this which was a link from your original.
Just reinstall Grub2 in the same hard drive as Ubuntu with a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You don't mention the use of easybcd so I assume you want grub back.

---

### Post by schoft on 2010-08-17
Hey. Thanks for the reply. I havent used XP in 6 years. XP is on another HDD, that i only use for storage.

Not sure what easybcd is but i might have used that a year ago when i was trying this, the same thing.

Ill post updates here :)

---

### Post by ranch hand on 2010-08-17
I think you have a problem with your device map.  It only lists sda.  Put;
```

(hd1)   dev/sdb

```
in there too.

If you do not use MS then having it installed on both MBRs is just not right.

Use this set of instructions, ignoring the part about editing files;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Do the grub-install part twice, one for sda and another for sdb,  I would run update-grub before AND after the 2 grub-installs.

After you boot into Kinky Kitty (9.10) run update-grub again.  This may actually pick up your MS install.  If not, and you want such an entry you can put one in /etc/grub.d/40_custom.

What it is supposed to look like is beyond me.  Will not have MS in the house to pollute my boxes.  Fine with me if you  do, but I don't and therefore do not know the entry for any of their versions.

---

### Post by schoft on 2010-08-17
Hey. I'm getting stuck with some errors. In the guide, it says i should do this:

"When that is done you need to run **update-grub** to create the configuration file. [B]If you have a separate /boot partition you need to mount it first!"

[/B]```
sudo update-grub
grub-probe: error: cannot find a device for /.

```my device map:

```
ubuntu@ubuntu:/mnt/boot$ cat /boot/grub/device.map 
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb

```Note that im using a LiveCD. Wont /boot/grub/device.map be on the livecd's cache ? Or is that correct?

Here is the complete process:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc922c922

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36e1f639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7129    57263661   83  Linux
/dev/sdb2   *        7130        7142      102400    7  HPFS/NTFS
/dev/sdb3            7142       18662    92535808    7  HPFS/NTFS
/dev/sdb4           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt/boot
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc922c922

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36e1f639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7129    57263661   83  Linux
/dev/sdb2   *        7130        7142      102400    7  HPFS/NTFS
/dev/sdb3            7142       18662    92535808    7  HPFS/NTFS
/dev/sdb4           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt/boot
fuse: mount failed: Device or resource busy
ubuntu@ubuntu:~$ cd /mnt/boot
ubuntu@ubuntu:/mnt/boot$ ls -l
total 388
drwx------ 1 ubuntu ubuntu   4096 2010-05-03 03:50 Boot
-rwxrwxrwx 1 ubuntu ubuntu 383562 2009-07-14 01:38 bootmgr
-rwxrwxrwx 1 ubuntu ubuntu   8192 2010-05-03 03:50 BOOTSECT.BAK
drwx------ 1 ubuntu ubuntu      0 2010-08-18 02:48 grub
drwx------ 1 ubuntu ubuntu      0 2010-05-03 02:52 System Volume Information
ubuntu@ubuntu:/mnt/boot$ sudo update-grub
grub-probe: error: cannot find a device for /.




```Also, ignore my XP. I dont want it. I dont use it. I have a C:\ ( /dev/sdb3 ) with windows 7 on it. I've got D:\ wich is sda1which we can totally ignore. I want ubuntu on /dev/sdb1. /dev/sdb2 is the system reserve (boot). it looks like this:

```
$ ls /media/System\ Reserved/
Boot  bootmgr  BOOTSECT.BAK  grub  System Volume Information

```In the folder is also a device.map

```
$ cat /media/System\ Reserved/grub/device.map 
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb

```

I continue anyway

```

ubuntu@ubuntu:/mnt/boot$ sudo grub-install /dev/sdb1
grub-probe: error: cannot find a device for /boot/grub.
No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:/mnt/boot$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

Clueless I am.

---

### Post by schoft on 2010-08-17
This should be a piece of cake for someone :)

---

### Post by wilee-nilee on 2010-08-17
From the live cd run.
```
sudo mount /dev/sdb1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot then choose Ubuntu run sudo update-grub to add W7 to grub.

Make sure sdb is the first HD to be read in bios.

---

### Post by oldfred on 2010-08-17
You are mixing up windows boot partition with Ubuntu. The windows boot/recovery partition sdb2 approx 100mb is just for win7.

Now you have grub in the windows partition sdb2 and that will confuse windows. You will have to delete that.
You should not mount this as it is windows only:
sudo mount /dev/sdb2 /mnt/boot

Install MBR from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sdb's MBR:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

Then in BIOS select to boot sdb, since both drives are 500GB you may have to try both to be sure of which is which.

---

### Post by ranch hand on 2010-08-18
And you need to look in the installed OS for your device map, not the CDs.

Never install on anything but the drive, not a partition.  Sda, sdb not sda1 or sdbwhatever.

---

### Post by schoft on 2010-08-18
Got it to work , thanks loads :)

---

