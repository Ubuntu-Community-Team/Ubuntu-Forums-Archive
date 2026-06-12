---
title: "Help with Grub! Can't seem to get it right!"
date: 2009-12-30
forum: General Help
---

### Post by _DeepBlue on 2009-12-30
First of all I apologize for grammar mistakes and anything else I do wrong, im italian and new as of 2 days ago to linux and just got to the forum (my first post!) 

breifly my problem is: My vista crashed about 3 days ago (huge red ERROR in the middle of the screen when I tried to boot), so I installed ubuntu 9.10, something that I was planning on doing for a while and finally had the excuse to do. I got ubuntu onto a CD and booted it so that I could get the files I needed off my hard drive, and then installed Ubuntu onto my hd, hoping to be able to restore vista on the other partition using the repair thing my asus has. this was not possible, so I installed XP instead. Grub didnt work, so i googled what to do and managed fine, now grub loads, but it doesnt seem to see XP, and has 6 options, 2 different versions of ubuntu and their recovery mode (don't really know why but oh well), Vista and Vista repair, even though neither of the last two exist. i've been on google and forums all day and I just can't seem to hack it! 

ill give some random info hoping it would be of use: My grub version when I turn the pc on is 1.97beta I believe.. XP is on /dev/sda2 and ubuntu is on /dev/sda5. I somehow screwed up the Vista Repair partition, making it unable to work and this situation is a general mess! Can anyone help? last thing, a message of appreciation, what you guys have here is awsome, I hated every second of vista and windows in general, but linux is awsome! im actually enjoying trying to sort out these problems as opposed to calling a tech over to sort it out and spending 20 euros!

EDIT: ive read the guides to grub, but still can't get it right! help plz?

---

### Post by Leppie on 2009-12-30
ok, booting with the livecd, please download and run meierfra's script:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.43/boot_info_script043.sh/download' \
&& chmod 755 boot_info_script043.sh \
&& sudo ./boot_info_script043.sh
```

post the RESULTS.txt which the script generates.

Could you also explain what you did to install XP? did you actually reformat (not the quick format) the partitions, or did you skip this step?
What happened when you tried to boot from vista repair partition (was there any error message)?

---

### Post by john newbuntu on 2009-12-30
DeepBlue, On behalf of the community, I welcome you to Ubuntu and its friendly forum.
Now, have you run "sudo update-grub2" at the Ubuntu terminal and then seen if Grub recognizes the XP bootloader?
If it does not, I get the feeling that you may have to run "fixboot C:" first from a rescue CD in order to first fix the boot sector of XP (assuming C: is where you have your XP root partition).  Please wait on a second opinion before you run this.  But certainly go ahead and run what I said in the first para if you have not already done so.

---

### Post by _DeepBlue on 2009-12-30
> **Leppie said:**
> ok, booting with the livecd, please download and run meierfra's script:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.43/boot_info_script043.sh/download' \
&& chmod 755 boot_info_script043.sh \
&& sudo ./boot_info_script043.sh
```post the RESULTS.txt which the script generates.

Could you also explain what you did to install XP? did you actually reformat (not the quick format) the partitions, or did you skip this step?
What happened when you tried to boot from vista repair partition (was there any error message)?

Thanks for replies, ill get to it!

basically, I installed XP and did the propper format option (the long one) on the partition where I had vista(only that one). XP worked fine, but when I booted i couldnt choose between ubuntu and vista, so i got on my ubuntu cd and following a guide i put grub back, which means I can use ubuntu fine now (which i am :P) but i cannot access XP. i tried to change the menu file like it says on the examples but nothing happens..

last: I appreciate your help with that script Leppie, but i'm seriously new to this and have no idea how or what to do with it! could you explain? thanks!

EDIT: John newbuntu when i try sudo update-grub2 it says "command not found".. meh..

---

### Post by Leppie on 2009-12-30
> **_DeepBlue said:**
> Thanks for replies, ill get to it!

basically, I installed XP and did the propper format option (the long one) on the partition where I had vista(only that one). XP worked fine, but when I booted i couldnt choose between ubuntu and vista, so i got on my ubuntu cd and following a guide i put grub back, which means I can use ubuntu fine now (which i am :P) but i cannot access XP. i tried to change the menu file like it says on the examples but nothing happens..

last: I appreciate your help with that script Leppie, but i'm seriously new to this and have no idea how or what to do with it! could you explain? thanks!

the command you have to run in a terminal. i misread your post before, so you don't have to boot using a livecd, just boot normally into ubuntu. then open a terminal (Applications>Accessories>Terminal) and copy and paste this command and hit enter:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.43/boot_info_script043.sh/download' \
&& chmod 755 boot_info_script043.sh \
&& sudo ./boot_info_script043.sh
```

---

### Post by _DeepBlue on 2009-12-30
> **Leppie said:**
> the command you have to run in a terminal. i misread your post before, so you don't have to boot using a livecd, just boot normally into ubuntu. then open a terminal (Applications>Accessories>Terminal) and copy and paste this command and hit enter:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.43/boot_info_script043.sh/download' \
&& chmod 755 boot_info_script043.sh \
&& sudo ./boot_info_script043.sh
```

ok, done! the results file says this(its big!): (and sda1 was the vista recovery thing fo asus which doesnt work now..) 
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1cd6b96b

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,048   335,749,039   315,266,992   7 HPFS/NTFS
/dev/sda3         335,749,216   488,395,247   152,646,032   5 Extended
/dev/sda5         335,749,260   482,084,415   146,335,156  83 Linux
/dev/sda6         482,084,460   488,395,247     6,310,788  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat" 
sda2: UUID="52380D2D380D1221" TYPE="ntfs" 
sda5: UUID="df9e5311-e23c-436b-8618-d2ff2fa8af56" TYPE="ext4" 
sda6: UUID="bbef04b8-b7fd-4b61-b48d-b4f633d7eabf" TYPE="swap" 

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
gvfs-fuse-daemon on /home/leo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=leo)
/dev/sda5 on /media/sda5 type ext4 (rw)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=df9e5311-e23c-436b-8618-d2ff2fa8af56

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        df9e5311-e23c-436b-8618-d2ff2fa8af56
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        df9e5311-e23c-436b-8618-d2ff2fa8af56
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        df9e5311-e23c-436b-8618-d2ff2fa8af56
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        df9e5311-e23c-436b-8618-d2ff2fa8af56
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        df9e5311-e23c-436b-8618-d2ff2fa8af56
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        df9e5311-e23c-436b-8618-d2ff2fa8af56
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set df9e5311-e23c-436b-8618-d2ff2fa8af56
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set df9e5311-e23c-436b-8618-d2ff2fa8af56
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set df9e5311-e23c-436b-8618-d2ff2fa8af56
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set df9e5311-e23c-436b-8618-d2ff2fa8af56
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set df9e5311-e23c-436b-8618-d2ff2fa8af56
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 ro single 
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
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f64267134266d7bf
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
UUID=df9e5311-e23c-436b-8618-d2ff2fa8af56 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bbef04b8-b7fd-4b61-b48d-b4f633d7eabf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 171.9GB: boot/grub/core.img
 171.9GB: boot/grub/grub.cfg
 171.9GB: boot/grub/menu.lst
 171.9GB: boot/grub/stage2
 171.9GB: boot/initrd.img-2.6.31-14-generic
 171.9GB: boot/initrd.img-2.6.31-16-generic
 171.9GB: boot/vmlinuz-2.6.31-14-generic
 171.9GB: boot/vmlinuz-2.6.31-16-generic
 171.9GB: initrd.img
 171.9GB: initrd.img.old
 171.9GB: vmlinuz
 171.9GB: vmlinuz.old
```

---

### Post by Leppie on 2009-12-30
you have 2 versions of grub installed.
i'd suggest you remove the older version (grub legacy):
```
$sudo apt-get remove grub
```

this should leave you with grub2, which now needs to be installed to your mbr:
```
$sudo grub-install --recheck /dev/sda
```
then generate the appropriate grub configuration file (grub.cfg):
```
$sudo update-grub
```

reboot and test, i'm off to sleep now (e forse dovresti fare lo stesso ;))

---

### Post by _DeepBlue on 2009-12-30
> **Leppie said:**
> you have 2 versions of grub installed.
i'd suggest you remove the older version (grub legacy):
```
$sudo apt-get remove grub
```this should leave you with grub2, which now needs to be installed to your mbr:
```
$sudo grub-install --recheck /dev/sda
```then generate the appropriate grub configuration file (grub.cfg):
```
$sudo update-grub
```reboot and test, i'm off to sleep now (e forse dovresti fare lo stesso ;))
The first code worked, but the second gave an error error: ```
grub-install: command not found
``` so i didnt do the third one.. When i reboot, now I dont have the option to boot vista or vista recover (which is progress because they don't exist:P)

time for me to go to bed too.. thanks for the help so far guys! 
and.. > **Leppie said:**
> (e forse dovresti fare lo stesso ;)) anche tu italiano?! comunque si adesso vado pure io che zii mi uccidono se si svegliano! notte e grazie!

---

### Post by Leppie on 2009-12-31
well, we have some progress now. still not the desired results, but getting there.
re-install grub2:
```
$sudo apt-get install grub-pc grub-common
```

re-create all vital configuration files for running update-grub:
```
$sudo grub-install --recheck /dev/sda
```

generate your grub.cfg file:
```
$sudo update-grub
```
windows xp should now appear in the list of entries.

ps: non sono italiano, ma abito a roma...

---

### Post by Leppie on 2009-12-31
if you want to know if all grub2 files installed, you can run this command:
```
$ls -l /usr/sbin | grep grub
-rwxr-xr-x 1 root    root       1480 2009-12-08 00:08 grub-dumpbios
-rwxr-xr-x 1 root    root      10372 2009-12-08 00:08 grub-install
-rwxr-xr-x 1 root    root       7084 2009-12-08 00:08 grub-mkconfig
-rwxr-xr-x 1 root    root      13932 2009-12-08 00:09 grub-mkdevicemap
-rwxr-xr-x 1 root    root     147064 2009-12-08 00:09 grub-probe
-rwxr-xr-x 1 root    root       2730 2009-12-08 00:08 grub-reboot
-rwxr-xr-x 1 root    root       2472 2009-12-08 00:08 grub-set-default
-rwxr-xr-x 1 root    root     151192 2009-12-08 00:09 grub-setup
-rwxr-xr-x 1 root    root         60 2009-12-07 23:53 update-grub
-rwxr-xr-x 1 root    root         35 2009-12-07 23:53 update-grub2
-rwxr-xr-x 1 root    root       1298 2009-12-07 23:53 upgrade-from-grub-legacy
```

---

### Post by _DeepBlue on 2009-12-31
> **Leppie said:**
> well, we have some progress now. still not the desired results, but getting there.
re-install grub2:
```
$sudo apt-get install grub-pc grub-common
```re-create all vital configuration files for running update-grub:
```
$sudo grub-install --recheck /dev/sda
```generate your grub.cfg file:
```
$sudo update-grub
```windows xp should now appear in the list of entries.

ps: non sono italiano, ma abito a roma...

you sir ar a legend :KS:KS
all commands worked, and when I installed the new one they detected XP fine. I rebooted and XP works, thank you so much!

one last thing, is it possible to get rid of some of the other options? for example one of the Vista ones is still there, and a recovery mode and old version of ubuntu. i tried looking at the grub menu.lst but the vista options aren't on the list... any ideas? thanks so much for your help!!

---

### Post by Leppie on 2009-12-31
grub2 uses grub.cfg instead of menu.lst (you could remove it from your system if you wanted).
to remove older kernel options from grub2, go into synaptic and remove those kernels from your system.

to disable memtest options in grub2:
```
$sudo chmod -x /etc/grub.d/20_memtest86+
```

to remove the Vista recovery partition from the grub2 menu, backup your current 30_os-prober and open it with an editor:
```
$sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &
```

search for this section in the file:
> for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

add this after this section:
```
# Added to remove Windows Recovery
if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
continue
fi
# End Added
```

save and run:
```
$sudo update-grub
```

NOTE: you may have to check the exact menu entry and amend it accordingly in the to be added piece of code:
```
$cat /boot/grub/grub.cfg | grep Vista
```

---

### Post by _DeepBlue on 2009-12-31
> **Leppie said:**
> grub2 uses grub.cfg instead of menu.lst (you could remove it from your system if you wanted).
to remove older kernel options from grub2, go into synaptic and remove those kernels from your system.

to disable memtest options in grub2:
```
$sudo chmod -x /etc/grub.d/20_memtest86+
```to remove the Vista recovery partition from the grub2 menu, backup your current 30_os-prober and open it with an editor:
```
$sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &
```search for this section in the file:


add this after this section:
```
# Added to remove Windows Recovery
if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
continue
fi
# End Added
```save and run:
```
$sudo update-grub
```NOTE: you may have to check the exact menu entry and amend it accordingly in the to be added piece of code:
```
$cat /boot/grub/grub.cfg | grep Vista
```

Thank you very much, worked wonders! ill keep looking at it to try and understand.. Your my life saver!! :):):)

EDIT: If I were to mark some of the things on the grub.cfg as comments, (for example the recovery mode ones) does that mean that they wouldnt appear at the boot menu? thanks again for your immensely helpful replies!
EDIT2: I dont want to get rid of the recovery, just the second two ubuntu boots, which I don't know why they are there.. all I would want to keep is the top ubuntu, ubuntu recovery and Xp..

---

### Post by Leppie on 2009-12-31
To remove kernel entries in grub2, you need to remove them from your system with synaptic.
Recovery mode is not really necessary to have listed in your grub2 menu. When the menu appears you can press the "e" button to edit the boot paramaters for the highlighted entry. To enter recovery mode, just remove "splash" from the line and substitute with "s" or "single".

To remove recovery entries from the grub2 menu, open your grub2 defaults file:
```
$gksu gedit /etc/default/grub &
```
and uncomment (remove the hash sign, #) the following line:
```
GRUB_DISABLE_LINUX_RECOVERY="true"
```
regenerate your grub.cfg:
```
$sudo update-grub
```

---

### Post by _DeepBlue on 2009-12-31
> **Leppie said:**
> To remove kernel entries in grub2, you need to remove them from your system with synaptic.
Recovery mode is not really necessary to have listed in your grub2 menu. When the menu appears you can press the "e" button to edit the boot paramaters for the highlighted entry. To enter recovery mode, just remove "splash" from the line and substitute with "s" or "single".

To remove recovery entries from the grub2 menu, open your grub2 defaults file:
```
$gksu gedit /etc/default/grub &
```and uncomment (remove the hash sign, #) the following line:
```
GRUB_DISABLE_LINUX_RECOVERY="true"
```regenerate your grub.cfg:
```
$sudo update-grub
```

Thank you very much, works perfectly! 
thanks again!

---

### Post by Leppie on 2009-12-31
You're welcome.

Buon anno nuovo!!!

ps: set the thread to "solved" using the thread tools.

---

