---
title: "Help! GRUB/Windows Bootloader"
date: 2009-12-09
forum: General Help
---

### Post by Skinnybill on 2009-12-09
First of all, dont tell me 'oh go search google' i have and it hasnt helped.
--
Ok basically i need some sort of tutorial on how to use the Windows bootloader instead of GRUB. I have already googled and i cant find the solution.

What i want is to:
Make the Windows Boot Loader appear instead of GRUB.
NOTE: I have windows 7, there is no boot.ini, you have to use bcdedit.exe 

If neccesary, make the windows bootloader boot GRUB to then boot Ubuntu.
--
so basically, how do i make the Windows bootloader appear instead of grub, and how to put Ubuntu (or GRUB) onto the windows bootloader.
NOTE: Windows and Ubuntu are not partitioned. They are installed on seperate drives. Windows is on drive 0 and Ubuntu is on Drive 1 (I have 2 seperate HD's in my computer)

i really will apreciate any help you can provide.

Thanks, Skinnybill

---

### Post by rahilm on 2009-12-09
oh go search google

---

### Post by nacho32 on 2009-12-09
if you are using the easy BCD-1.73 it's pretty simple just point the boot in the configuration option. I use it on a triple boot with like yours each OS installed on a separate HD just configure easy BSD to point to each OS and each drive save and it should work. You might have to fix the MBR first in Windows 7 but the BSD should over right it. In what your trying to do it's easyer just to install windows 7 after Ubuntu if you dont want the grub to appear over Windows boot screen

---

### Post by rugbywarrior on 2009-12-22
Hello, I have a BIG problem.  I had some games that don't like wine too much so I put windows onto my computer.  We all know what happened, windows removed grub and took over my cpu, Grrrr...  So anyway, I created a copy of xubuntu 9.10 and loaded it up.  after a lottle bit of grief, it finally worked doing the whole grub, root (hd0,0) setup (hd0) exit thing.  I thought I was in the clear, then when I rebooted it said starting grub stage 1.5 blah, blah, blah, error 2.  I did some research and found that it means that grub can't find the files it needs to load.  I put the live CD back in and now it can't find (hd0).  All other posts don't seem to be axactly what I'm looking for so I decided to run boot info script and post it here in the hopes that someone can help me! so her goes
```

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b8387

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   513,790,829   513,790,767  83 Linux
/dev/sda2    *    513,790,830   613,120,724    99,329,895   7 HPFS/NTFS
/dev/sda3         613,120,725   625,137,344    12,016,620   5 Extended
/dev/sda5         613,120,788   625,137,344    12,016,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="711f64d5-a212-4506-b2a9-27a0abcdb7b6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="8A48BBCD48BBB5F3" TYPE="ntfs" 
/dev/sda5: UUID="f963d428-3fc5-4c59-96cb-26adba7ca458" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)


=========================== sda1/boot/grub/menu.lst: ===========================

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Mon Dec 21 10:46:02 2009
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
gfxmenu /boot/grub/deep_stage1
# End GRUB global section
# Linux bootable partition config begins
  title Linux (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/sda1 ro vga=normal
# Linux bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/sda2)
  map (hd0,0) (hd0,1)
  map (hd0,1) (hd0,0)
  rootnoverify (hd0,1)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable initrd config begins
  title Linux initrd /tmp/boot/boot/initrd.img-2.6.31-16-generic (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/sda1 ramdisk_size=18793 root=/dev/ram0 rw
  initrd /tmp/boot/boot/initrd.img-2.6.31-16-generic
# Linux bootable initrd config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,0)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/sda1)
root (hd0,0)
setup (hd0,0)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=711f64d5-a212-4506-b2a9-27a0abcdb7b6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f963d428-3fc5-4c59-96cb-26adba7ca458 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

```

Please help me

---

### Post by oldfred on 2009-12-22
rugbywarrior, You should start a new thread with your problem as more people look at those with low counts.

You have a very customized menu.lst?

Your linux entry is minimal does it work?
Your map commands for windows are not required and are wrong. Map is just to switch hard drives as windows wants to be on the first hard drive.
This was my entry for a 4th drive's windows:
map        (hd0) (hd3)
map        (hd3) (hd0)

You could back up or rename your menu.lst and let update-grub create a new one that should work.

---

### Post by Yogotiss on 2009-12-22
If you want window's boot-loader to take over you have to install Ubuntu inside the windows environment. Pretty much Wubi install.

---

