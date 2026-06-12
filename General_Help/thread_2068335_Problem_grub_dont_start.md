---
title: "Problem grub dont start"
date: 2012-10-08
forum: General Help
---

### Post by jonsan191086 on 2012-10-08
Hello this is mi first post and I need help because my laptop (samsung series 5 ultra) is not starting the grub when try to load display 
[B]Error: file not found
grub rescue> [/B]

Can somebody help me I try to reinstall the grub with boot-repair and doesnt work, tried to install linux again and doesnt work

Thanks and regards

---

### Post by daslinkard on 2012-10-08
[LIST=1]
[*]Type ls to get a list of partitions
[*]Enter set prefix=(hd0,msdos6)/boot/grub [you will  almost certainly have to enter a different drive/partition in the  brackets, you may just have to try all of those listed by ls until you find the one that works.
[*]Type insmod normal
[*]Type normal and you will get your boot prompt back!
[/LIST]
  See also: [The helpful place where I found this.]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/355359/comments/4") 

  Once you've loaded Ubuntu, run ```
sudo grub-install /dev/sda
``` and```
 sudo update-grub
``` as soon as possible. This means you won't have to do that tedious process above every time you boot your machine.

---

### Post by jonsan191086 on 2012-10-09
> **daslinkard said:**
> [LIST=1]
[*]Type ls to get a list of partitions
[*]Enter set prefix=(hd0,msdos6)/boot/grub [you will  almost certainly have to enter a different drive/partition in the  brackets, you may just have to try all of those listed by ls until you find the one that works.
[*]Type insmod normal
[*]Type normal and you will get your boot prompt back!
[/LIST]
  See also: [The helpful place where I found this.]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/355359/comments/4") 

  Once you've loaded Ubuntu, run ```
sudo grub-install /dev/sda
``` and```
 sudo update-grub
``` as soon as possible. This means you won't have to do that tedious process above every time you boot your machine.

when type ls in grub rescue>ls
(hd0)  (hd0,gpt7)  (hd0,gpt6)  (hd0,gpt5)  (hd0,gpt4)  (hd0,gpt3) (hd0,gpt2)  (hd0,gpt1) (hd1) (hd1,gpt2) (hd1,gpt1)

after that type 
ls (hd1,gpt2)/boot/grub
x86_64-efi/ grubenv locale fonts/ grub.cfg

then
set prefix=(hd1,gpt2)/boot/grub/x86_64-efi
set root=(hd1,gpt2)
but when try insmod linux
display **error: symbol not found: 'grub_efi_secure_boot'**
and when try linux /vmlinuz display unknow command linux 
and try boot **error you need to load the kernel first**

:confused::(

---

### Post by jonsan191086 on 2012-10-09
when type ls in grub rescue>ls
[COLOR="DarkRed"](hd0) (hd0,gpt7) (hd0,gpt6) (hd0,gpt5) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (hd1) (hd1,gpt2) (hd1,gpt1)[/COLOR]

after that type 
ls (hd1,gpt2)/boot/grub
x86_64-efi/ grubenv locale fonts/ grub.cfg

then
set prefix=(hd1,gpt2)/boot/grub/[COLOR="DarkOrange"]x86_64-efi[/COLOR]
set root=(hd1,gpt2)
but when try insmod linux
[B][SIZE="3"]display error: symbol not found: 'grub_efi_secure_boot'
and when try linux /vmlinuz display unknow command linux 
and try boot error you need to load the kernel first[/SIZE][/B]


:KS

---

### Post by sienile on 2012-10-09
Have you tried using Boot Repair? It solves nearly every GRUB problem.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by jonsan191086 on 2012-10-09
> **sienile said:**
> Have you tried using Boot Repair? It solves nearly every GRUB problem.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Yeah I tried even I tried to reinstall the linux OS but nothing seems work I think the problem was when I have the linux and windows working I resize the partition of windows after that the grub doesnt work :(

---

### Post by sienile on 2012-10-09
GRUB likely is installed to the partition you edited. Run Boot Repair again and it should be able to fix it.

If it doesn't work, post your Boot Info here so we can see what's going on.

---

### Post by YannBuntu on 2012-10-09
> **jonsan191086 said:**
> I try to reinstall the grub with boot-repair and doesnt work, tried to install linux again and doesnt work

Thanks and regards

What is the URL returned by Boot-Repair?

---

### Post by oldfred on 2012-10-09
Threads merged. You have two threads with same issue. Please only start new threads for unique issues. We are all volunteers here and not seeing what others post may confuse the issue.

---

### Post by jonsan191086 on 2012-10-10
> **sienile said:**
> GRUB likely is installed to the partition you edited. Run Boot Repair again and it should be able to fix it.

If it doesn't work, post your Boot Info here so we can see what's going on.
this is the boot info I tried with the boot repair multiple times but doesnt works

```


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    228726784 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 2 for (,gpt2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 76513304 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 85290144 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   123,254,148   122,785,157 Data partition (Windows/Linux)
/dev/sda4     123,256,832   220,913,081    97,656,250 Data partition (Windows/Linux)
/dev/sda5     220,913,664   228,726,163     7,812,500 Swap partition (Linux)
/dev/sda6     228,726,784   228,747,263        20,480 BIOS Boot partition
/dev/sda7     228,747,264   331,651,071   102,903,808 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1    31,277,231    31,277,231  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34        65,569        65,536 Microsoft Reserved Partition (Windows)
/dev/sdb2          67,584    21,510,943    21,443,360 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D6AE-FE5B                              vfat       
/dev/sda3        68CAB129CAB0F482                       ntfs       
/dev/sda4        3dae80e2-36c8-4f0a-aa44-623c8583684e   ext4       
/dev/sda5        193c0a28-f5d1-4beb-b563-103748f4f875   swap       
/dev/sda7        7A44B72344B6E0D5                       ntfs       Datos
/dev/sdb2        bb8f4fb7-bf74-45f1-81aa-3eab972336a8   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda4        /home                    ext4       (rw)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
else
  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 75,75,75; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
	else
	  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
	fi
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
	menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-23-generic-advanced-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		else
		  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		fi
		echo	'Loading Linux 3.2.0-23-generic ...'
		linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-23-generic-recovery-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		else
		  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		fi
		echo	'Loading Linux 3.2.0-23-generic ...'
		linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-23-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root D6AE-FE5B
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}

menuentry "Windows UEFI memory test" {
search --fs-uuid --no-floppy --set=root D6AE-FE5B
chainloader (${root})/EFI/Microsoft/Boot/memtest.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D6AE-FE5B  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda4 during installation
UUID=3dae80e2-36c8-4f0a-aa44-623c8583684e /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=193c0a28-f5d1-4beb-b563-103748f4f875 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.482559204 = 0.518144000    boot/grub/grub.cfg                             1
   0.717067719 = 0.769945600    boot/initrd.img-3.2.0-23-generic               2
   5.052047729 = 5.424594944    boot/vmlinuz-3.2.0-23-generic                  1
   0.717067719 = 0.769945600    initrd.img                                     2
   5.052047729 = 5.424594944    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  c8 c5 92 4c 68 28 dd 50  f6 f3 5d 69 19 7f 19 5a  |...Lh(.P..]i...Z|
00000010  18 4a a4 37 4a 9c 37 25  ce 6a 02 61 7b 7a c4 84  |.J.7J.7%.j.a{z..|
00000020  1a c8 9a 05 d3 29 14 ff  e6 2e 8e 34 9c 4b be 53  |.....).....4.K.S|
00000030  7c 38 89 76 c1 98 1b ef  0c d9 36 44 57 5b ca 78  ||8.v......6DW[.x|
00000040  2a d4 c7 8c 11 f3 2f 46  4d 43 6f 31 ca 53 ef e5  |*...../FMCo1.S..|
00000050  51 14 e8 88 ff 82 76 95  f6 86 ee dc 52 1b 71 cb  |Q.....v.....R.q.|
00000060  5f b1 c1 eb 09 ce 54 ad  93 fb a7 67 8c de d5 9a  |_.....T....g....|
00000070  ff a4 68 76 eb a2 6f a0  f2 3b d1 32 55 04 e0 04  |..hv..o..;.2U...|
00000080  20 26 31 2a a2 04 ac bd  20 1e df df cb 35 97 f9  | &1*.... ....5..|
00000090  ee b1 b2 47 6c 3f 2f 97  6a be 87 4d 49 5c 40 ab  |...Gl?/.j..MI\@.|
000000a0  d7 fc bf 4f c6 dc 5e fd  5d 74 be 9f 6d a1 5f 8a  |...O..^.]t..m._.|
000000b0  87 02 6d 03 6c a2 dd 02  c5 d8 b9 36 14 6c b8 48  |..m.l......6.l.H|
000000c0  eb fb 12 64 5c 9d 92 f6  b0 c4 ed b1 5b 68 52 d6  |...d\.......[hR.|
000000d0  30 61 42 b3 d2 14 a2 6a  6b 51 0f f3 a0 7c 71 64  |0aB....jkQ...|qd|
000000e0  c4 eb d3 70 4b 90 72 2e  82 d8 13 1c 7e d2 9a 64  |...pK.r.....~..d|
000000f0  52 94 d9 5e 86 db a6 55  c4 f1 30 8e d3 d4 93 86  |R..^...U..0.....|
00000100  ca 94 a9 7c 7d fd 23 2f  3c 76 d9 e9 bd 29 5f bc  |...|}.#/<v...)_.|
00000110  56 64 d9 0c 6f 3f 10 4e  38 80 c5 0e 97 bb 45 37  |Vd..o?.N8.....E7|
00000120  65 be 3d 8f d9 2c d0 81  44 67 e7 1f ff b3 c8 67  |e.=..,..Dg.....g|
00000130  a2 99 eb c5 77 8a 08 da  2f c5 75 7c d3 7b af fe  |....w.../.u|.{..|
00000140  fd 30 37 b1 47 64 9f aa  04 73 e4 c6 2e ba fe ec  |.07.Gd...s......|
00000150  a0 fb b6 92 85 02 b8 83  11 89 e9 df 6f 5a fa 63  |............oZ.c|
00000160  fa b3 3e ea af ee b8 34  e2 61 79 e7 31 84 29 d3  |..>....4.ay.1.).|
00000170  b7 51 e3 7a 82 f1 46 d0  46 94 c8 3f 52 a1 4e ee  |.Q.z..F.F..?R.N.|
00000180  c4 0f fa 43 f9 12 44 a7  48 fb 4d 89 f0 59 6f a5  |...C..D.H.M..Yo.|
00000190  4e 65 19 86 54 9d da 49  36 ae bb a5 66 97 d2 28  |Ne..T..I6...f..(|
000001a0  c3 0c 14 c3 0e 18 6b 89  9d 07 09 b4 53 83 fb e9  |......k.....S...|
000001b0  cf fd 01 bd e4 4f 9d 77  49 9f 6a 17 92 86 af 98  |.....O.wI.j.....|
000001c0  5f 71 34 73 d4 48 54 64  49 4e 54 70 42 49 f3 27  |_q4s.HTdINTpBI.'|
000001d0  a1 e2 42 27 1a 4e b6 e1  e8 2e 7c a0 be b4 0c c7  |..B'.N....|.....|
000001e0  01 08 01 59 34 ea 28 bf  b4 98 d7 c6 a5 f2 80 e8  |...Y4.(.........|
000001f0  2c dc 85 cc de e4 4e 10  79 25 9a 45 d2 6a 12 3b  |,.....N.y%.E.j.;|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt




```

Thanks for the help :guitar:

---

### Post by jonsan191086 on 2012-10-10
> **oldfred said:**
> Threads merged. You have two threads with same issue. Please only start new threads for unique issues. We are all volunteers here and not seeing what others post may confuse the issue.

Sorry i get it now thanks for all the help :KS

---

### Post by jonsan191086 on 2012-10-10
> **YannBuntu said:**
> What is the URL returned by Boot-Repair?

the url is the same as [COLOR="Orange"]remember boot from sda1/efi/ubuntu/grubx64.eif ?[/COLOR]

---

### Post by YannBuntu on 2012-10-10
> **jonsan191086 said:**
> the url is the same as [COLOR="Orange"]remember boot from sda1/efi/ubuntu/grubx64.eif ?[/COLOR]

Sorry, i don't understand. The URL should be something like paste.ubuntu.com/XXXXXXX

---

### Post by jonsan191086 on 2012-10-10
> **YannBuntu said:**
> Sorry, i don't understand. The URL should be something like paste.ubuntu.com/XXXXXXX

I dont know which is the url how I get that ?

this is my boot info 

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    228726784 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 2 for (,gpt2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 76513304 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 85290144 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   123,254,148   122,785,157 Data partition (Windows/Linux)
/dev/sda4     123,256,832   220,913,081    97,656,250 Data partition (Windows/Linux)
/dev/sda5     220,913,664   228,726,163     7,812,500 Swap partition (Linux)
/dev/sda6     228,726,784   228,747,263        20,480 BIOS Boot partition
/dev/sda7     228,747,264   331,651,071   102,903,808 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1    31,277,231    31,277,231  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34        65,569        65,536 Microsoft Reserved Partition (Windows)
/dev/sdb2          67,584    21,510,943    21,443,360 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D6AE-FE5B                              vfat       
/dev/sda3        68CAB129CAB0F482                       ntfs       
/dev/sda4        3dae80e2-36c8-4f0a-aa44-623c8583684e   ext4       
/dev/sda5        193c0a28-f5d1-4beb-b563-103748f4f875   swap       
/dev/sda7        7A44B72344B6E0D5                       ntfs       Datos
/dev/sdb2        bb8f4fb7-bf74-45f1-81aa-3eab972336a8   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda4        /home                    ext4       (rw)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
else
  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 75,75,75; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
	else
	  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
	fi
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
	menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-23-generic-advanced-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		else
		  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		fi
		echo	'Loading Linux 3.2.0-23-generic ...'
		linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-23-generic-recovery-bb8f4fb7-bf74-45f1-81aa-3eab972336a8' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		else
		  search --no-floppy --fs-uuid --set=root bb8f4fb7-bf74-45f1-81aa-3eab972336a8
		fi
		echo	'Loading Linux 3.2.0-23-generic ...'
		linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.2.0-23-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root D6AE-FE5B
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}

menuentry "Windows UEFI memory test" {
search --fs-uuid --no-floppy --set=root D6AE-FE5B
chainloader (${root})/EFI/Microsoft/Boot/memtest.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=bb8f4fb7-bf74-45f1-81aa-3eab972336a8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D6AE-FE5B  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda4 during installation
UUID=3dae80e2-36c8-4f0a-aa44-623c8583684e /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=193c0a28-f5d1-4beb-b563-103748f4f875 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.482559204 = 0.518144000    boot/grub/grub.cfg                             1
   0.717067719 = 0.769945600    boot/initrd.img-3.2.0-23-generic               2
   5.052047729 = 5.424594944    boot/vmlinuz-3.2.0-23-generic                  1
   0.717067719 = 0.769945600    initrd.img                                     2
   5.052047729 = 5.424594944    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  c8 c5 92 4c 68 28 dd 50  f6 f3 5d 69 19 7f 19 5a  |...Lh(.P..]i...Z|
00000010  18 4a a4 37 4a 9c 37 25  ce 6a 02 61 7b 7a c4 84  |.J.7J.7%.j.a{z..|
00000020  1a c8 9a 05 d3 29 14 ff  e6 2e 8e 34 9c 4b be 53  |.....).....4.K.S|
00000030  7c 38 89 76 c1 98 1b ef  0c d9 36 44 57 5b ca 78  ||8.v......6DW[.x|
00000040  2a d4 c7 8c 11 f3 2f 46  4d 43 6f 31 ca 53 ef e5  |*...../FMCo1.S..|
00000050  51 14 e8 88 ff 82 76 95  f6 86 ee dc 52 1b 71 cb  |Q.....v.....R.q.|
00000060  5f b1 c1 eb 09 ce 54 ad  93 fb a7 67 8c de d5 9a  |_.....T....g....|
00000070  ff a4 68 76 eb a2 6f a0  f2 3b d1 32 55 04 e0 04  |..hv..o..;.2U...|
00000080  20 26 31 2a a2 04 ac bd  20 1e df df cb 35 97 f9  | &1*.... ....5..|
00000090  ee b1 b2 47 6c 3f 2f 97  6a be 87 4d 49 5c 40 ab  |...Gl?/.j..MI\@.|
000000a0  d7 fc bf 4f c6 dc 5e fd  5d 74 be 9f 6d a1 5f 8a  |...O..^.]t..m._.|
000000b0  87 02 6d 03 6c a2 dd 02  c5 d8 b9 36 14 6c b8 48  |..m.l......6.l.H|
000000c0  eb fb 12 64 5c 9d 92 f6  b0 c4 ed b1 5b 68 52 d6  |...d\.......[hR.|
000000d0  30 61 42 b3 d2 14 a2 6a  6b 51 0f f3 a0 7c 71 64  |0aB....jkQ...|qd|
000000e0  c4 eb d3 70 4b 90 72 2e  82 d8 13 1c 7e d2 9a 64  |...pK.r.....~..d|
000000f0  52 94 d9 5e 86 db a6 55  c4 f1 30 8e d3 d4 93 86  |R..^...U..0.....|
00000100  ca 94 a9 7c 7d fd 23 2f  3c 76 d9 e9 bd 29 5f bc  |...|}.#/<v...)_.|
00000110  56 64 d9 0c 6f 3f 10 4e  38 80 c5 0e 97 bb 45 37  |Vd..o?.N8.....E7|
00000120  65 be 3d 8f d9 2c d0 81  44 67 e7 1f ff b3 c8 67  |e.=..,..Dg.....g|
00000130  a2 99 eb c5 77 8a 08 da  2f c5 75 7c d3 7b af fe  |....w.../.u|.{..|
00000140  fd 30 37 b1 47 64 9f aa  04 73 e4 c6 2e ba fe ec  |.07.Gd...s......|
00000150  a0 fb b6 92 85 02 b8 83  11 89 e9 df 6f 5a fa 63  |............oZ.c|
00000160  fa b3 3e ea af ee b8 34  e2 61 79 e7 31 84 29 d3  |..>....4.ay.1.).|
00000170  b7 51 e3 7a 82 f1 46 d0  46 94 c8 3f 52 a1 4e ee  |.Q.z..F.F..?R.N.|
00000180  c4 0f fa 43 f9 12 44 a7  48 fb 4d 89 f0 59 6f a5  |...C..D.H.M..Yo.|
00000190  4e 65 19 86 54 9d da 49  36 ae bb a5 66 97 d2 28  |Ne..T..I6...f..(|
000001a0  c3 0c 14 c3 0e 18 6b 89  9d 07 09 b4 53 83 fb e9  |......k.....S...|
000001b0  cf fd 01 bd e4 4f 9d 77  49 9f 6a 17 92 86 af 98  |.....O.wI.j.....|
000001c0  5f 71 34 73 d4 48 54 64  49 4e 54 70 42 49 f3 27  |_q4s.HTdINTpBI.'|
000001d0  a1 e2 42 27 1a 4e b6 e1  e8 2e 7c a0 be b4 0c c7  |..B'.N....|.....|
000001e0  01 08 01 59 34 ea 28 bf  b4 98 d7 c6 a5 f2 80 e8  |...Y4.(.........|
000001f0  2c dc 85 cc de e4 4e 10  79 25 9a 45 d2 6a 12 3b  |,.....N.y%.E.j.;|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

---

### Post by oldfred on 2012-10-10
Boot script tells a lot, but BootInfo would show more. You have UEFI system with gpt partitioning and grub installed in a BIUOS/MBR partitioning mode. Ubuntu liveCD/USB needed to be booted in UEFI mode to install correctly. You also managed to install grub to severa partitions but that should not matter, but will never be used.

If Windows files are ok, script does not show them, you can use this to fix Ubuntu. Boot-Repair runs the boot info script as part of its BootInfo and adds some extra info that will tell us if your Windows boot files are still there.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by YannBuntu on 2012-10-10
> **jonsan191086 said:**
> I dont know which is the url how I get that ?

it appears in the final window after running Boot-Repair.

---

### Post by jonsan191086 on 2012-10-11
> **YannBuntu said:**
> it appears in the final window after running Boot-Repair.

This is the URL [http://paste.ubuntu.com/1272547/](http://paste.ubuntu.com/1272547/)

I hope you can help me 

:popcorn:

---

### Post by oldfred on 2012-10-11
You have a UEFI system and both Windows & Ubuntu installed in efi mode. But you then install grub into the MBR or old BIOS mode and installed it into several partitions. Not sure if install into the efi partition will prevent booting or not. Windows normally has to have its boot info in the partition boot sector.

Are you in UEFI/BIOS choosing UEFI and booting from that?

But you can fix the Windows partition.

```
sda3: _____________________________________

    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 85290144 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe
```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD. Note your drive is gpt(GUID) not MBR(msdos).
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If UEFI boot does not work we may have to backup the efi boot files in sda1, and totally reformat it, then restore boot files.
Update. 
Testdisk site says this. So also try to run same repair on sda1.
> Recovery of a FAT32 partition (instead of an NTFS partition) can be accomplished by following exactly the same steps.

---

### Post by YannBuntu on 2012-10-11
oldfred +1  (you need to fix the bootsector of sda3)


However, i see you are able to boot into your installed Ubuntu in UEFI mode:

```
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
```

so you probably don't need to fix the bootsector of sda1.

So i would:
1) fix the bootsector of sda3 as described by oldfred
2) reboot the PC, in the GRUB menu choose the "Windows UEFI" entry, and tell us if it boots Windows or not.

---

### Post by jonsan191086 on 2012-10-12
> **oldfred said:**
> You have a UEFI system and both Windows & Ubuntu installed in efi mode. But you then install grub into the MBR or old BIOS mode and installed it into several partitions. Not sure if install into the efi partition will prevent booting or not. Windows normally has to have its boot info in the partition boot sector.

Are you in UEFI/BIOS choosing UEFI and booting from that?

But you can fix the Windows partition.

```
sda3: _____________________________________

    File system:       ntfs
[COLOR=Red]    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 85290144 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
[/COLOR]    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe
```Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:

This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD. Note your drive is gpt(GUID) not MBR(msdos).
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

If UEFI boot does not work we may have to backup the efi boot files in sda1, and totally reformat it, then restore boot files.
Update. 
Testdisk site says this. So also try to run same repair on sda1.

Sorry but for this [COLOR="Red"]Note your drive is gpt(GUID) not MBR(msdos).[/COLOR] then i have to select intel or EFI GPT ??? I dont want screw it all

---

### Post by jonsan191086 on 2012-10-12
> **YannBuntu said:**
> oldfred +1  (you need to fix the bootsector of sda3)


However, i see you are able to boot into your installed Ubuntu in UEFI mode:

```
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
```

so you probably don't need to fix the bootsector of sda1.

So i would:
1) fix the bootsector of sda3 as described by oldfred
2) reboot the PC, in the GRUB menu choose the "Windows UEFI" entry, and tell us if it boots Windows or not.

This is what i got trying with EFI GPT and select the sda3

```
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 3 P MS Data                   468992  123254148  122785157 [Basic data partition]

Boot sector
Status: OK

Backup boot sector
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

 [  Quit  ]  [  List  ] >[Org. BS ]  [Rebuild BS]  [  Dump  ]
```

What I have to select to do this ?? :confused:

---

### Post by oldfred on 2012-10-12
All you can do now is use testdisk and click on the RebuildBS. But that creates a XP type Boot sector. You then have to use a Windows 7 64 bit repairCD or USB to run chkdsk to convert it to Windows 7 style boot sector.

I have XP but ran chkdsk from a Windows 7 repairUSB. Chkdsk worked better but it converted from XP with ntldr to 7 with bootmgr as clear text in the boot sector. You can see tath in the compare boot sector/Dump command of Testdisk. There are also other differences, but using the repairCD I was able to write a new BS.

If chkdsk does not totally fix it then you may need to run this:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by jonsan191086 on 2012-10-23
> **oldfred said:**
> All you can do now is use testdisk and click on the RebuildBS. But that creates a XP type Boot sector. You then have to use a Windows 7 64 bit repairCD or USB to run chkdsk to convert it to Windows 7 style boot sector.

I have XP but ran chkdsk from a Windows 7 repairUSB. Chkdsk worked better but it converted from XP with ntldr to 7 with bootmgr as clear text in the boot sector. You can see tath in the compare boot sector/Dump command of Testdisk. There are also other differences, but using the repairCD I was able to write a new BS.

If chkdsk does not totally fix it then you may need to run this:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

Thanks all for the help i really appreciate this after all I can fix this only with reinstall windows and after that with the rescue boot disk fix the boot problem


:guitar::P:popcorn::KS

---

