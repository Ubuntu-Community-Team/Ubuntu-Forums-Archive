---
title: "dual boot issues"
date: 2011-02-04
forum: General Help
---

### Post by pshooter on 2011-02-04
i need win7 to run a rip software for my new roland printer, but i want to use and learn ubuntu for personal use. i tried installing win7 then installing ubuntu next to it. now wheni start the laptop it only starts ubuntu and there is no option for win7. can someone help here?
 
bb

---

### Post by lindsay7 on 2011-02-04
type this in the terminal using Ubuntu and post the result/

sudo fdisk -l   

that is the lower case letter L not the number 1.  The results of this command will show what is on your hard drive.

---

### Post by pshooter on 2011-02-05
here is a screen shot

bb

---

### Post by oldfred on 2011-02-05
The hidden(in windows) 100MB windows boot partition and a large NTFS partition are there so it looks ok. Sometimes the installer just does not see it.

sudo update-grub

If that does not list your windows and add it to the grub menu.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by pshooter on 2011-02-05
so i got the grub menu to come up at boot, but it lists the win7 bootloader at sda1 and win7 is actually installed on sda2. so it will still only boot ubuntu. still trying to figure out the directory/ path thing to run the bash. thanks for all the help so far.
 
bb

---

### Post by oldfred on 2011-02-05
Standard installs of windows 7 have a hidden (in windows) 100MB boot/recovery partition. That is so you can encrypt the main install. You cannot encrypt the boot loader. It is also for future use with efi, but windows has not done a good job in implementing UEFI and gpt partition support. Ubuntu for once is way ahead of windows. Of course Apple has been using EFI and gpt since it converted to Intel.

---

### Post by pshooter on 2011-02-06
what am i doing wrong here?

---

### Post by oldfred on 2011-02-06
Linux is case sensitive, windows is not.

It is Desktop not desktop

From link:
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```It is often better to copy and paste commands. Even spaces can be important.

You can use up arrow on terminal to see last command. Or history to see all commands.
You also can start typing boo and then hit tab and it will complete or partially try to complete command if muliple versions.

---

### Post by pshooter on 2011-02-06
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 222899216 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   121,955,203   121,748,356   7 HPFS/NTFS
/dev/sda3         121,956,350   234,440,703   112,484,354   5 Extended
/dev/sda5         121,956,352   229,756,927   107,800,576  83 Linux
/dev/sda6         229,758,976   234,440,703     4,681,728  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8E9CFB4F9CFB2FF7                       ntfs       System Reserved               
/dev/sda2        585C13645C133BE6                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        674f82b7-0d8b-4b86-900f-38b142e4754f   ext4                                     
/dev/sda6        9690c6ef-c8b0-4149-8014-7c0fe5f704df   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 674f82b7-0d8b-4b86-900f-38b142e4754f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 674f82b7-0d8b-4b86-900f-38b142e4754f
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 674f82b7-0d8b-4b86-900f-38b142e4754f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=674f82b7-0d8b-4b86-900f-38b142e4754f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 674f82b7-0d8b-4b86-900f-38b142e4754f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=674f82b7-0d8b-4b86-900f-38b142e4754f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 674f82b7-0d8b-4b86-900f-38b142e4754f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 674f82b7-0d8b-4b86-900f-38b142e4754f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 8e9cfb4f9cfb2ff7
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=674f82b7-0d8b-4b86-900f-38b142e4754f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9690c6ef-c8b0-4149-8014-7c0fe5f704df none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 114.1GB: boot/grub/core.img
  75.5GB: boot/grub/grub.cfg
  63.2GB: boot/initrd.img-2.6.35-22-generic
 114.1GB: boot/vmlinuz-2.6.35-22-generic
  63.2GB: initrd.img
 114.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  20 20 3b 20 5b 2a 30 42  30 33 2e 30 30 32 30 2e  |  ; [*0B03.0020.|
00000010  30 30 30 32 2e 32 42 31  37 5d 20 23 20 44 49 41  |0002.2B17] # DIA|
00000020  4d 4f 4e 44 20 57 49 54  48 20 52 49 47 48 54 20  |MOND WITH RIGHT |
00000030  48 41 4c 46 20 42 4c 41  43 4b 0a 32 42 31 38 20  |HALF BLACK.2B18 |
00000040  20 3b 20 5b 2a 30 42 30  34 2e 30 30 32 30 2e 30  | ; [*0B04.0020.0|
00000050  30 30 32 2e 32 42 31 38  5d 20 23 20 44 49 41 4d  |002.2B18] # DIAM|
00000060  4f 4e 44 20 57 49 54 48  20 54 4f 50 20 48 41 4c  |OND WITH TOP HAL|
00000070  46 20 42 4c 41 43 4b 0a  32 42 31 39 20 20 3b 20  |F BLACK.2B19  ; |
00000080  5b 2a 30 42 30 35 2e 30  30 32 30 2e 30 30 30 32  |[*0B05.0020.0002|
00000090  2e 32 42 31 39 5d 20 23  20 44 49 41 4d 4f 4e 44  |.2B19] # DIAMOND|
000000a0  20 57 49 54 48 20 42 4f  54 54 4f 4d 20 48 41 4c  | WITH BOTTOM HAL|
000000b0  46 20 42 4c 41 43 4b 0a  32 42 31 41 20 20 3b 20  |F BLACK.2B1A  ; |
000000c0  5b 2a 30 42 30 36 2e 30  30 32 30 2e 30 30 30 32  |[*0B06.0020.0002|
000000d0  2e 32 42 31 41 5d 20 23  20 44 4f 54 54 45 44 20  |.2B1A] # DOTTED |
000000e0  53 51 55 41 52 45 0a 32  42 32 30 20 20 3b 20 5b  |SQUARE.2B20  ; [|
000000f0  2a 30 42 30 37 2e 30 30  32 30 2e 30 30 30 32 2e  |*0B07.0020.0002.|
00000100  32 42 32 30 5d 20 23 20  57 48 49 54 45 20 50 45  |2B20] # WHITE PE|
00000110  4e 54 41 47 4f 4e 0a 32  42 32 31 20 20 3b 20 5b  |NTAGON.2B21  ; [|
00000120  2a 30 42 30 38 2e 30 30  32 30 2e 30 30 30 32 2e  |*0B08.0020.0002.|
00000130  32 42 32 31 5d 20 23 20  57 48 49 54 45 20 48 45  |2B21] # WHITE HE|
00000140  58 41 47 4f 4e 0a 32 42  32 32 20 20 3b 20 5b 2a  |XAGON.2B22  ; [*|
00000150  30 42 30 39 2e 30 30 32  30 2e 30 30 30 32 2e 32  |0B09.0020.0002.2|
00000160  42 32 32 5d 20 23 20 42  4c 41 43 4b 20 48 45 58  |B22] # BLACK HEX|
00000170  41 47 4f 4e 0a 32 42 32  33 20 20 3b 20 5b 2a 30  |AGON.2B23  ; [*0|
00000180  42 30 41 2e 30 30 32 30  2e 30 30 30 32 2e 32 42  |B0A.0020.0002.2B|
00000190  32 33 5d 20 23 20 48 4f  52 49 5a 4f 4e 54 41 4c  |23] # HORIZONTAL|
000001a0  20 42 4c 41 43 4b 20 48  45 58 41 47 4f 4e 0a 32  | BLACK HEXAGON.2|
000001b0  43 45 35 20 20 3b 20 5b  2a 30 42 30 42 2e 00 df  |CE5  ; [*0B0B...|
000001c0  d3 ff 83 df d3 ff 02 00  00 00 00 e8 6c 06 00 df  |............l...|
000001d0  d3 ff 05 df d3 ff 02 e8  6c 06 00 78 47 00 00 00  |........l..xG...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200  
```

---

### Post by oldfred on 2011-02-06
You installed grub ot sda1 not sda. Since sda1 is a windows partition it has to have NTFS signature and boot code.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You also then need to install grub2 to sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by pshooter on 2011-02-06
i will try this tomorrow. thank you for all your help. 
 
bb

---

### Post by srs5694 on 2011-02-07
> **oldfred said:**
> It is also for future use with efi, but windows has not done a good job in implementing UEFI and gpt partition support. Ubuntu for once is way ahead of windows.

It's a bit more complicated than that. The 64-bit version of Windows 7 (and I think also of Vista and even XP) boots very nicely using UEFI on GPT disks. I've done a couple of test installs this way, and it works very well. (With real UEFI implementations; there are deficiencies in VirtualBox's UEFI that cause problems. Also, Apple's EFI is an old version that's reportedly not compatible with Windows.) Linux's (U)EFI support varies from one distribution to another, and I'm pretty sure that Ubuntu is deficient on that score through version 10.10. The 11.04 alpha releases include (U)EFI support, and I successfully managed a test install on one Intel motherboard using the 11.04 alpha 2. I had serious video problems with another system using UEFI DUET, but that was a video driver issue that I don't think was EFI-related. VirtualBox was a wash because of EFI framebuffer video problems. Some of these problems may be alpha-related, of course.

No 32-bit version of Windows can boot using (U)EFI. This isn't a big drawback because, AFAIK, no mainstream PC with a 32-bit x86 CPU includes (U)EFI firmware. A few early Intel-based Macs have 32-bit EFIs, but as I just noted, even the 64-bit version of Windows won't boot in EFI mode on these systems. (Apple uses a BIOS emulation feature in its EFI implementation to enable Windows to dual-boot on its computers.)

Where Ubuntu trounces Windows is in GPT support on BIOS-based computers. Ubuntu can boot from such disks just fine, but Windows can't; Windows requires MBR on its boot disks on BIOS-based computers. (On the flip side, Windows reportedly requires GPT on UEFI-based computers, despite the fact that the (U)EFI specification says that it's OK to boot from an MBR disk. I don't know offhand if Linux can boot from an MBR disk on a (U)EFI-based computer.) Both Windows (Vista and 7) and Ubuntu can handle GPT data (non-boot) disks.

So to sum up, Ubuntu is much more flexible about its firmware/partition system matchups, but it's still catching up to Windows in (U)EFI support.

---

### Post by pshooter on 2011-02-07
well i am not sure what i did wrong now. i am sending this via live cd. ubuntu is so cool, yet so frustrating.

bb

---

### Post by oldfred on 2011-02-07
Your commands are mixing up drives & partitions. A drive is sda, sdb, sdc etc. A partition is sda1, sda2, sdb1, sdc1 etc.

You have to mount the linux partition with grub so grub2 knows where the rest of its files are. Then you install to the drive.

If sda5 is the linux partition with grub files:
sudo mount /dev/sda5 /mnt
Then you install to the drive sda:
sudo grub-install --root-directory=/mnt/ /dev/sda

If you mounted the wrong thing to /mnt then you may have to start over. You can umount /mnt or reboot.

---

### Post by pshooter on 2011-02-07
success! thank you for your patience with me and for being so helpful. grub is in the right place and both os's boot up and run.

bb

---

### Post by oldfred on 2011-02-07
Glad that worked.

I see you have flexnet, which grub2 created a workaround for proprietary windows software that uses the boot area to hide serial numbers or other DRM info. Some other windows7 software does the same, and grub2 may not have workarounds. Often HP & DELL related. If you have issues post back.

---

### Post by pshooter on 2011-02-07
> **oldfred said:**
> Glad that worked.
 
I see you have flexnet, which grub2 created a workaround for proprietary windows software that uses the boot area to hide serial numbers or other DRM info. Some other windows7 software does the same, and grub2 may not have workarounds. Often HP & DELL related. If you have issues post back.
 
not sure what you mean here, but i have not had any issues so far. although i have to revert back to xp from 7 because i cannot get the network adapter drivers to install in 7. but that's an issue for another forum. thanks again. the feeling of accomplishment is a joyous one.
 
bb

---

