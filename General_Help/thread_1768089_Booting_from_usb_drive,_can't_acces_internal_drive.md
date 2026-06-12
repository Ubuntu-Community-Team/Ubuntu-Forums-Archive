---
title: "Booting from usb drive, can't acces internal drive"
date: 2011-05-26
forum: General Help
---

### Post by klambert2010 on 2011-05-26
Hello,
I am new to linux and am having a problem accessing my hard drive.  I am running a hp dv701175nr laptop and am booting ubuntu 11.04 from a usb flash drive.  I can not seem to find my internal drive that has windows 7 stored on it.  I tried to mount it but it give me this error:

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

Please advise.  

I can't use this operating system if I can't access my windows 7 drive and I really want to use this OS :).

Thanks in advance,

Kevin

EDIT:  Okay, so I think I have found my problem, but I don't know how to fix it, there are differences in my mtab and fstab commands, I will post what they say in a second, but I do not know how or what I need to do to change and make the settings right

---

### Post by klambert2010 on 2011-05-26
kevin@Widowmaker:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=52b54d95-bd71-4e7f-a63b-3eef71be0b38 none            swap    sw              0       0


kevin@Widowmaker:~$ cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kevin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kevin 0 0
/dev/sdc1 /media/3236-6663 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0

---

### Post by klambert2010 on 2011-05-26
the difference that I can see is that in the mtab, something is labeled as sdb1 and fstab its labeled as sda1 and my drive is trying to mount onto sdb1, and it should be trying to mount on sda1.  Or something like that, I have searched around and have not been able to find a solution to my problem and I do not understand the terminal enough yet as I just installed this last night, in order to work through it myself.

Thanks

---

### Post by klambert2010 on 2011-05-26
Does anyone know of a solution for me?

---

### Post by ajgreeny on 2011-05-26
Have you been playing around editing the fstab or mtab files?  I ask because the partitions are normally seen in fstab with UUIDs and not device names such as /dev/sda1.   /etc/mtab seems to still use device names, to my surprise, I must admit.

Can you show the output of the command sudo blkid in terminal as it may simply need an edit of /etc/fstab to show the UUID and all may then be well.

---

### Post by klambert2010 on 2011-05-27
No I have not edited anything as I do not know how.  I am wanting to learn how.  The more I can do in Linux= the less i have to do in windows.

Here is the read out for sudo blkid

kevin@Widowmaker:~$ sudo blkid
[sudo] password for kevin: 
sudo /dev/sda1: UUID="94BC4C33BC4C11E2" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="B2EE7CCEEE7C8C7B" TYPE="ntfs" 
/dev/sdb1: UUID="d309ad46-f9e1-4edd-acbf-73623fca39d4" TYPE="ext4" 
/dev/sdb5: UUID="52b54d95-bd71-4e7f-a63b-3eef71be0b38" TYPE="swap"

---

### Post by klambert2010 on 2011-05-27
so my problem is in my fstab, where it says that the sda1 is called the ext4, it should be sdb1...i think.  So if that is the case, how do I edit that and then tell my disk utility to mount my internal drive to sda1?

---

### Post by jbowen7 on 2011-05-27
Hey Kevin,

can you please post the result of:

cat /etc/fstab



Things can go wrong when fstab is using scsi format ( sd{a,b,c} ) to identify a disk, it's best to identify with an UUID.

But first post /etc/fstab results

---

### Post by klambert2010 on 2011-05-27
kevin@Widowmaker:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=52b54d95-bd71-4e7f-a63b-3eef71be0b38 none            swap    sw              0       0

---

### Post by klambert2010 on 2011-05-27
all i did was install Ubuntu, so I have not edited anyhting yet.  If it works better to change to the UUID then I would rather use what works better, any help setting that up is appreciated.  Im like a sponge when it comes to htis stuff. I love to soak up information, its just kind of hard for me to understand and get started on it :(

---

### Post by jbowen7 on 2011-05-27
Also, if you just want to have quick access to these drives then:

Open a terminal and type in:


cd ~/Desktop && mkdir sda1 

mount /dev/sda1 ./sda1



The folder "sda1" is on your desktop, browse through it.

---

### Post by klambert2010 on 2011-05-27
okay, I now have a directory called sda1 on my desktop but it is empty and has 213 mb of free space, but my internal drive should have about 180 gigs of free space

So I was reading that post right around me about harddrive confusion and I read the thing about the bash script deal and did that.  So if it helps, here it is:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   601,198,591   601,198,529   7 NTFS / exFAT / HPFS
/dev/sda2         601,198,592   625,135,615    23,937,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8210 MB, 8210350080 bytes
253 heads, 62 sectors/track, 1022 cylinders, total 16035840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,653,375     7,651,328  83 Linux
/dev/sdb2           7,655,422    16,033,791     8,378,370   5 Extended
/dev/sdb5           7,655,424    16,033,791     8,378,368  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        94BC4C33BC4C11E2                       ntfs       
/dev/sda2        B2EE7CCEEE7C8C7B                       ntfs       HP_RECOVERY
/dev/sdb1        d309ad46-f9e1-4edd-acbf-73623fca39d4   ext4       
/dev/sdb5        52b54d95-bd71-4e7f-a63b-3eef71be0b38   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d309ad46-f9e1-4edd-acbf-73623fca39d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root d309ad46-f9e1-4edd-acbf-73623fca39d4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root d309ad46-f9e1-4edd-acbf-73623fca39d4
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d309ad46-f9e1-4edd-acbf-73623fca39d4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root d309ad46-f9e1-4edd-acbf-73623fca39d4
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d309ad46-f9e1-4edd-acbf-73623fca39d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root d309ad46-f9e1-4edd-acbf-73623fca39d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root d309ad46-f9e1-4edd-acbf-73623fca39d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=52b54d95-bd71-4e7f-a63b-3eef71be0b38 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.218048096 = 1.307869184    boot/grub/core.img                             1
   1.218063354 = 1.307885568    boot/grub/grub.cfg                             1
   1.821289062 = 1.955594240    boot/initrd.img-2.6.38-8-generic               6
   1.415348053 = 1.519718400    boot/vmlinuz-2.6.38-8-generic                  1
   1.821289062 = 1.955594240    initrd.img                                     6
   1.415348053 = 1.519718400    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by klambert2010 on 2011-05-27
okay so i figured it out.  Heres what I did in case anyone else ever has this problem.

gksu gedit /etc/fstab

That opened fstab in a text editor.

Then I changed the line that said:

/dev/sda1  ext4  

to 

/dev/sdb1  ext4

And then rebooted and everything works fine now

---

