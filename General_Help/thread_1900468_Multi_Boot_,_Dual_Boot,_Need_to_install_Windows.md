---
title: "Multi Boot , Dual Boot, Need to install Windows"
date: 2011-12-26
forum: General Help
---

### Post by sureshsaragadam on 2011-12-26
I wish to install Windows 7 Home Basic, Earlier I have already installed Ubuntu 11.10

I got a copy of windows with my laptop, Earlier when i freshly installed Ubuntu formatting HDD, i left 50GB extended free space for windows

What precautions do i need to take to install windows now?

Why because i know windows will overwrite partition.

How to i recover my Ubuntu after installing Windows.

---

### Post by 2F4U on 2011-12-26
This site lists several variations of dual booting Ubuntu and Windows and may be very helpful for further information:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sureshsaragadam on 2011-12-26
[LIST=1]
[*]Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1 
[*]Install windows 
[*]Boot into a [LiveCD]("https://help.ubuntu.com/community/LiveCD") 
[*]Mount your root partition in the LiveCD 
[*]Restore the MBR e.g. dd if=/medi/sda/mbr.bin of=/dev/sda bs=446 count=1 

[/LIST]


I am following the above procedure from the ref,  Thanks for the Ref

---

### Post by Splat_NJ on 2011-12-26
Easiest way I've found after trial and error was to install Windows first, then install Ubuntu, ensuring to install Ubuntu to the same disk (not partition) as Windows.

---

### Post by oldfred on 2011-12-26
Do you have a full backup of your Windows? The restore DVDs you create are an image of the hard drive as of when you purchased it and not an install disk, so that erases entire drive and restores system to as new.

If a backup of your Windows, you have to restore to the same partition as you copied it from.

Windows will only work from a primary partition or it has to boot from a primary partition. So the first install of Windows cannot be to a logical partition in the extended.

---

### Post by sureshsaragadam on 2011-12-27
> **Splat_NJ said:**
> Easiest way I've found after trial and error was to install Windows first, then install Ubuntu, ensuring to install Ubuntu to the same disk (not partition) as Windows.

In case of dual boot, Installing Windows first is the best option, then installing Ubuntu we don't need to update the gurb entry, So that Ubuntu Will take care of the dual boot option.

But here i am installing windows side to my existing Ubuntu already installed and running fully loaded.

---

### Post by sureshsaragadam on 2011-12-27
> **oldfred said:**
> Do you have a full backup of your Windows? The restore DVDs you create are an image of the hard drive as of when you purchased it and not an install disk, so that erases entire drive and restores system to as new.

If a backup of your Windows, you have to restore to the same partition as you copied it from.

Windows will only work from a primary partition or it has to boot from a primary partition. So the first install of Windows cannot be to a logical partition in the extended.

I think this version of your point is very important to be considered if you have taken backup of windows image, 
  
I didn't take any back up of the Windows which is preloaded when i bought my laptop, 
I used Windows recovery media, to install fresh Windows 7,

But Now being a fresh install, i have installed windows 7 in a logical drive of the extended partition,

Now I have installed windows successfully Disabling  UEFI boot option

with dd command i resorted my earlier Ubuntu and Partitions, using the backup of my MBR while booting from a live Ubuntu CD 

Now i need to make a grub entry to opt for windows 7.

Yet to complete.

---

### Post by Splat_NJ on 2011-12-27
> **sureshsaragadam said:**
> In case of dual boot, Installing Windows first is the best option, then installing Ubuntu we don't need to update the gurb entry, So that Ubuntu Will take care of the dual boot option.

Not always. I've had Ubuntu a few times not locate Windows. In that case a simple sudo update-grub after Ubuntu installs will usually find it. Glad it's working for you though.

---

### Post by sureshsaragadam on 2011-12-27
> **Splat_NJ said:**
> Not always. I've had Ubuntu a few times not locate Windows. In that case a simple sudo update-grub after Ubuntu installs will usually find it. Glad it's working for you though.

Here I installed Windows after Ubuntu install, I could recover Ubuntu with backup MBR, 

To boot windows option I tried 
$sudo update-grub 

it did not work in identifying my windows, 
may be i installed windows in a logical extension, Is this the case?

I think i should add a 40_custom entry,

How do i add an entry to the grub menu to boot my windows partition. (for grub version of Ubuntu 11.10)

Can any further simple way does the job, because I don't want to take a chance to my Ubuntu which is fully loaded.

---

### Post by Shvesley on 2011-12-27
Just install Windows to the 50 Gb partition and re install GRUB 2 which is a boot loader. I have done this many many times. Works like clockwork. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by sureshsaragadam on 2011-12-28
I tried grub-install, It too didn't work in detecting windows 

I added a custom entry to boot windows 
But when i select windows in the grub menu i am getting this error

[B]BOOTMGR is missing, 
[/B]**Press Ctrl+Alt+Del to reboot**

may be the chain-loader is failing to boot first sector of windows...where to start debug?

---

### Post by Splat_NJ on 2011-12-28
I back up my Ubuntu install with Remastersys. So far I've been able to restore my Ubuntu to different partitions, different sized partitions than original, and on different drives altogether. I've even completely deleted the Ubuntu partitions, made new sized ones, then reinstalled Ubuntu without touching the Windows install using the Remastersys backupl. I would back up using Remastersys, wipe everything and/or install Windows first and then Ubuntu, ensuring they're both on the same physical drive. Whenever I've installed Ubuntu to a different physical drive from Windows it never sees the Windows install no matter what I tried.

---

### Post by dave2001 on 2011-12-28
> **sureshsaragadam said:**
> I tried grub-install, It too didn't work in detecting windows 


I allow the Windows 7 boot loader to "run" things on my dual-boot system, and it always works very smoothly. Enter that one time command you've got to get your Windows installation booted up, then check out EasyBCD.
 [http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html](http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html)

It is a freeware program that makes setting up your windows boot loader for a dual-boot really fast and simple. I highly recommend it.

I use the Windows7 boot loader because, let's face it, sometimes Ubuntu just doesn't work. You make an update or upgrade one day, and your system is fubar'd until you can figure out what went wrong.

---

### Post by oldfred on 2011-12-28
Suggest you post this from Ubuntu or a liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils


Often bootmgr is missing is either the PBR - partition boot sector is not correct and needs chkdsk or fixBoot or you are trying to boot from a partition that does not have the bootmgr. Script will tell us what is where.

@ dave2001 Some here like you do recommend EasyBCD with Windows 7 or Vista, I do not know it. But unlike Splat_NJ I find having a different system (and its boot loader) on every drive avoids the issue of not having anything to boot. I have different versions of Ubuntu on sdb, sdc & sdd and a USB flash (full install) and grub2's os-prober has always found Windows XP on sda.

---

### Post by TroN-0074 on 2011-12-28
This is what I have done in the past.
Put liveCD and boot from it
open up a terminal and type
```
$sudo mkdir /media/root
```
then do
```
$sudo mount /dev/sda1 /media/root
```
then check by doing
```
ls /media/root
```
I think you should see
> bin dev home lib mnt root srv usr
       boot etc initrd lib64 opt sbin sys var
       cdrom initrd.img media proc selinux tmp vmlinuz

you then can install GRUB by typing
```
sudo grub-install --root-directory=/media/root dev/sda
```
close terminal, and re-boot your computer
I hope I didnt make a spelling mistake here so, good luck to you and let us know how you did.

---

### Post by sureshsaragadam on 2011-12-29
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:      Grub2 (v1.97-1.98) in the file /mbr.bin looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   253,962,239   253,960,192  83 Linux
/dev/sda2         253,962,240   460,685,311   206,723,072  83 Linux
/dev/sda3         460,685,312   563,902,463   103,217,152  83 Linux
/dev/sda4         563,902,464   976,773,119   412,870,656   5 Extended
/dev/sda5         563,904,512   636,569,599    72,665,088  83 Linux
/dev/sda6         636,571,648   709,375,999    72,804,352   6 FAT16
/dev/sda7         709,378,048   778,901,503    69,523,456  83 Linux
/dev/sda8         778,903,552   823,226,367    44,322,816  83 Linux
/dev/sda9         823,228,416   856,393,727    33,165,312  83 Linux
/dev/sda10        856,395,776   864,784,383     8,388,608  82 Linux swap / Solaris
/dev/sda11        864,786,432   976,773,119   111,986,688   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a3c7d467-2f4f-436e-8816-4a535793b7a2   ext4       
/dev/sda10       ca04b2ab-ac59-4ca5-8559-e5d3c3d0d6f8   swap       
/dev/sda11       2496611859CF2427                       ntfs       Windows7
/dev/sda3        a1f85eb6-a642-4498-a215-a94c59b4d025   ext2       
/dev/sda5        7f571efe-bf96-44e6-aa66-d773f72b6027   ext2       
/dev/sda6        ee0e01a2-760e-4fc7-915c-09b22d091f74   ext2       
/dev/sda7        c1943f1d-cb86-4bab-b798-658321dd929c   ext2       
/dev/sda8        38675a68-062c-4ced-a038-48bed0f875c6   ext2       
/dev/sda9        96113601-5393-4dce-ab81-e44288e712b5   ext2       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
# kopt=root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a3c7d467-2f4f-436e-8816-4a535793b7a2

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

title        Ubuntu 11.10, kernel 3.0.0-14-generic
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/vmlinuz-3.0.0-14-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro quiet splash 
initrd        /boot/initrd.img-3.0.0-14-generic
quiet

title        Ubuntu 11.10, kernel 3.0.0-14-generic (recovery mode)
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/vmlinuz-3.0.0-14-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro  single
initrd        /boot/initrd.img-3.0.0-14-generic

title        Ubuntu 11.10, kernel 3.0.0-13-generic
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/vmlinuz-3.0.0-13-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro quiet splash 
initrd        /boot/initrd.img-3.0.0-13-generic
quiet

title        Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/vmlinuz-3.0.0-13-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro  single
initrd        /boot/initrd.img-3.0.0-13-generic

title        Ubuntu 11.10, kernel 3.0.0-12-generic
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro quiet splash 
initrd        /boot/initrd.img-3.0.0-12-generic
quiet

title        Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/vmlinuz-3.0.0-12-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro  single
initrd        /boot/initrd.img-3.0.0-12-generic

title        Chainload into GRUB 2
root        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/grub/core.img

title        Ubuntu 11.10, memtest86+
uuid        a3c7d467-2f4f-436e-8816-4a535793b7a2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro  splash vga=799  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro recovery nomodeset  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro  splash vga=799  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro recovery nomodeset  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro  splash vga=799  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 ro recovery nomodeset  splash vga=799
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root a3c7d467-2f4f-436e-8816-4a535793b7a2
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

menuentry "Windows 7 Bootloader" {
set root=(hd0,11)
chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a3c7d467-2f4f-436e-8816-4a535793b7a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=478bf806-a3aa-4b7c-90b9-f3ae7fe5a71f none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0

# cread by suresh swap partition for dev/sda5    
UUID=ca04b2ab-ac59-4ca5-8559-e5d3c3d0d6f8 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.167007446 = 0.179322880    boot/grub/core.img                             4
   0.163570404 = 0.175632384    boot/grub/grub.cfg                             2
   0.137092590 = 0.147202048    boot/grub/menu.lst                             2
   0.513305664 = 0.551157760    boot/grub/stage2                               2
  32.505722046 = 34.902753280   boot/initrd.img-3.0.0-12-generic              17
  32.508186340 = 34.905399296   boot/initrd.img-3.0.0-13-generic               8
  42.368164062 = 45.492469760   boot/initrd.img-3.0.0-14-generic               3
  31.399005890 = 33.714425856   boot/vmlinuz-3.0.0-12-generic                  1
  38.372505188 = 41.202163712   boot/vmlinuz-3.0.0-13-generic                  2
  41.700630188 = 44.775710720   boot/vmlinuz-3.0.0-14-generic                  1
  42.368164062 = 45.492469760   initrd.img                                     3
  32.508186340 = 34.905399296   initrd.img.old                                 8
  41.700630188 = 44.775710720   vmlinuz                                        1
  38.372505188 = 41.202163712   vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  a8 ea 6f d4 61 2c 72 e2  f3 0b 6a 78 af 85 7a dd  |..o.a,r...jx..z.|
00000010  c4 4b 42 b2 7e 03 d0 b3  bb 71 32 57 bc 77 28 cf  |.KB.~....q2W.w(.|
00000020  4d 84 4e f9 21 7e 24 23  6b 6a b9 25 c8 04 f7 c8  |M.N.!~$#kj.%....|
00000030  f7 20 47 ea b4 ef a6 c2  42 bb 73 22 7f 97 cb 63  |. G.....B.s"...c|
00000040  7d f3 d2 48 bf 83 1c 64  38 e6 84 90 93 cf 0e c0  |}..H...d8.......|
00000050  ec da 28 fe 63 62 51 7a  1f f5 24 bb 87 82 65 11  |..(.cbQz..$...e.|
00000060  8b f1 f9 d6 3a 0a 0f a1  db af cf 9d 29 e9 f3 33  |....:.......)..3|
00000070  a5 3b 1f 88 6a cc ea e8  66 4a 84 76 23 4c 6b 22  |.;..j...fJ.v#Lk"|
00000080  24 4c 99 1f c3 ad 75 dc  24 58 a1 a8 15 6f d5 92  |$L....u.$X...o..|
00000090  b5 dc a4 88 3f f0 32 c5  3b f0 eb 4c c4 ed 0a a8  |....?.2.;..L....|
000000a0  eb 06 78 c2 60 3b 04 c8  09 74 16 4b 10 9a c5 64  |..x.`;...t.K...d|
000000b0  c9 74 d8 eb a8 31 a1 c9  ec c5 7d 4e f1 cc 17 52  |.t...1....}N...R|
000000c0  6f ed 6d 90 56 c9 41 3e  1a d6 72 d6 e6 5e de d5  |o.m.V.A>..r..^..|
000000d0  6b 0b 54 ff c7 7d e7 77  f3 87 7b e7 e8 69 8f 60  |k.T..}.w..{..i.`|
000000e0  03 3a ec 45 52 7d 09 c0  bf 01 6f 3c 02 f6 60 af  |.:.ER}....o<..`.|
000000f0  68 11 ef eb 82 2b 6e 2b  4a c1 c6 eb 47 41 ff 25  |h....+n+J...GA.%|
00000100  0e 2c 3b cf 3a 1b 6a fa  72 83 ee 36 ec 0c f2 4f  |.,;.:.j.r..6...O|
00000110  25 37 d9 8c 5e 94 8a 8a  a1 3e 94 19 ee 56 b9 58  |%7..^....>...V.X|
00000120  a3 33 70 fc 90 6d bd 88  34 83 6d f7 c4 ac ee d9  |.3p..m..4.m.....|
00000130  9f f1 05 ab 3d a6 47 94  6a 3a f8 9a 04 be e6 d6  |....=.G.j:......|
00000140  bd 4c a0 07 d7 d4 3e 0a  eb fc c5 e1 0d f6 66 06  |.L....>.......f.|
00000150  ec 07 0f 40 4b 37 99 aa  b7 a5 fb 89 cd 87 90 f3  |...@K7..........|
00000160  d4 5c 23 a3 cd 15 16 4c  2d 60 1a 69 78 ec b9 73  |.\#....L-`.ix..s|
00000170  9b 25 40 ee 28 df 56 3c  d2 d7 78 ef b5 13 27 e5  |.%@.(.V<..x...'.|
00000180  6c 6c ef 43 82 a0 f5 47  f7 ef 29 b2 b5 8a ef 9a  |ll.C...G..).....|
00000190  bb a6 19 56 89 04 69 70  1f ee b8 c3 c1 6a 7b 32  |...V..ip.....j{2|
000001a0  c9 63 71 8d 5b 51 68 5c  94 6b f9 03 87 35 ca b1  |.cq.[Qh\.k...5..|
000001b0  da 7d 03 b0 54 72 db a9  c8 42 cb 18 48 3e 41 da  |.}..Tr...B..H>A.|
000001c0  96 55 44 ee 61 45 0c 03  f2 38 98 af b0 d7 e4 f3  |.UD.aE...8......|
000001d0  86 9a 03 3e d3 10 ca 8f  c4 f6 d5 bf 0c fe 2b 31  |...>..........+1|
000001e0  cc 20 51 eb 9a 66 10 58  87 0e 65 ba d9 18 f9 5d  |. Q..f.X..e....]|
000001f0  b9 f6 ef f5 b5 f1 2e dc  6c b1 74 ba 48 5e 1c 8a  |........l.t.H^..|
00000200



```This is the output of the above script

I am now able to boot Ubuntu, I have already installed Windows, but grub-install is not detecting the windows, 

I tried custom menu entry to boot windows 7, Later Multiple time i tried grub-install, wholly i lost Grub in the process of recovering installed windows,

Now, Again I could recover GRUB

Above code is the output of the script run from my Recovered Ubuntu (not live cd) 

I am planning multi-boot, After recovering dual-boot with windows 7,
I understand the complications of this process, so step by step i need to back up required information need to multi-boot.

How to safely backup grub, Add Windows to Grub Menu?

---

### Post by sureshsaragadam on 2011-12-29
My sda2 is hidden drive, with TrueCrypt, The above Output may be confusing.

There are three primary partitions, I installed windows 7 in sda11.

---

### Post by oldfred on 2011-12-29
Windows only can boot thru a primary partition. You can have the main install in a logical but the boot partition for Windows 7 must be a primary.

You show no primary partition left, so I do not know how you want to rearrange things to make it work. Most install the full Windows to a primary NTFS partition (best before the extended, and most often sda1 as Windows is usually first). Windows 7 default install uses two primaries, one a 100MB hidden boot/repair partition and the main install, but it will install to one partition if you create it in advance.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition which are the files you are missing)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by sureshsaragadam on 2011-12-29
> **oldfred said:**
> Windows only can boot thru a primary partition. You can have the main install in a logical but the boot partition for Windows 7 must be a primary.


So, May be a better option is to install windows 7 in the primary sda3 in my case.

In fact i am not aware that windows needs primary partition to boot,  I need to make an other installation of windows 7 that fits in primary partition.

Earlier i never faced such a situation where i am used to install windows first and then Linux, hopefully the best option for dual-boot

---

### Post by sureshsaragadam on 2012-01-01
update-grub command did not work in detecting my windows 7 in Ubuntu 11.10,

```

$ sudo grub-mkconfig -o /boot/grub/grub.cfg 

```This above command detected my windows 7( with out the need for 40_custom entry, i.e. with out manually editing custom entry)
Better take a backup of your old config file before you create a new config file

I even tried 40_custom entry also it also worked with the above commnad

40_custom file, to manually add windows entry to grub menu

```

 
 #!/bin/sh
 exec tail -n +3 $0
 # This file provides an easy way to add custom menu entries.  Simply type th    e
 # menu entries you want to add after this comment.  Be careful not to change
 # the 'exec tail' line above.
  
 menuentry "Windows 7 Home Basic" {
 set root=(hd0,3)
 chainloader +1
 }
      

```

In my case i installed windows in sda3 so in the above code root is (hd0,3)

Hint: Hold Shift Key to see the Menu bar if it is hidden, to choose between OS 
check for hiddenmenu, timeout in /boot/grub/menu.lst

---

### Post by sureshsaragadam on 2012-01-01
> **TroN-0074 said:**
> This is what I have done in the past.
Put liveCD and boot from it
open up a terminal and type
```
$sudo mkdir /media/root
```then do
```
$sudo mount /dev/sda1 /media/root
```then check by doing
```
ls /media/root
```I think you should see

you then can install GRUB by typing
```
sudo grub-install --root-directory=/media/root dev/sda
```close terminal, and re-boot your computer
I hope I didnt make a spelling mistake here so, good luck to you and let us know how you did.

It simply works perfect in recovering your Ubuntu after Windows install, simple and elegant way, instead using dd command, It worked for me.

---

