---
title: "Discrepancy in boot info script output"
date: 2010-08-07
forum: General Help
---

### Post by Quackers on 2010-08-07
Here is the first part of my boot info script output

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *             63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sda3         170,851,275   365,398,424   194,547,150  af HFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   214,843,391   214,841,344  83 Linux
/dev/sdb2         214,853,310   222,660,899     7,807,590  82 Linux swap / Solaris
/dev/sdb3         222,660,900   488,392,064   265,731,165   7 HPFS/NTFS


blkid -c /dev/null: ______________________________________
```


It states in the first couple of lines that 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb


However it doesn't look like that's true in later entries. In fact it states that /boot/grub/grub.confg is listed at sdb1
It doesn't make any sense to me :(
Am I reading it correctly or am I misguided? :)

Thanks.

---

### Post by varunendra on 2010-08-08
Is it complete output?? If not, please post the complete one.

Also, please post the screenshots of gparted [System>Administration>GParted] for each hard disk.

If gparted isn't already installed, use synaptic to install it, or through terminal by-
```
sudo apt-get install gparted
```

---

### Post by Quackers on 2010-08-08
Thanks for the reply. 
Here is the complete output from the boot info script. I'm working on the other outputs requested :-)

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *             63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sda3         170,851,275   365,398,424   194,547,150  af HFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   214,843,391   214,841,344  83 Linux
/dev/sdb2         214,853,310   222,660,899     7,807,590  82 Linux swap / Solaris
/dev/sdb3         222,660,900   488,392,064   265,731,165   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        D0FEB59CFEB57B74                       ntfs                                     
/dev/sda3        1a6aa2b2-6cb5-3c59-a3c7-79e612695c87   hfsplus    Snow Leopard                  
/dev/sda: PTTYPE="dos" 
/dev/sdb1        83742eeb-0983-4c0d-89ae-f94eaa1da86e   ext4                                     
/dev/sdb2        0615874e-e425-412e-81b5-4a1467f615cc   swap       swap                          
/dev/sdb3        348FE4F01843B257                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 83742eeb-0983-4c0d-89ae-f94eaa1da86e
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 83742eeb-0983-4c0d-89ae-f94eaa1da86e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 83742eeb-0983-4c0d-89ae-f94eaa1da86e
	linux	/boot/vmlinuz-2.6.32-24-generic root=/dev/sdb1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d0feb59cfeb57b74
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sda3)" {
	insmod hfsplus
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda3)" {
	insmod hfsplus
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=83742eeb-0983-4c0d-89ae-f94eaa1da86e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2d97c423-df43-48f4-b7c2-29e468f99319 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  60.3GB: boot/grub/grub.cfg
  21.7GB: boot/initrd.img-2.6.32-24-generic
  21.6GB: boot/vmlinuz-2.6.32-24-generic
  21.7GB: initrd.img
  21.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


```

---

### Post by Quackers on 2010-08-08
Here are the GParted screen shots for both disks.

---

### Post by WorMzy on 2010-08-08
[MBR]("http://en.wikipedia.org/wiki/Master_boot_record") is a special area at the start of a partition which holds the bootloader (or in grub's case, the first part of the boot loader). It's not uncommon for a disk to not have anything in it's MBR if it's the second disk in a machine.

What happens when your machine turns on is the BIOS runs POST, then looks at the MBR of the first disk in the boot list, then the bootloader takes over and loads your Operating System.

You can still have boot files installed on a disk that doesn't have a MBR, as shown in the "/boot/grub/grub.conf is listed at sdb1" part. There does seem to be a discrepancy in the boot info though, since grub must be looking at sdb1 for stage 1.5 et al.

---

### Post by Quackers on 2010-08-08
Again, thanks for your reply WorMzy, and the info in it.
It may help if I describe my past and present systems to you.
At first I had a 2 x 250GB radi0 setup with Vista pre-installed.
I then sacked the raid array and re-installed vista on the first HDD with a small backup partition. I then installed a Mac OS X on the 3rd partition and Ubuntu on the 4th partition of sda.
I then deleted the backup partition (sda1) and moved the vista partition to the beginning of the disk, deleted Ubuntu from sda and re-installed on the 1st partition of sdb. 
All OSes boot from the Grub2 menu. It just looks strange to me when reading the boot info script output. It doesn't seem to agree with itself.

---

### Post by WorMzy on 2010-08-08
Yeah, I don't know what to say about that, it's definitely wrong. If what you've said is accurate, then the first partition of sda has never had /boot/grub on it, so there's no reason why it'd be looking there. The only possible (and very farfetched) theory I have is that there's some remnant of the RAID left over, tricking grub into thinking that it's loading from the only disk in the computer, and that sdb1 is it's first partition.

Since everything's working fine, you should be okay just ignoring it. It's possible that that part of the script is just outputting the wrong thing. You could post a bug report [here]("http://sourceforge.net/projects/bootinfoscript/forums/forum/905693") if you want to alert the developers.

---

### Post by Quackers on 2010-08-08
I was wondering whether to file a bug report, but needed some kind of confirmation that I was reading it correctly.
On another note, the size of partitions doesn't seem to be accurate either. Some appear to be almost double their actual size in the script. Maybe I should file a bug report giving full details of my system.
Thanks again WorMzy.

---

### Post by varunendra on 2010-08-08
Me too suspect the raid0 thing.

I might have requested the actual contents of your MBR (it should be interesting to see it) but I'm afraid I won't be able to interpret it. However, the raid 0 history you mentioned is something that rings an alarm to me! I've encountered threads where one had to go through special methods to remove raid config. completely from the HDDs. Otherwise it would stay in parts no matter how many times you format/repartition them.

So it is just a wild guess that the script might be correct and it may be the remains of previously existing raid 0 array that is saving you from a boot failure (or that prevented grub to note it as sdb1 during installation).



**EDIT:** For the size part, it is stated in 'sectors' (1 sector = 512 byte). So divide the fig. by 512 and you'll get the size in bytes.

---

### Post by Quackers on 2010-08-08
Yikes!  Maybe I'll just leave things alone :-)
Vaio's can be a bit of a nuisance. The bios is almost completely locked. The raid array is purely a bios function and all you can do is turn on raid0 or raid1 or delete the raid array completely. I deleted the raid array completely because installing other OSes was problematical.
It may be that some of the raid setup still exists on the hard disks. I wouldn't be surprised where Sony is concerned!
Thanks to both of you for your help.

---

### Post by varunendra on 2010-08-08
> **Quackers said:**
> The raid array is purely a bios function and all you can do is turn on raid0 or raid1 or delete the raid array completely. I deleted the raid array completely because installing other OSes was problematical.
It may be that some of the raid setup still exists on the hard disks. I wouldn't be surprised where Sony is concerned!
Thanks to both of you for your help.

I'm glad I participated. It is an interesting issue here.

As for the help part, I don't think you need it but wonder if this can offer something useful to you:
[http://ubuntuforums.org/showthread.php?t=1464276](http://ubuntuforums.org/showthread.php?t=1464276) (refer to post #9).

Please don't thank again !;)

---

### Post by Quackers on 2010-08-08
That thread and it's link is very interesting.
When I first installed Mac OS X on the second hard drive it would not boot. Even when I made it bootable with GParted and made its Mac partition active. When I booted up it would only boot Vista or give the white cursor at the top of the screen. 
So something is different now, because all OSes now boot through Grub2 menu.
I notice the instructions in the link within that thread and I may get around to using that - but not yet :-)
I'll do some more thinking :-)

---

### Post by oldfred on 2010-08-08
There is a bug in either grub2 or the boot_info script v 055. The drive is not reported correctly. I had one grub2 booting from sda. The script said same drive partition 7 but it booted correctly from sdc7 and I only have 3 partitions on sda. Grub2 also does not number drives the same as Ubuntu if you do not boot sda. If I boot sdc that becomes hd0 and then my chainboot to sda has to be to hd1 not hd0 as I would otherwise expect.

Someone did say they emailed meierfra with the issue, but we have not seen him lately in the forum. Since they have been making so many changes to grub2 maybe he is just waiting until it stabilizes a bit more.

---

### Post by Quackers on 2010-08-08
Thanks oldfred.
I did notice that in the Grub2 menu my Vista partition was listed as /dev/sda2 and the Vista Recovery partition was listed as /dev/sda3. These 2 entries are completely the wrong way round which definitely confirms that the partitions can be read wrongly.

---

