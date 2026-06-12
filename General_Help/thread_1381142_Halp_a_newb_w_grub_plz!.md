---
title: "Halp a newb w/ grub plz!"
date: 2010-01-14
forum: General Help
---

### Post by wil3y on 2010-01-14
Hey im new to ubuntu and im havin a problem,
when my comp dual boots and i select windows via grub, it goes into the windows screen and then just black screens me.  i've already done the mbr repair process but its not fixing it. i have a different dual boot installed but it defaults to grub when i turn my comp on. it doesn't give me an error message or anything, it just wont load windows. any thoughts would be appreciated 
using karmic koala

vista x64

---

### Post by wil3y on 2010-01-14
fixed problem again via repair windows prompt in windows start-up repair, this is the second time it's happened though, and am hoping it wont happen again. if you can think of a reason why it's reoccuring please inform :D

---

### Post by drs305 on 2010-01-14
> **wil3y said:**
> fixed problem again via repair windows prompt in windows start-up repair, this is the second time it's happened though, and am hoping it wont happen again. if you can think of a reason why it's reoccuring please inform :D

Are you reinstalling Grub 2? You may be overwriting the Windows MBR information in doing so. 

For help in determining why you are having boot problems follow this thread to run the boot info script and post the results here (use the # symbol as explained in the link):
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

There is also this guide for dual booting, which offers solutions to non-booting in dual-boot systems:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by wil3y on 2010-01-14
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89900f6b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   352,771,334   352,769,287   7 HPFS/NTFS
/dev/sda2         352,771,335   475,186,634   122,415,300   5 Extended
/dev/sda5         352,771,398   470,110,094   117,338,697  83 Linux
/dev/sda6         470,110,158   475,186,634     5,076,477  82 Linux swap / Solaris
/dev/sda3         475,187,200   598,073,343   122,886,144   7 HPFS/NTFS
/dev/sda4         598,075,392   625,135,615    27,060,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4E401EBF5E239B86" TYPE="ntfs" 
/dev/sda3: UUID="1030EF4F30EF39FC" LABEL="Ubuntu 9.1.0" TYPE="ntfs" 
/dev/sda4: UUID="849C7D759C7D631A" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="066151cd-a89f-4b47-adc1-3596350710f2" TYPE="ext4" 
/dev/sda6: UUID="9e05c26e-f4fb-44f3-8688-cd35f972d2ad" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wil3y/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wil3y)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=wil3y)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 066151cd-a89f-4b47-adc1-3596350710f2
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 066151cd-a89f-4b47-adc1-3596350710f2
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=066151cd-a89f-4b47-adc1-3596350710f2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 066151cd-a89f-4b47-adc1-3596350710f2
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=066151cd-a89f-4b47-adc1-3596350710f2 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 066151cd-a89f-4b47-adc1-3596350710f2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=066151cd-a89f-4b47-adc1-3596350710f2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 066151cd-a89f-4b47-adc1-3596350710f2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=066151cd-a89f-4b47-adc1-3596350710f2 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4e401ebf5e239b86
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 849c7d759c7d631a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=066151cd-a89f-4b47-adc1-3596350710f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9e05c26e-f4fb-44f3-8688-cd35f972d2ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 180.6GB: boot/grub/core.img
 180.6GB: boot/grub/grub.cfg
 180.6GB: boot/initrd.img-2.6.31-14-generic
 180.6GB: boot/initrd.img-2.6.31-17-generic
 180.6GB: boot/vmlinuz-2.6.31-14-generic
 180.6GB: boot/vmlinuz-2.6.31-17-generic
 180.6GB: initrd.img
 180.6GB: initrd.img.old
 180.6GB: vmlinuz
 180.6GB: vmlinuz.old
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda1: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

i haven't reinstalled grub2 as of yet.
thanks for the help, it is appreciated :D

---

