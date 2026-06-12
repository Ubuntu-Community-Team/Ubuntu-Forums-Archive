---
title: "Grub of Wubi Ubuntu lost after Windows 7 Installation"
date: 2012-05-17
forum: General Help
---

### Post by sotstas on 2012-05-17
Hello everybody!

I am having a common problem when you install Windows 7, my grub thus my ability to boot into my Wubi Ubuntu got lost and now I only get directed to Windows 7.

I want my grub back and I tried the known solution of making a LiveUSB, booting through that, running the boot info script (I display it below) then while running it, I got a message 
Unable to open a folder for 18 GB Filesystem
No application is registered as handling this file

The 18GB Filesystem is my Wubi.

In any case, I tried to do it the way I knew it, I run the commands:
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
It finished with no mistakes, but I still don't get to see grub when I start my laptop. It gives me some option to start Windows Startup Repair which is doing crap...

Any suggestions? Please, any help would be great, since I also need this to be solved asap.

Thx, Sotiris
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sdb1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30286 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   472,254,463   472,254,401   7 NTFS / exFAT / HPFS
/dev/sda2         472,254,464   488,390,655    16,136,192   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3980 MB, 3980394496 bytes
255 heads, 63 sectors/track, 483 cylinders, total 7774208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *            128     7,774,207     7,774,080   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        58B87CF8B87CD5CA                       ntfs       
/dev/sda2        AE0A68520A68199B                       ntfs       HP_RECOVERY
/dev/sdb1        E48883EE8883BE14                       ntfs       DATA
/dev/sdc1        0913-0616                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/58B87CF8B87CD5CA  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

======================== sdb1/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root E48883EE8883BE14
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root E48883EE8883BE14
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root E48883EE8883BE14
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=E48883EE8883BE14 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BA06A9BB06A978D1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root AE0A68520A68199B
    chainloader +1
}
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

============================= sdb1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdb1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-28-generic              2
               =                boot/initrd.img-2.6.38-10-generic              2
               =                boot/initrd.img-2.6.38-11-generic              2
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.35-28-generic                 2
               =                boot/vmlinuz-2.6.38-10-generic                 1
               =                boot/vmlinuz-2.6.38-11-generic                 2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by sotstas on 2012-05-17
Please, somebody?

---

### Post by Frogs Hair on 2012-05-17
Wubi installs in a folder inside the Windows partition and uses the Windows boot loader for operating system selection. On earlier versions of Wubi grub would appear after Ubuntu was selected from the Windows boot loader.The kernels and other options were displayed. I don't if Wubi still works this way.

Normally Windows would be installed first in order to use Wubi and you wrote in the title 'lost after Windows 7 installation". I'm a bit confused about this. Are you missing the Ubuntu option in the Windows boot loader ?

---

### Post by sotstas on 2012-05-17
Hello Frogs Hair and thanx for your time.

After I installed Windows 7 every time I boot I don't get any booting option between Windows and Ubuntu as I used to in the past. It just boots into Windows 7.

In short, the grub is not working or it has been overwritten?

At the time I have 2 main partitions, 1 where Windows Vista was installed and in which I installed Windows 7 and the other where I had the Wubi 18GB files. Now, I still have the Wubi 'Ubuntu' files in my second partition, but I cannot boot into Ubuntu.

---

### Post by wilee-nilee on 2012-05-17
> **sotstas said:**
> Hello Frogs Hair and thanx for your time.

After I installed Windows 7 every time I boot I don't get any booting option between Windows and Ubuntu as I used to in the past. It just boots into Windows 7.

In short, the grub is not working or it has been overwritten?

You have a strange setup that will be helped with you explaining a little more. A wubi would not be in a ext4 partition, it would just be a file in windows.

sdb1/Wubi:        File system:       ext4     Boot sector type:  -     Boot sector info:      Operating System:  Ubuntu 11.04     Boot files:        /boot/grub/grub.cfg /etc/fstab

Also grub is not completely used in the way it would be in a partitioned install, that is installed from a booted cd or usb thumb, rather than installed from windows.

Did you transfer a wubi to the sdb1 partition, and have a wubi still installed in the XP setup?

---

### Post by critin on 2012-05-17
Wubi is a Windows app that runs inside Windows.  If you lose or reinstall Windows, you lose wubi.   Wubi is a Windows Ubuntu Installer.

You will need to reinstall wubi.

---

### Post by sotstas on 2012-05-17
I edited my last post, but I guess maybe I should explain better.

I was using Windows Vista and having two partitions on my hard drive C and D, with Windows being on C and D being a DATA partition.

I installed Wubi taking space from partition D and it was working perfectly fine with Grub starting whenever I booted and giving me to option to boot between Vista and Ubuntu.

Now I decided to install Windows 7, so I formatted the entire partition C and installed Windows 7 on it. I checked the partition D and the folder 'Ubuntu' is still there like it was before.

However, I get no option to boot into Ubuntu in the beginning. I don't know how else to explain it. Also, I don't know if I did something wrong when installing Windows 7.

Any troubleshooting ideas?

---

### Post by wilee-nilee on 2012-05-17
> **sotstas said:**
> I edited my last post, but I guess maybe I should explain better.

I was using Windows Vista and having two partitions on my hard drive C and D, with Windows being on C and D being a DATA partition.

I installed Wubi taking space from partition D and it was working perfectly fine with Grub starting whenever I booted and giving me to option to boot between Vista and Ubuntu.

Now I decided to install Windows 7, so I formatted the entire partition C and installed Windows 7 on it. I checked the partition D and the folder 'Ubuntu' is still there like it was before.

However, I get no option to boot into Ubuntu in the beginning. I don't know how else to explain it. Also, I don't know if I did something wrong when installing Windows 7.

Any troubleshooting ideas?

There is only about one user on the forums that probably can fix this and understand what is going on here, maybe another a mod.

So to get started post in the wubi mega thread a heads up to this thread, and post your bootscript there as well.

[http://ubuntuforums.org/showthread.php?t=1639198&page=14](http://ubuntuforums.org/showthread.php?t=1639198&page=14)

---

### Post by sotstas on 2012-05-17
So there is no way of retrieving my old documents?

I can still see the root.disk and swap.disk in my Ubuntu/disks folder in D.

---

### Post by wilee-nilee on 2012-05-17
> **sotstas said:**
> So there is no way of retrieving my old documents?

I can still see the root.disk and swap.disk in my Ubuntu/disks folder in D.

I think this can be fixed, it just needs the right people to look at it, saw your post in the megathread, so crack a cold one and relax, you will get the help needed. :)

---

### Post by sotstas on 2012-05-17
Thank you Computeratin for your eagerness to help.

Since wilee-nilee here says that it is kind of more complicated, I will wait to see if someone more experienced and especially in Wubi is involved. 
I wouldn't like to start trying things if there is something specific I could do to regain my former Wubi status.

Luckily, the beans never lie...

---

### Post by JKyleOKC on 2012-05-17
Since your "Ubuntu" folder is still intact on your D: drive, your data in it is intact. This folder serves as a "virtual disk" in which the Ubuntu system is installed.

If the system-selection screen that you used to see was in all capital letters, it came from the Windows "boot.ini" file that was part of XP and, I think, Vista. Installing Win7 did away with that file and lost the choice.

Re-installing wubi would put the choice dialog back, but would also overwrite your data unless you told it to install to drive C instead of D -- and in that case would give you a brand new installation rather than using your existing one. Neither option seems very desirable.

I'm sure there's a way to re-create the "boot.ini" equivalent in Win7 and regain access to your Ubuntu installation, but since I've not used Windows since XP I don't know enough about it to be much help other than pointing out a general direction in which to proceed... Good luck!

---

### Post by critin on 2012-05-17
If grub could be reinstalled because it was overwritten by Win7,  using Boot Repair on a live cd will do that.   

See this wiki for info on installing on its own partition--did you do this?  If not, wubi is gone and must be reinstalled.

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29")

---

### Post by CharlesA on 2012-05-17
Hi,

Because this is a wubi install, it does **not** use GRUB - it uses the Windows boot loader.

Just wanted to clear that up.

Charles

---

### Post by computeratin on 2012-05-17
> **critin said:**
> ... If not, wubi is gone and must be reinstalled.
 
Not according to [How To Geek]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/"). They say you can rebuild it.
 
BUT, ONCE AGAIN, DON'T JUST JUMP IN TO THIS!!! I'M TRYING TO HELP YOU WITH RESEARCH, NOT DIRECTIONS!!! IF YOU DECIDE TO GO THE WIN WAY THEN READ ALL OF THE COMMENTS AT THE BOTTOM OF THE PAGE, THIS DIDN'T "JUST WORK" FOR SOME PEOPLE!
 
TALK TO PEOPLE HERE, GET ADVICE FROM THE WUBI THREAD, AND GET READY TO DO LOTS OF RESEARCH.
 
I BUILD CUSTOM, TWEAKED, CRAZY SYSTEMS MYSELF. I ALMOST NEVER FIND ANYBODY WITH THE WHOLE ANSWER. USUALLY I END UP HAVING TO TAKE 2,3,4 ANSWERS FROM DIFFERNT SOURCES, COMBINING THEM AND FIGURING IT OUT FOR MYSELF.
 
Welcome to the wonderful world of custom computing.

---

### Post by westie457 on 2012-05-17
No magic answer from me. This part is puzzling me atm > After I installed Windows 7 every time I boot I don't get any booting option between Windows and Ubuntu as I used to in the past. It just boots into Windows 7.


The Windows 7 installer should at have picked the other Windows installations and made them available to you at computer boot time ie given you a choice of which Windows to start.

If you do get that choice try booting XP to see what happens.

If you do not get that choice then as everyone here is saying it is a very complicated situation.

---

### Post by critin on 2012-05-17
> **sotstas said:**
> Wubi status.

Luckily, the beans never lie...

:confused:     bean counts simply show the quantity of posts--not the quality of posts.  

They are fun.   :lolflag:

---

### Post by CharlesA on 2012-05-17
> **computeratin said:**
> Not according to [How To Geek]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/"). They say you can rebuild it.
 
BUT, ONCE AGAIN, DON'T JUST JUMP IN TO THIS!!! I'M TRYING TO HELP YOU WITH RESEARCH, NOT DIRECTIONS!!! IF YOU DECIDE TO GO THE WIN WAY THEN READ ALL OF THE COMMENTS AT THE BOTTOM OF THE PAGE, THIS DIDN'T "JUST WORK" FOR SOME PEOPLE!
 
TALK TO PEOPLE HERE, GET ADVICE FROM THE WUBI THREAD, AND GET READY TO DO LOTS OF RESEARCH.
 
I BUILD CUSTOM, TWEAKED, CRAZY SYSTEMS MYSELF. I ALMOST NEVER FIND ANYBODY WITH THE WHOLE ANSWER. USUALLY I END UP HAVING TO TAKE 2,3,4 ANSWERS FROM DIFFERNT SOURCES, COMBINING THEM AND FIGURING IT OUT FOR MYSELF.
 
Welcome to the wonderful world of custom computing.
Friendly note:

Watch the CAPS. It can be seen as shouting. If you want to emphasize something, use **bold** or *italics*.

Thank you.

---

### Post by bcbc on 2012-05-17
I posted a couple things on the megathread. 

Getting data off the root.disk: [http://ubuntuforums.org/showpost.php?p=11944482&postcount=1040](http://ubuntuforums.org/showpost.php?p=11944482&postcount=1040)

Getting a wubi install to boot again after reinstalling windows: [http://ubuntuforums.org/showpost.php?p=11944531&postcount=1041](http://ubuntuforums.org/showpost.php?p=11944531&postcount=1041)

---

### Post by JKyleOKC on 2012-05-17
> **bcbc said:**
> Getting a wubi install to boot again after reinstalling windows: [http://ubuntuforums.org/showpost.php?p=11944531&postcount=1041](http://ubuntuforums.org/showpost.php?p=11944531&postcount=1041)This looks like the really elegant way to solve the problem. Forcing the wubi installer to fix up the "boot.ini" information should do the trick with no danger at all to the original data, so long as you rename the folder first and then reboot after doing so just to make certain that all Windows information has been updated to reflect the change.

---

