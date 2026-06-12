---
title: "Grub loop + MBR/Boot sector problem"
date: 2011-06-16
forum: General Help
---

### Post by msfisher on 2011-06-16
I'm calling it a loop because that's what it seems to do and I don’t know what else to call it.  It seems to be connected with an MBR or boot sector problem.  It isn’t strictly an Ubuntu problem, but I figure you guys know this stuff better than I do.

Before I get to my problem, a few notes.  

I’m not quite a newbie – I’m at that dangerous level where I sometimes think I can figure out something and end up making it worse.  I’ve been using MS products since DOS 3 (with a well-remembered side trip to DR-DOS), so I’m most comfortable there, but I’ve been using Linux more and more since my first distro (Mandrake 5.2), so please no sniping about Windows.  I've also been a forum member for quite some time, but stopped coming here because I wasn't having problems!

I also fairly often install and try new or different distributions, so I’m familiar with the fact that each distro is likely to modify Grub and/or install its own version.  I’ve generally been able to recover from such changes and revert to what I’m most comfortable with.

What I’m comfortable with is the older Grub.  Maybe I’m lazy, but I find it easier to edit a text file than to learn a whole new scripting language (can someone write a graphical configuration tool for us non-scripters?).  This is one of two reasons why I also still run Windows 98 – it ain’t broke so don’t fix it (the second reason, which I only mention since someone is bound to ask, is that I’ve tried five times to upgrade to XP and I can’t even get the Upgrade Advisor tool to run properly - a whole other problem).

That said, here’s what happened.  

I have my hardware set up with two hard drives.  Sda is my Windows drive, split into three partitions.  The second, sdb, is where my Linux distros reside, split into three Linux partitions and a small Windows partition (to make Windows happy).  I’ve been running one version of Ubuntu or another for several years.  Most recently I installed 10.10 and, using the old Grub, modified the Grub screen to be distro-neutral (no logos, no distro-specific image).  Recently I installed Mint, which uses Grub2.  Though I didn’t and don’t like the changes Mint insisted on when setting up the Grub loader page, I was learning to accept it.  I know, I could have changed it, but, as I said above, I really didn’t want to have to learn a whole new language just to change colors or text or background image.  Then I installed Mageia, which, it turns out, also uses the older Grub.  Ouch.  Mageia put up a Grub loader screen which completely ignored Mint and, frankly, was blinding and ugly.  Yes, I now know that all I should have done was modify the menu.lst, but I really hated the Mageia screen and it had ignored Mint completely.  

So I did what I thought I’d done before and tried to just run update-grub.  The Mageia screen didn’t go away.  Instead, each entry now popped up my original Grub screen.  All of the Linux entries worked (and still do), but the Windows entry – nothing but a savedefault, makeactive, chainloader +1 line – now did nothing but bring the Grub screen back.  Worse, booting a Win98 floppy and running fdisk told me that my c: drive was now “Unknown”, and dir c: got me an “Invalid media” error.  I’ve booted with the Ultimate Boot CD and found that gParted and every other tool (and Linux) sees the partition OK.  I can access the Windows 98 drive from all three of the Linux distros currently on the system.  So, with a bit of arm twisting, I tried fdisk /mbr.  

Partial success.  Now the Mageia screen is gone, and Grub goes straight to the original screen.  All the Linux lines work, but the Windows one still drops straight back to the screen – a loop. 

So, what do you guys recommend to be able to boot to my original c: Windows 98 drive? And please, no comments about not doing so, OK? I have data, games, etc. and a high comfort level, so I want to get back to where I was.  I have the UBCD tools, but I’m edgy about using any of them (two “fix” the MBR, a third appears to completely rebuild the boot sector).  Are there some Linux ones out there?  Is it as simple as going most of the way through installing Ubuntu or some other distro and forcing an MBR rewrite that way?  Is the Grub loader even on the MBR anymore (I mean, in accidentally loading two Grubs, did one go to the MBR and the other elsewhere)?  Is Super Grub Disk the way to go?  Test Disk?  At this point, any ideas will likely be helpful.  And, yes, I can – and probably should – back the whole thing up if I need to (I have a second drive of the same make, model and capacity sitting on my desk and a copy of Clonezilla somewhere).

Many thanks to everyone in advance.

---

### Post by Quackers on 2011-06-16
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by msfisher on 2011-06-16
Thanks for the prompt reply.  Here's the results.txt contents:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 54095090 on boot drive #2 
                       for the stage2 file.  A stage2 file is at this 
                       location on /dev/sdb.  Stage2 looks on partition #2 
                       for /boot/grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows 98
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mageia release 1 (Official) for 
                       i586 Kernel 2.6.38.7-desktop-1.mga on an i686 /
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Syslinux 3.53-3.86
    Boot sector info:   Syslinux looks at sector 15448 of /dev/sdc1 for its 
                       second stage. It is very unlikely that Syslinux is 
                       (still) installed. The second stage could not be 
                       found. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   117,226,304   117,226,242   c W95 FAT32 (LBA)
/dev/sda2         117,226,305   312,576,704   195,350,400   f W95 Extended (LBA)
/dev/sda5         117,226,368   234,484,739   117,258,372   b W95 FAT32
/dev/sda6         234,484,803   312,576,704    78,091,902   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    24,579,449    24,579,387   c W95 FAT32 (LBA)
/dev/sdb2          24,579,450    67,119,569    42,540,120  83 Linux
/dev/sdb3          67,119,570   109,659,689    42,540,120  83 Linux
/dev/sdb4         109,659,751   156,296,384    46,636,634   f W95 Extended (LBA)
/dev/sdb5    *    109,659,753   152,199,809    42,540,057  83 Linux
/dev/sdb6         152,199,873   156,296,384     4,096,512  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,897,087     7,897,025   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        396C-F280                              vfat       WINDOWS98
/dev/sda5        E727-13A7                              vfat       GAMES
/dev/sda6        3434-2C74                              vfat       MEDIA
/dev/sdb1        45C8-D0DD                              vfat       BACKUPS
/dev/sdb2        a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4   ext3       
/dev/sdb3        2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6   ext3       
/dev/sdb5        e8943073-5cf5-4eed-82be-6425e0e2f83d   ext3       
/dev/sdb6        16d03c2b-1ed4-4c5f-91d5-4713d6e17c5b   swap       
/dev/sdc1        0CA7-8B3C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/WINDOWS98_        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda5        /media/GAMES             vfat       (rw,utf8,umask=0)
/dev/sda6        /media/MEDIA             vfat       (rw,utf8,umask=0)
/dev/sdb1        /media/BACKUPS           vfat       (rw,utf8,umask=0)
/dev/sdb2        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sdc1        /media/0CA7-8B3C         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb2/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
splashimage (hd1,1)/boot/grub/splashimages/87943-SG-Daedalus-gray.xpm.gz
default 4
timeout 30
color white/black black/light-gray

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
# kopt=root=UUID=a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title Ubuntu Lucid (development branch), kernel 2.6.32-28-generic
root (hd1,1)
kernel /boot/vmlinuz-2.6.35-28-generic root=UUID=a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4 ro quiet splash acpi=off noresume nosmp noapic
initrd /boot/initrd.img-2.6.35-28-generic

title Ubuntu (development branch), kernel Last successful boot
root (hd1,1)
kernel /boot/last-good-boot/vmlinuz root=UUID=a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4 ro quiet splash  last-good-boot
initrd /boot/last-good-boot/initrd.img

title Ubuntu (development branch), memtest86+
root (hd1,1)
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows 98
root (hd0,0)
chainloader +1
savedefault
makeactive

title Mageia 1
	root (hd1,2)
	kernel /boot/vmlinuz-2.6.38.7-desktop-1.mga root=/dev/sdb3 resume=/dev/sdb6 splash=silent  showopts vga=0x317
	initrd /boot/initrd-2.6.38.7-desktop-1.mga.img

title Linux Mint
	root (hd1,4)
	kernel /boot/vmlinuz-2.6.35-22-generic ro root=/dev/sdb5 ro quiet splash acpi=off noresume nosmp noapic
	initrd /boot/initrd.img-2.6.35-22-generic


--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb2 :
UUID=a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sdb5 :
UUID=43181629-6ad2-40a3-8dc3-a2b72b4d0b2b	/media/1	ext3	defaults,relatime	0	2
#Entry for /dev/sdb1 :
UUID=45C8-D0DD	/media/BACKUPS	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda5 :
UUID=E727-13A7	/media/GAMES	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda6 :
UUID=3434-2C74	/media/MEDIA	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sda1 :
UUID=4D0D-D171	/media/WINDOWS98	vfat	defaults,utf8,umask=0	0	2
#Entry for /dev/sdb3 :
UUID=31ae8722-0944-4888-b1e9-0d6889a76f8d	/media/sdb3	ext3	defaults,relatime	0	2
#Entry for /dev/sdb6 :
UUID=16d03c2b-1ed4-4c5f-91d5-4713d6e17c5b	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0


--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  25.759518623 = 27.659072512   boot/grub/menu.lst                             1
  25.797177315 = 27.699508224   boot/grub/stage2                               5
  28.064946175 = 30.134506496   boot/initrd.img-2.6.35-25-generic             49
  27.571873665 = 29.605073920   boot/initrd.img-2.6.35-27-generic             42
  23.459988594 = 25.189970944   boot/initrd.img-2.6.35-28-generic             18
  27.899304390 = 29.956649984   boot/vmlinuz-2.6.35-25-generic                29
  23.444249153 = 25.173070848   boot/vmlinuz-2.6.35-27-generic                 4
  23.382271767 = 25.106523136   boot/vmlinuz-2.6.35-28-generic                 4
  23.459988594 = 25.189970944   initrd.img                                    18
  27.571873665 = 29.605073920   initrd.img.old                                42
  23.382271767 = 25.106523136   vmlinuz                                        4
  23.444249153 = 25.173070848   vmlinuz.old                                    4

=========================== sdb3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,2)/boot/gfxmenu
default 3

title Mageia
kernel (hd1,2)/boot/vmlinuz BOOT_IMAGE=Mageia root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 resume=UUID=16d03c2b-1ed4-4c5f-91d5-4713d6e17c5b splash=silent vga=788
initrd (hd1,2)/boot/initrd.img

title linux-nonfb
kernel (hd1,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 resume=UUID=16d03c2b-1ed4-4c5f-91d5-4713d6e17c5b
initrd (hd1,2)/boot/initrd.img

title failsafe
kernel (hd1,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 failsafe
initrd (hd1,2)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title Ubuntu 10.10 
root (hd1,1)
kernel /boot/vmlinuz-2.6.35-28-generic root=UUID=a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4 ro quiet splash acpi=off noresume nosmp noapic
initrd /boot/initrd.img-2.6.35-28-generic


title Linux Mint 
root (hd1,4)
kernel /boot/vmlinuz-2.6.35-22-generic root=/dev/sdb5 ro quiet splash acpi=off noresume nosmp noapic
initrd /boot/initrd.img-2.6.35-22-generic

--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# Entry for /dev/sdb3 :
UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 / ext3 acl,relatime 1 1
# Entry for /dev/sdb1 :
UUID=45C8-D0DD /media/BACKUPS vfat umask=000,iocharset=utf8 0 0
# Entry for /dev/sda5 :
UUID=E727-13A7 /media/GAMES vfat umask=000,iocharset=utf8 0 0
# Entry for /dev/sda6 :
UUID=3434-2C74 /media/MEDIA vfat umask=000,iocharset=utf8 0 0
# Entry for /dev/sda1 :
UUID=4D0D-D171 /media/WINDOWS98 vfat umask=000,iocharset=utf8 0 0
/dev/cdrom /media/cdrom auto umask=0,users,iocharset=utf8,noauto,ro,exec 0 0
/dev/fd0 /media/floppy auto umask=0,users,iocharset=utf8,noauto,exec,flush 0 0
none /proc proc defaults 0 0
# Entry for /dev/sdb6 :
UUID=16d03c2b-1ed4-4c5f-91d5-4713d6e17c5b swap swap defaults 0 0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  36.774918556 = 39.486768128   boot/grub/menu.lst                             1
  36.775334358 = 39.487214592   boot/grub/stage2                               2
  36.790257454 = 39.503238144   boot/initrd-2.6.38.7-desktop-1.mga.img         2
  36.790257454 = 39.503238144   boot/initrd-desktop.img                        2
  36.790257454 = 39.503238144   boot/initrd.img                                2
  36.774903297 = 39.486751744   boot/vmlinuz                                   2
  36.774903297 = 39.486751744   boot/vmlinuz-2.6.38.7-desktop-1.mga            2
  36.774903297 = 39.486751744   boot/vmlinuz-desktop                           2

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sdb5)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e8943073-5cf5-4eed-82be-6425e0e2f83d ro  vga=758  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sdb5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e8943073-5cf5-4eed-82be-6425e0e2f83d ro single  vga=758
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set e8943073-5cf5-4eed-82be-6425e0e2f83d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 95/98/Me (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4d0d-d171
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu Lucid (development branch), kernel 2.6.32-24-generic (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4 ro quiet splash acpi=off noresume nosmp noapic
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu (development branch), memtest86+ (on /dev/sdb2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set a4500dc5-0e41-46d1-8e42-ac9cd4b9e7e4
	linux /boot/memtest86+.bin 
}
menuentry "Kubuntu, with Linux 2.6.35-27-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Kubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2d2bec74-47ee-4bf9-b2fa-7a7dd6c1d4f6 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober_proxy ###

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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e8943073-5cf5-4eed-82be-6425e0e2f83d /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=16d03c2b-1ed4-4c5f-91d5-4713d6e17c5b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  63.891167164 = 68.602618368   boot/grub/core.img                             1
  63.840187550 = 68.547879424   boot/grub/grub.cfg                             1
  63.917107105 = 68.630471168   boot/initrd.img-2.6.35-22-generic             12
  63.855934620 = 68.564787712   boot/vmlinuz-2.6.35-22-generic                 3
  63.917107105 = 68.630471168   initrd.img                                    12
  63.855934620 = 68.564787712   vmlinuz                                        3

```

---

### Post by Quackers on 2011-06-16
Which hard drive is set to boot first in your bios please?

It is likely that Windows is not booting because grub legacy got installed to the sda1 partition, rather than to the mbr of sda.
Afaik that should be repaired with a Windows repair disc/installation disc for Win 98.
That should get Windows booting if sda is set as the first bootable hard drive.
This would need to be the case I suspect, to repair the bootloader.
Once Windows boots again grub or grub2 should then be able to boot it.

---

### Post by msfisher on 2011-06-16
I had a gut feeling it was something like that.  I have plenty of Win98 installation disks, but I'm not sure about a "repair disk" for '98.  Still, it gives me some ideas -- rebuild the partition table.  

Thanks.  I'll try a couple of things and check back.

---

### Post by Quackers on 2011-06-16
No need to rebuild the partition table, just repair the mbr of sda will do it. As I've never used Win 98 I'm not sure of the prcedure - you will need to check that first.

---

### Post by LostFarmer on 2011-06-16
[QUOTEsda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 54095090 on boot drive #2 
                       for the stage2 file.  A stage2 file is at this 
                       location on /dev/sdb.  Stage2 looks on partition #2 
                       for /boot/grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
][/QUOTE]  You have installed grub into the Win98 partitions Volume Boot Record, that must be corrected.  The easyest is to use 'testdisk' -advanced option.  Not sure if it will correct all the errors but it is a must first step.

For the record to rewrite the MBR boot code with Win98  'fdisk /mbr',  added: the command will only write to the first hdd listed in the BIOS, you can not select a different hdd unlike XP's fixmbr command.

added: If I remember correctly Win98- **sys c:** will rewrite the boot code in the VBR., if so 'testdisk' would not be needed.

---

### Post by msfisher on 2011-06-16
Thanks and good eye, LostFarmer; thanks Quackers.  I used TestDisk (which I used once many years ago and got terrific support from Christof Grenier) even before I saw your reply and found that the two boot records were not identical.  I wrote the backup over the primary and bingo.

Win98 fdisk /mbr apparently writes to the MBR, which accounts for the Mageia Grub getting cleared by that command.  It doesn't write to any boot records -- which your good eye spotted as where the second Grub ended up.

Thanks again both of you.

---

