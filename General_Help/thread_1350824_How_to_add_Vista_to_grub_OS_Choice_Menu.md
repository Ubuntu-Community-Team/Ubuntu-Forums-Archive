---
title: "How to add Vista to grub OS Choice Menu?"
date: 2009-12-09
forum: General Help
---

### Post by madmax.santana on 2009-12-09
Ok I was playing around and I messed up. First I was looking to add splash images to grub. It didn't work out with grub2 and I thought maybe  should test it first on legacy grub. I purged the grub2 configuration files and grub-common and grub-osprober and reinstalled legacy grub. Then I installed it on my sda1 partition by using grub-install command. All worked well till here.
Then I ran update grub and everything. But it didn't read my vista partition. I tried to add it manually to my menu.lst but when I select the Windows Vista option it says something about initializing grub stage 2 and then grub restarts. I cannot boot on my vista partition. Please help I am in lot of trouble if I don't get it fixed very soon.

Here is my menu.lst file.

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=195c5259-a096-42f3-b08d-5576c9d077fe

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

[B]title        Microsoft Windows Vista Home Basic
root        (hd0,0)
makeactive
chainloader     +1
[/B] 
title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Leppie on 2009-12-09
could you post the output of "fdisk -l"?

---

### Post by madmax.santana on 2009-12-09
There you go.
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x788faa65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19980   160487392    7  HPFS/NTFS
/dev/sda2           19980       25080    40960000    7  HPFS/NTFS
/dev/sda3           25080       30179    40960000    7  HPFS/NTFS
/dev/sda4           30179       38913    70160225    f  W95 Ext'd (LBA)
/dev/sda5           30179       34542    35046400    7  HPFS/NTFS
/dev/sda6           34543       35757     9759456   83  Linux
/dev/sda7           35758       38189    19535008+  83  Linux
/dev/sda8           38190       38913     5815498+  82  Linux swap / Solaris

---

### Post by zwygart on 2009-12-09
Please post the output of the script at 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Leppie on 2009-12-09
I'm not so very familiar with grub-legacy. I kinda skipped from lilo to grub2.

Try to do a update-grub (this should reconfigure grub) and see if you can boot normally again.

Edit:
Are you by any chance on an HP or Dell? You may want to have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1341624").

---

### Post by madmax.santana on 2009-12-09
Nope. update-grub doesn't even mention windows or any non-linux os anywhere. And no normal booting.

---

### Post by madmax.santana on 2009-12-09
**@zwygart**

> ============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 556026541 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x788faa65

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   320,974,846   320,974,784   7 HPFS/NTFS
/dev/sda2         320,974,848   402,894,847    81,920,000   7 HPFS/NTFS
/dev/sda3         402,894,848   484,814,847    81,920,000   7 HPFS/NTFS
/dev/sda4         484,816,895   625,137,344   140,320,450   f W95 Ext d (LBA)
/dev/sda5         484,816,896   554,909,695    70,092,800   7 HPFS/NTFS
/dev/sda6         554,917,293   574,436,204    19,518,912  83 Linux
/dev/sda7         574,436,268   613,506,284    39,070,017  83 Linux
/dev/sda8         613,506,348   625,137,344    11,630,997  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="12F45A8AF45A6FC9" LABEL="Volume" TYPE="ntfs" 
/dev/sda3: UUID="0870915670914B78" LABEL="Volume" TYPE="ntfs" 
/dev/sda5: UUID="1C1CEB391CEB0C98" LABEL="Volume" TYPE="ntfs" 
/dev/sda6: UUID="195c5259-a096-42f3-b08d-5576c9d077fe" TYPE="ext4" 
/dev/sda7: UUID="43293dfd-0ea3-4b2b-b8de-818c745cda68" TYPE="ext4" 
/dev/sda8: UUID="0c8411f6-abc4-41f8-a768-317c4fd3cc25" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/madmax/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=madmax)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=195c5259-a096-42f3-b08d-5576c9d077fe

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

title        Microsoft Windows Vista Home Basic
root        (hd0,0)
makeactive
chainloader     +1

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        195c5259-a096-42f3-b08d-5576c9d077fe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
  set timeout=1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
insmod png
if background_image /usr/share/images/desktop-base/GrubWall.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/blue
  set menu_color_highlight=blue/cyan
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_title ###

menuentry "GRUB: Welcome to Mario's Mean Machine" {
}

menuentry "Please select the desired OS from the menu below" {
}

menuentry " "{
}

### END /etc/grub.d/06_title ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 195c5259-a096-42f3-b08d-5576c9d077fe
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=195c5259-a096-42f3-b08d-5576c9d077fe ro single 
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
    search --no-floppy --fs-uuid --set 6a68d46068d42d17
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=195c5259-a096-42f3-b08d-5576c9d077fe /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=43293dfd-0ea3-4b2b-b8de-818c745cda68 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=0c8411f6-abc4-41f8-a768-317c4fd3cc25 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 284.1GB: boot/grub/grub.cfg
 284.1GB: boot/grub/menu.lst
 284.1GB: boot/grub/stage2
 284.1GB: boot/initrd.img-2.6.31-14-generic
 284.1GB: boot/initrd.img-2.6.31-15-generic
 284.1GB: boot/initrd.img-2.6.31-16-generic
 284.1GB: boot/vmlinuz-2.6.31-14-generic
 284.1GB: boot/vmlinuz-2.6.31-15-generic
 284.1GB: boot/vmlinuz-2.6.31-16-generic
 284.1GB: initrd.img
 284.1GB: initrd.img.old
 284.1GB: vmlinuz
 284.1GB: vmlinuz.old

---

### Post by zwygart on 2009-12-09
As a overview, I see that you have installed Grub on sda1 where Vista should be, this is a big problem since the other ntfs partition don't seem to have boot sectors. 

So what you have to do is install Grub on sda6 and the install Vista bootloader on sda1 (thisw will be the hardest thing).

But at first, during boot you may try this :
Instead of selecting a option press "c" then enter the following at the prompt by replacing Y by 0,1,2 or 4 (others are not dangerous):

root (hd0,Y)
makeactive
chainloader +1
boot

If any worked correct the menu.lst

To install the Grub at sda6 do this in a shell (bash):

$sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
$

To install the boot loader of Vista you may use a install CD of Windows (XP or Vista it's the same)

---

### Post by oldfred on 2009-12-09
None of your other partitions identified as NTFS show any boot files. You may still have them in sda1, but because you installed grub you overwrote the vista boot loader that is in the partition. You first need to repair Vista in sda1 and make sure you can boot ok. Then you will have to reinstall grub to sda (not sda1).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Then with the Vista/win7 install dvd, used the repair command line and type:
bootrec /fixmbr (press enter)
bootrec /fixboot (press enter)
bootrec /rebuildbcd (press enter)

I install grub to partitions so I can chainboot, but if you are not chainbooting you should not have to install grub to a partition.

---

### Post by meierfra. on 2009-12-09
> You may still have them in sda1, but because you installed grub you overwrote the vista boot loader that is in the partition. You first need to repair Vista in sda1.


I agree. But I recommend to use testdisk to fix your boot sector.  (Vista's "fixboot" usually only repairs the boot code in the boot sector, but not the boot parameters)

So try this: Open a terminal in ubuntu. Then  install and run testdisk via: 

```
sudo apt-get install testdisk
sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Vista partition (although it should be selected already) and choose
"boot"
"Backup BS"
Type "Y" to confirm
  
then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Windows.

---

### Post by madmax.santana on 2009-12-10
Hey guys, I don't have a Vista disk... I use a notebook and I only have recovery disks which will format all my drives and restore original factory settings. All data lost. Even all partitions are formatted and merged into a single disk... Everything gone, pals. I am in big trouble. Cuz my HDD contains the data of my last 3 semesters and lots of very important data of the present semester which if deleted, will cause me to lose grades!!! Isn't there any other method that I can use to restore my Vista Bootloader?

---

### Post by oldfred on 2009-12-10
meierfra's solution does not require a Vista disk. You use a live CD and download testdisk per his instructions. He is more knowledgeable than I so I am sure his instructions will work.

You can download a repair only recovery CD: 

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by meierfra. on 2009-12-10
> You use a live CD

You don't even need a live CD. Just boot into Ubuntu and follow my instruction.

---

### Post by madmax.santana on 2009-12-10
Yeah!!! Yeah! @meierfra, You are a wizard man! Kudos. You solved the problem.
This is what I love about community support. Talking about paid support, what? You are paying few bucks to a tech bust and he just doesn't want you to know what actually is going on in the background. And in community support, like this example here, people want you to know exactly what is going on in the background... Paid support keeps you ignorant so that only a few people can continue the chain. Community support has the aroma of sincerity and honor, which keeps you enlightened so that the number of support keeps on multiplying, exponentially.
Thanks pals. Thanks a lot. Not only for solving my problem, but for keeping the spirit of "Ubuntu" alive!

---

### Post by madmax.santana on 2009-12-10
And now here is what I understood out of my problem. Correct me please if I am wrong at any point.

- When I installed ubuntu, grub overtook the responsibility of booting. So vista boot sectors were there but they were being managed by grub.

- When I uninstalled my old grub and reinstalled in older version, the vista boot sectors got deleted somehow in the process. (How, I am yet a bit confused, will be glad if anyone could explain in detail.)

- The lines I had added in menu.lst for booting vista were alright except that grub was blind for vista as the boot sectors of vista were lost.

- Whatsoever be the cause, testdisk located the vista partition on sda and repaired the boot sectors for me. Then the same sequence

> title Windows Vista
root (hd0,0)
makeactive
chainloader +1
bootworked without a hassle.

This is my understanding of the topic. Is it alright? Am I qualified to mess with grub once again? ;)

---

### Post by meierfra. on 2009-12-10
> When I uninstalled my old grub and reinstalled in older version, the vista boot sectors got deleted somehow in the process. 

Exactly. You should never install Grub to a Windows partition.  That erases the code necessary to boot Windows.  Luckily, Windows keeps a copy of the boot sector in the last sector of the partition. So it is was easy for testdisk to restore the original boot sector.


One  more thing. You should  move your Vista item in menu.lst above the line 

### BEGIN AUTOMAGIC KERNELS LIST

or below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

Otherwise it will be erased during the next kernel update.

Have fun with Vista and Ubuntu.

---

