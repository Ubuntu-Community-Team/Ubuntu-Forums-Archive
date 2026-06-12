---
title: "Multiboot Two Drives?"
date: 2011-11-27
forum: General Help
---

### Post by VcDeveloper on 2011-11-27
I have two HD's, 1) Ubuntu, and 2) Windows 7 on the same computer and Windows being the default.  Currently using the F10 during boot to switch back and forth, but would like to create a boot menu without using the F10.

Can anyone direct me to a tutorial on how to do this using either one as the default OS or the best and easiest way?

Thanks!...

---

### Post by fantab on 2011-11-27
> **VcDeveloper said:**
> I have two HD's, 1) Ubuntu, and 2) Windows 7 on the same computer and Windows being the default.  Currently using the F10 during boot to switch back and forth, but would like to create a boot menu without using the F10.

Can anyone direct me to a tutorial on how to do this using either one as the default OS or the best and easiest way?

Thanks!...

You can use GRUB to do this. 
On which HDD is Ubuntu, /dev/sda? and where is Grub? 

meanwhile see this on [**Grub2**]("https://help.ubuntu.com/community/Grub2")

---

### Post by oldfred on 2011-11-27
fantab is correct.

I like to keep each boot loader on the same drive as the system and a different system on every drive.

I would expect when you boot Ubuntu you should get a grub menu with Windows as one of the choices. if not run this:
```

sudo update-grub
```

Grub should give you a choice of which system to boot from. If you ever have major issues with the Ubuntu drive, then you still could use the BIOS to choose the Windows drive.

---

### Post by VcDeveloper on 2011-11-28
Here is the info:


```
eqmiller@studio-desktop:~$ sudo upadte-grub
[sudo] password for eqmiller: 
sudo: upadte-grub: command not found

```

What do I need to install for this?

Ubuntu Zorin 5 Ultimate is on /dev/sda:
```
eqmiller@studio-desktop:~$ sudo grub-probe -t device /boot/grub
/dev/sda1

eqmiller@studio-desktop:~$ sudo grub-probe -t fs_uuid /boot/grub
fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
```

And, I'm assuming correctly I should set /dev/sda as the default boot in order to use GRUB.

---

### Post by VcDeveloper on 2011-11-28
Will this cause a failure in updating GRUB to include Windows?


eqmiller@studio-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
mkdir: cannot create directory `/var/lib/os-prober/mount': No such file or directory
done

---

### Post by fantab on 2011-11-28
From BIOS change the HDD order to boot Ubuntu HDD first. If Ubuntu is on 1st HDD then it is on /dev/sda.

From what you say, your Grub is installed to /dev/sda

Will you post the output of**[ Boot Info Script]("http://bootinfoscript.sourceforge.net/")**

Also see this [Thread]("http://ubuntuforums.org/showthread.php?p=10057577")

---

### Post by VcDeveloper on 2011-11-28
The Result:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   960,135,167   960,133,120  83 Linux
/dev/sda2         960,137,214   976,771,071    16,633,858   5 Extended
/dev/sda5         960,137,216   976,771,071    16,633,856  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/ramzswap0                                          swap       
/dev/sda1        fd8f7860-b07a-48cc-99ce-ecfb04b30ca3   ext4       AnointedStudio
/dev/sda5        67389c54-e015-4d07-a76b-5744d38d9eb7   swap       
/dev/sdb1        DC1A51211A50F9CA                       ntfs       Anointed Media
/dev/sdc1        489618D09618BFFC                       ntfs       AnointedDocs

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
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
if background_color 8,50,90; then
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=fd8f7860-b07a-48cc-99ce-ecfb04b30ca3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
	echo	'Loading Linux 2.6.38-12-generic ...'
	linux	/boot/vmlinuz-2.6.38-12-generic root=UUID=fd8f7860-b07a-48cc-99ce-ecfb04b30ca3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fd8f7860-b07a-48cc-99ce-ecfb04b30ca3 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=fd8f7860-b07a-48cc-99ce-ecfb04b30ca3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root fd8f7860-b07a-48cc-99ce-ecfb04b30ca3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda1/etc/fstab: ================================

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
UUID=67389c54-e015-4d07-a76b-5744d38d9eb7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 310.135513306 = 333.005471744  boot/grub/core.img                             1
 346.370193481 = 371.912163328  boot/grub/grub.cfg                             1
   6.195709229 = 6.652592128    boot/initrd.img-2.6.38-12-generic              2
   2.415039062 = 2.593128448    boot/initrd.img-2.6.38-8-generic               2
   3.688789368 = 3.960807424    boot/vmlinuz-2.6.38-12-generic                 1
 310.133792877 = 333.003624448  boot/vmlinuz-2.6.38-8-generic                  1
   6.195709229 = 6.652592128    initrd.img                                     2
   2.415039062 = 2.593128448    initrd.img.old                                 2
   3.688789368 = 3.960807424    vmlinuz                                        1
 310.133792877 = 333.003624448  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  08 89 74 24 04 89 14 24  ff 51 24 85 ff 89 7e 54  |..t$...$.Q$...~T|
00000010  74 ae 8b 46 30 8b 10 89  7c 24 08 89 74 24 04 89  |t..F0...|$..t$..|
00000020  04 24 ff 52 24 8b 75 f8  8b 7d fc 89 ec 5d c3 90  |.$.R$.u..}...]..|
00000030  55 89 e5 83 ec 18 8b 45  08 8b 10 89 04 24 c7 44  |U......E.....$.D|
00000040  24 04 00 00 00 00 ff 52  5c b8 01 00 00 00 c9 c3  |$......R\.......|
00000050  55 89 e5 83 ec 18 8b 45  08 8b 50 24 31 c0 85 d2  |U......E..P$1...|
00000060  74 08 8b 02 89 14 24 ff  50 10 c9 c3 8d 74 26 00  |t.....$.P....t&.|
00000070  55 89 e5 56 83 ec 14 8b  45 08 80 b8 89 00 00 00  |U..V....E.......|
00000080  00 75 1a 8b 50 24 85 d2  74 13 8b 0a 8b 75 0c 89  |.u..P$..t....u..|
00000090  44 24 04 89 14 24 89 74  24 08 ff 51 0c 83 c4 14  |D$...$.t$..Q....|
000000a0  5e 5d c3 90 8d b6 00 00  00 00 8d bf 00 00 00 00  |^]..............|
000000b0  55 89 e5 83 ec 28 8b 45  0c 89 5d f4 8b 4d 10 89  |U....(.E..]..M..|
000000c0  75 f8 8b 75 08 89 7d fc  8b 50 24 e8 e7 f5 c4 ff  |u..u..}..P$.....|
000000d0  81 c3 24 45 94 00 85 d2  74 2e 8b 3a 89 4c 24 0c  |..$E....t..:.L$.|
000000e0  89 44 24 08 89 54 24 04  89 34 24 ff 57 28 83 ec  |.D$..T$..4$.W(..|
000000f0  04 89 f0 8b 5d f4 8b 75  f8 8b 7d fc 89 ec 5d c2  |....]..u..}...].|
00000100  04 00 8d b6 00 00 00 00  89 4c 24 08 89 44 24 04  |.........L$..D$.|
00000110  89 34 24 e8 e8 6c 00 00  83 ec 04 eb d4 90 66 90  |.4$..l........f.|
00000120  55 89 e5 83 ec 28 8b 45  0c 89 5d f4 8b 4d 10 89  |U....(.E..]..M..|
00000130  75 f8 8b 75 08 89 7d fc  8b 50 24 e8 77 f5 c4 ff  |u..u..}..P$.w...|
00000140  81 c3 b4 44 94 00 85 d2  74 2e 8b 3a 89 4c 24 0c  |...D....t..:.L$.|
00000150  89 44 24 08 89 54 24 04  89 34 24 ff 57 24 83 ec  |.D$..T$..4$.W$..|
00000160  04 89 f0 8b 5d f4 8b 75  f8 8b 7d fc 89 ec 5d c2  |....]..u..}...].|
00000170  04 00 8d b6 00 00 00 00  89 4c 24 08 89 44 24 04  |.........L$..D$.|
00000180  89 34 24 e8 c8 6e 00 00  83 ec 04 eb d4 90 66 90  |.4$..n........f.|
00000190  55 89 e5 83 ec 28 8b 45  0c 89 5d f4 8b 4d 10 89  |U....(.E..]..M..|
000001a0  75 f8 8b 75 08 89 7d fc  8b 50 24 e8 07 f5 c4 ff  |u..u..}..P$.....|
000001b0  81 c3 44 44 94 00 85 d2  74 2e 8b 3a 89 4c 00 fe  |..DD....t..:.L..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 fd 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

What hd number I use for this setup: hd0 or hd1?
```
menuentry "Microsoft Windows 7" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set DC1A51211A50F9CA
drivemap -s (hd0) ${root}
chainloader +1
}
```

---

### Post by VcDeveloper on 2011-11-28
I've successfully created the menu using:

```
menuentry "Microsoft Windows 7" {
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set DC1A51211A50F9CA
drivemap -s (hd1) ${root}
chainloader +1
}

```

but it gives me an error msg saying "no parameters used" and still boots Windows 7.  What parameters do I need to remove the msg.  Is Windows 7 looking something during boot time?

---

### Post by oldfred on 2011-11-28
When you installed Windows was it the first drive or the second?

If you reinstall a Windows boot loader to sdb and boot that in BIOS does it then work? BIOS boot will make that the first drive. The drivemap in grub tries to make windows think it is the first drive. With 11.04 you also may not have synaptic installed. Not sure how to enable universe without synaptic. Does Software Center let you download lilo? If need be just install synaptic, it was the first thing I installed in 11.04, but I just experimented in 11.04 and still use 10.10.

From Ubuntu you can install a Windows boot loader.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by efflandt on 2011-11-28
You should not really need to install anything to put or restore the Windows mbr on sdb.  You should already have syslinux (used to create bootable floppies or USB).

```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
```

That is what I did (except /dev/sda instead of sdb) when I somehow ended up with grub in the mbr of my Win7 drive instead of on sda4.  If I want to boot grub on sda4 (Maverick) I would just need to mark sda4 the boot partition instead of sda2 that Win7 boots from.  But I actually currently boot everything from 11.10's grub in the mbr of sdb.

---

### Post by VcDeveloper on 2011-11-29
> **oldfred said:**
> When you installed Windows was it the first drive or the second?


Well, I went through a series of installs with Windows ending up on /dev/sdb and Zorin on /dev/sda.  

[LIST=1]
[*]Installed Ubuntu Studio 10.04, then
[*]6 months later Windows 7, set BIO's to boot Window 7 first,
[*]This past week replaced Ubuntu with Zorin 5 Ultimate and I couldn't boot into Windows so I had to run the auto fix to restore mbr.
[*]then I couldn't boot Zorin, so from Windows I just deleted volume, reformat it and re-installed Zorin.
[/LIST]
I set BIO's to boot from Zorin first, but when using the custom menu above to boot Windows, I get the error msg.  I can boot to Windows normally using F10.

So where do I go from here to get a clean GRUB menu?

---

### Post by oldfred on 2011-11-29
I have not seen a no parameters used message, but if you set root to hd1 and then use drivemap to map root and hd1 that seems like it is saying it did not have to map drives??

Normally the drivemap is for XP as the boot.ini uses fixed drive numbers. I think 7  is more like Ubuntu and has something like a UUID internally to keep track of partitions. Look at your BCD with BCDedit and it will not say rdisk(0) or rdisk(1) like a boot.ini does.

---

### Post by VcDeveloper on 2011-12-06
Here's what BDCEdit say's about my boot device:```

Default: Windows 7 
Timeout: Skipped 
EasyBCD Boot Device: C:\ 
 
Entry #1 
Name: Windows 7 
BCD ID: {current} 
Drive: C:\ 
Bootloader Path: \Windows\system32\winload.exe
```

How do I add this to my menu?

---

### Post by oldfred on 2011-12-06
I know nothing about EasyBCD.

A few here do use EasyBCD, if not try this:

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

