---
title: "How to fix corrupted partition from ubuntu?"
date: 2011-08-06
forum: General Help
---

### Post by lordmonkeyu on 2011-08-06
Hello,
I have just reinstalled ubuntu today and I run out of space on its partition so I wanted to add some space by subtracting some of it from Windows's partition (/dev/sda5 or /dev/sda4 I don't really know because things did get messed up) and what I get in result is this 


[IMG]http://img24.imageshack.us/img24/3985/screenshotgr.png[/IMG]

And this error message. 
[IMG]http://img546.imageshack.us/img546/456/screenshot1jh.png[/IMG]
[IMG]http://imageshack.us/photo/my-images/546/screenshot1jh.png/[/IMG]
Now I cannot access this partition and the system says that I should format it ( but I have a lot of important stuff in there :( ) 

Please tell me it fixable :(

---

### Post by Nithogger on 2011-08-06
Relative of mine had the same issue, Windows wouldn't boot fast, and after a while it wouldn't boot at all (Ok, I know, windows isn't fast at all, but it was even slower then usual) Anyway. Nobody knows what happened there. All we know is that the HDD was dead. It just died random and that's that. 
Only thing we could come up with was this: Install ubuntu on a cd or flashdrive and retrieve all your documents and files etc. etc. to a big enough external memory. This can either be a Flashdrive or an external HDD. doesn't matter much which one as long as it has enough space on it for the lots of data.
After your files are secured make sure you have all the data coverd and back-uped on the external HDD, buy a new HDD and build that one in (don't forget to remove the battery whilest doing that) and reinstall the whole thing. 
although, after re reading your post: formatting after the data is saved might solve the trick, but only if you HDD is just corrupt (not sure what that means) and not damaged, liked the one dealt with was. 

I hope there is a better way of fixing it, but I couldn't find it. Or my brother. 
Good luck..

Feel free to contact me any time you like.

---

### Post by oldfred on 2011-08-06
You cannot run filechecks on the extended partition as it is just a container. The ntfsfix worked on sda5, but it only does minor fixes and sets the chkdsk flag for windows to run chkdsk. Ubuntu/gparted will not mount a NTFS partition with the chkdsk flag set to prevent futher damage that chkdsk then might not be able to repair.

In your case it may be D:?

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by lordmonkeyu on 2011-08-07
So...  I have tried what olfred suggested but i got this 

[IMG]http://img855.imageshack.us/img855/8822/unledcbx.png[/IMG]

Any other ideas ?

---

### Post by oldfred on 2011-08-07
RAW means it is not formated/ partition boot sector has issues. If it was formated and you have somehow lost the format or corrupted the partition boot sector you may be able to recover the boot sector with testdisk. Windows keeps a backup of the partition boot sector. If backup is valid you can copy it back with testdisk. Otherwise you may be able to use a fixBoot (XP) or BootRec.exe /FixBoot (Vista/7) command from windows.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by lordmonkeyu on 2011-08-07
I have visited the site you provided and there is something like:
> One of the following happens when trying to boot a Windows: grub menu appears, boots to grub prompt, immediate reboot,

whereas this is not my case because I can boot easily to both windows and ubuntu but I cannot see the D: partition. 

I can try to use the fixboot but later on when I get the Windows cd ( pendrive ).
Any other options before I do that ?

---

### Post by Blasphemist on 2011-08-07
I've never seen that error but I do see issues. I think you are spending time on something that won't solve your issues.

Do you have anything in the Ubuntu installation (sda7) that must be salvaged? Nothing else in the extended partition shows as being used.

I'd delete all partitions that are within the extended partition. This is sda5, sda6, sda7, sda8. Then delete the extended partition (sda4).  Your extended partition shows lba flag configuration. I suspect you installed Fedora at some time causing this but it could have been done in error as well.

I believe that after deleting these partions you should recreate the extended partition and have it use all available space. Then within it create whatever logical partitions you need. You only need one swap, a bit bigger than the amount of memory you have. I prefer to make it last and at the end of the disk but that is just preference. Linux OS partitions should be 15-20 GB if you use separate /Home partitions or a shared ntfs partition that will house your pictures, music, videos, etc. I say a shared ntfs partition so that linux and windows can both get to this. If you don't share data like this you should ensure each OS has enough to store the planned data.

Please see my screen shot that shows what I describe. As you can see I have a bunch of distros but if you won't you'd just split the space in the extended partition as needed.

When all this is done, then start doing installations and make sure you choose to allocate the disc space manually. Currently Ubuntu labels that option as "something else" on the disc allocation screen. If you install Fedora again, ensure that you don't do lba as it will greatly complicate things for you.

---

### Post by lordmonkeyu on 2011-08-07
Thanks for the reply but what I understand from what you have written you suggest to erase the whole extended partition and remake it (empty of course) and I am just trying to recover the partition as it was with just making some changes to file system or something. ( I hope it's possible ).

---

### Post by lordmonkeyu on 2011-08-07
Sorry for double posting but now I cannot even boot nor linux nor windows, and instead of standard grub i get grub rescue prompt. 

I have booted from ubuntu live cd and now I cannot even locate grub in here. Can you help me on that ? 

I have been looking for grub but i get these results : 
```
ubuntu@ubuntu:~$ sudo find / -name "*grub"
/mnt/boot/grub
/boot/grub
/usr/sbin/update-grub
/usr/lib/grub
/usr/lib/grub-legacy/update-grub
/usr/lib/linux-boot-probes/mounted/40grub
/usr/share/grub
/usr/share/grub/default/grub
/usr/share/recovery-mode/options/grub
/var/lib/ucf/cache/:etc:default:grub
/etc/default/grub
/etc/alternatives/default.plymouth.grub
/etc/bash_completion.d/grub
/etc/kernel/postinst.d/zz-update-grub
/etc/kernel/postrm.d/zz-update-grub

```


EDIT: 
Ok it's even worse - now I don't even get the grub rescue prompt -  I get the "blinking underscore" and I cannot do anything :/
Please help me :(

---

### Post by oldfred on 2011-08-07
Post boot script. The fix with testdisk was for your problem as it is a repair to the windows partition boot sector. The main reason it is corrupted is those who have installed grub to the windows partition not the MBR. But now lets see boot script output first before doing anything else.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Blasphemist on 2011-08-07
My opinion still isn't changed but do let me ask this. Did you ever have anything on sda5 or D: as you refer to it? That partition had to be created by a linux installation or purposeful effort by someone.

Your windows installation is on sda3 and has 20.35GB free. Linux is os sda7 and has very little space available. sda5 appears as if it's never been right. Is that the case? Is there anything on sda5 to salvage?

You've got a problem with the extended partition and with a logical partition within it. Unless you have something that needs recovered, my recommendation still stands. I'd do what I recommended and use this to install Ubuntu and allocate the disk space manually if I was you. [http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

---

### Post by lordmonkeyu on 2011-08-07
hmm. I have enconutered this run error while running boot info script :
```
ubuntu@ubuntu:~/Downloads/boot_info_script060$ sh boot_info_script.sh 

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

[: 326: busybox awk: unexpected operator
boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")

```I have tried to google the solution but I did not find any

EDIT:
@[Blasphemist]("http://ubuntuforums.org/member.php?u=1165520") : I do have a lot of stuff on sda5 to salvage :/ but anyway as you have probably seen my last posts I am trying to reinstall grub :/

---

### Post by Blasphemist on 2011-08-07
Don't worry about the gawk vs. awk error.

---

### Post by lordmonkeyu on 2011-08-07
Ok but oldfred posted that he wants my boot script and I cannot get it without getting rid of this error.

---

### Post by oldfred on 2011-08-07
That line is just checking if you have multiple copies of the boot script. Not sure why for you it generates an error.

did you run it as sudo?

IF on desktop otherwise change to path it is in.
sudo bash ~/Desktop/boot_info_script.sh

Mine is either in downloads or just in /home

cd Downloads
sudo bash boo  #then press tab for line completion and it will automatically add the full name.

---

### Post by lordmonkeyu on 2011-08-07
Ok, so I get rid of grub problem and reinstalled my ubuntu and now I've got this results from boot script 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    963760248 of the same hard drive for core.img. core.img is at this 
    location and looks for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 19. But according to the info from fdisk, 
                       sda5 starts at sector 232267795. According to the info 
                       in the boot sector, sda5 has 720244912 sectors, but 
                       according to the info from fdisk, it has 718198764 
                       sectors.
    Mounting failed:   Failed to read last sector (720244912): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (720244912): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  19    27,262,991    27,262,973  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,262,992    27,467,791       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,467,792   232,267,775   204,799,984   7 NTFS / exFAT / HPFS
/dev/sda4         232,267,793   976,771,071   744,503,279   f W95 Extended (LBA)
/dev/sda5         232,267,795   950,466,559   718,198,765   7 NTFS / exFAT / HPFS
/dev/sda6         950,468,608   968,044,543    17,575,936  83 Linux
/dev/sda7         968,046,592   976,771,071     8,724,480  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CBEA95730D28A0                       ntfs       PQSERVICE
/dev/sda2        01CBEA95760F9330                       ntfs       SYSTEM RESERVED
/dev/sda3        01CBEA9D4476C2F0                       ntfs       Acer
/dev/sda5        01CBEAC459A58360                       ntfs       New Volume
/dev/sda6        03c40d10-2200-4e00-8430-a020e8fd1f23   ext4       
/dev/sda7        e3729117-b936-4c1d-9883-aee73dab6729   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 03c40d10-2200-4e00-8430-a020e8fd1f23
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 03c40d10-2200-4e00-8430-a020e8fd1f23
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c40d10-2200-4e00-8430-a020e8fd1f23
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03c40d10-2200-4e00-8430-a020e8fd1f23 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c40d10-2200-4e00-8430-a020e8fd1f23
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=03c40d10-2200-4e00-8430-a020e8fd1f23 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c40d10-2200-4e00-8430-a020e8fd1f23
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 03c40d10-2200-4e00-8430-a020e8fd1f23
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 01CBEA95730D28A0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 01CBEA95760F9330
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=03c40d10-2200-4e00-8430-a020e8fd1f23 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e3729117-b936-4c1d-9883-aee73dab6729 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 459.556724548 = 493.445275648  boot/grub/core.img                             1
 458.263187408 = 492.056350720  boot/grub/grub.cfg                             1
 454.382812500 = 487.889829888  boot/initrd.img-2.6.38-8-generic               2
 459.537261963 = 493.424377856  boot/vmlinuz-2.6.38-8-generic                  1
 454.382812500 = 487.889829888  initrd.img                                     2
 459.537261963 = 493.424377856  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  8c fb c1 d2 a7 84 be 0c  f7 c6 9d 39 8e a0 59 37  |...........9..Y7|
00000010  85 2a 0a 8d 9f 6c c1 71  9b 51 e2 8b c9 7b 2c 92  |.*...l.q.Q...{,.|
00000020  b8 14 01 17 7f 26 21 2f  2f d3 dc 07 d2 24 58 42  |.....&!//....$XB|
00000030  76 6c 19 33 0d dd 20 ca  70 ba 96 e0 a2 fd 8b f5  |vl.3.. .p.......|
00000040  92 3a 2b fb e4 99 78 ed  01 1f 89 41 a7 d1 e3 41  |.:+...x....A...A|
00000050  ac ac 40 0c 6f 11 c3 56  1a 19 01 12 ed 3c 49 91  |..@.o..V.....<I.|
00000060  ed d5 fc 1f 65 9d 57 14  97 40 17 d7 a9 d2 aa 76  |....e.W..@.....v|
00000070  16 05 2c e2 34 34 5c 53  a2 45 da b4 df 07 4d 22  |..,.44\S.E....M"|
00000080  17 75 ec 54 84 ef d1 2d  ff c7 1c 0f 7a 84 85 2a  |.u.T...-....z..*|
00000090  7b 6f 10 1d 14 08 22 12  3b 7e da b0 7b 74 d8 d3  |{o....".;~..{t..|
000000a0  06 0c 8f 55 7b 8e 7c 1c  9e 67 4a 23 e8 b4 bb 39  |...U{.|..gJ#...9|
000000b0  8c ed 9d 99 52 9e 35 ec  d6 c4 d0 4a d8 82 ef ac  |....R.5....J....|
000000c0  ff 3d bc 78 04 10 d6 99  d4 ad 06 7d b8 66 5a 02  |.=.x.......}.fZ.|
000000d0  4c 9c 7e 03 18 4c 0d 43  df 34 23 35 44 01 8f be  |L.~..L.C.4#5D...|
000000e0  92 fb c8 fe 56 dd e3 9d  c2 b3 fd fa 31 26 80 f4  |....V.......1&..|
000000f0  44 00 31 8b aa 00 4d 5b  9e 26 6d f6 3b 96 71 47  |D.1...M[.&m.;.qG|
00000100  79 a5 36 89 3e 6e 00 19  d4 b3 55 55 8a d8 4d ea  |y.6.>n....UU..M.|
00000110  6e aa 29 f6 00 ab 91 aa  fa 68 d5 45 eb 47 1e 41  |n.)......h.E.G.A|
00000120  1f e1 10 3b 83 af 6e 9f  62 e1 a6 89 d2 70 25 e0  |...;..n.b....p%.|
00000130  af 05 de 84 d2 83 f3 5e  f4 bc 4a 31 ab 7e ba dc  |.......^..J1.~..|
00000140  1d 8b 22 39 ec f7 62 91  0f f9 54 4f dd e0 cb ec  |.."9..b...TO....|
00000150  d5 a7 9a eb 3e 24 3a b2  9e d3 c8 2f aa 3c 6d 19  |....>$:..../.<m.|
00000160  d1 10 64 f8 cd bd ae b1  3f 5d bd 0d 8e 3d df 7d  |..d.....?]...=.}|
00000170  37 a6 83 e8 40 08 76 53  7f 1f 70 e8 fc 13 41 3b  |7...@.vS..p...A;|
00000180  b8 49 87 66 b9 5e 9a b9  05 63 a5 1d 42 35 68 97  |.I.f.^...c..B5h.|
00000190  c3 64 ca 03 da be 7c 4b  51 cc f6 e6 e7 6e 28 29  |.d....|KQ....n()|
000001a0  85 e0 0e d6 9a 72 52 af  a8 ea 59 ce cb ee c3 4f  |.....rR...Y....O|
000001b0  a8 fd 2c 65 ba 54 b6 cc  55 53 6b f6 a0 1b 00 df  |..,e.T..USk.....|
000001c0  d3 ff 07 df d3 ff 02 00  00 00 ed d7 ce 2a 00 df  |.............*..|
000001d0  d3 ff 05 df d3 ff 6f d9  ce 2a 80 36 0c 01 00 00  |......o..*.6....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Blasphemist on 2011-08-07
I still see the lba flag on the extended partition and I see the error that is causing sda5 to be seen as not mountable. I don't know however how to fix those errors without taking the chance of loosing the data. I can tell you that grub is not the issue.

This utility may be what you need to try. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I don't have personal experience with it. I'll try to request assistance from a couple people that I think may have the expertise.

---

### Post by oldfred on 2011-08-07
Did you copy your windows to sda5? The windows partition boot sector has to have the correct partition info in the partition boot sector that matches the MBR partition table. It says it starts at sector 19.

If it is a copy then the backup partition boot sector that testdisk might recover is also wrong. You may be able to windows tools to fix it but those normally work on primary partitions. Testdisk has a rebuild partition boot sector but there are different versions for data, XP and Vista/7 and I do not think the rebuild does a bootable version.

---

### Post by lordmonkeyu on 2011-08-07
Basically what I did is:
I have installed ubuntu when windows was already installed. I get a strange error in the end of ubuntu installation and rebooted and everything was OK and then I run out of space on linux partition so I resized the windows partition (sda5) and then I got a strange error. 

I will wait for your response [Blasphemist]("http://ubuntuforums.org/member.php?u=1165520").

---

### Post by Blasphemist on 2011-08-07
I did request help from someone who was on line but he may be off now. He's Australian and some of those boys are trying to win a pga event right now. :)

What you've described as the sequence of events doesn't seem complete to me. There normally wouldn't be a ntfs partition in the extended partition without you creating it or some unusual process by the manufacturer. Both windows and linux boot successfully but linux at least doesn't see sda5 as mountable. When you boot windows, what are you able to see of sda5/D:? Do you get any errors? I see that chkdsk fails on it but what of the windows disk management apps? What data is on sda5 (D:)? How did you get it there? I'm trying to figure out how the boot sector thinks it starts at sector 19. Please provide all of the specifics of sequence of events that you can from when you shrunk the partition and gave the space to ubuntu.

---

### Post by Blasphemist on 2011-08-07
As I said earlier, I think we need input from someone other than me but from what I've seen in other threads I think it is likely that eventually there will be a need to do some work with the testdisk program. Please review this wiki and that will help you to understand what someone more knowledgeable than you and I recommend. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) In the meantime I'll keep studying myself. Please do answer the questions I asked a few minutes ago.

Thanks

---

### Post by lordmonkeyu on 2011-08-07
So when I boot windows I see D:\ but I cannot see how much space is occupied/left in there. What do you mean if I get any errors ? I have a lot of important documents, ISOs and things like that on this partition.

Do shrunk the partition I have used Gparted just by shrinking its size by around 1 GB and then clicking apply, then I get this error while it was checking the filesystem.

---

### Post by Herman on 2011-08-08
I would first make a backup of all files in all of your other partitions.

I think you should download the most recent version of [Parted Magic Live CD]("http://sourceforge.net/projects/partedmagic/") and burn it to disc or make a live USB out of it. Parted magic contains the most recent versions of GParted and most other supporting applications including TestDisk.

You should to read the illustrated examples in the [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") website  about how to use TestDisk, especially if it's your first time using  TestDisk.

Then I would use TestDisk in Parted Magic to scan the hard disk for partitions and I would restore the primary partitions plus /dev/sda5 only. I would not try to restore any partitions on the other side of the sda5 NTFS data partition for the time being.

If you do that then TestDisk should write a new partition table to agree with the (original) size for /sda5 to suit the file system in /dev/sda5 and that (with luck) will allow you to recover your data.

Good luck, I hope that will work for you.

---

### Post by lordmonkeyu on 2011-08-14
Ok, in the meantime I have tried to make a "backup" with Clonezilla live USB and I get a perfect clone of my hard drive but I got an error and now I have my partition on the 'target' drive which Gparted says is without a file system. 

I wanted to give Testdisk a try but I would like to have a 'backup' to restore to it later on if anything fails.

---

### Post by Herman on 2011-08-15
The best way I know of is to use the dd command, but that's not considered 'safe' nowadays. It's possible to make a mistake with it and destroy data if a person doesn't understand how to use the dd command correctly or just if a person doesn't use it carefully. For that reason I hesitate to advise anyone to use the dd command, although it seems to me it would be the best way to make a copy of your damaged file system.

---

### Post by lordmonkeyu on 2011-08-16
Ok, so I have finally solved this issue. Here is how I did this:
I have indeed used TestDisk but not to repair the filesystem but to copy the data onto the external drive thanks to the restoring ustilities. Then I reformatted the D: partition (sda5), copied my stuff back, then I get and error saying that I have some issues with booting so I have used the windows 7 DVD and repaired the system and voila ! I have all my files and everything back as I wanted :) :) :)

---

### Post by Robbyx on 2011-08-16
What  part of testdisk did you use to copy the files?

---

