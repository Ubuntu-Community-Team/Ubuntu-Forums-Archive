---
title: "GRUB Rescue Prompt"
date: 2011-04-14
forum: General Help
---

### Post by walpurgisnacht on 2011-04-14
Ok, so to get things out of the way, I am a total Linux n00b. Installed it yesterday and everything. Everything was going well, so I shut it down and go to bed. When I get up in the morning and turn on my computer, I got this:

error: no such device: 79067cab-78d2-4303-abdf-b1453098a6ef
Entering rescue mode.

And then I get the grub rescue prompt. Which, as a n00b, I have no idea how to deal with. I have looked around, but I haven't seen any definitive answers that have solved my problem, or didn't go over my head completely. 

So info: I installed Ubuntu version 10.10 using WUBI.exe and my USB drive. In order to do that, though, I had to install PLoP Boot Manager since my computer wouldn't let me boot from it directly. Once I got this problem, I realized how screwed I was - because my bootable USB was effectively worthless without access to that program - I created a bootable disc with a CD. 

So...help? Please?

---

### Post by wilee-nilee on 2011-04-14
First to install a wubi you would not need to boot the thumb.

So click on the bootscript link in my signature, follow the instructions to generate a text file. Come back to the thread, open a reply click on the (#) in the reply panel to generate code tags paste all the text from the generated file between.

This will give us a better picture of the setup than most any of us could give with a lot of posts it is quite helpful, read the instructions carefully and post the text in code tags as described or look in my signature for another code tag manual method.

---

### Post by lmarmisa on 2011-04-14
Welcome to the Forums.

Please, start your system from a Ubuntu Live CD or USB and visit the page

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Try to run the Boot Info Script and post the results on this thread.

According to that information you will receive more help.

Best regards,

Luis

---

### Post by walpurgisnacht on 2011-04-14
Thanks for the links, but another problem seems to have arisen.

I went to try the link in Firefox, but it started to crash repeatedly, even when I started a new instance. So I rebooted the computer.

And therein the trouble lies. I cannot get past the "Try it or Install it" screen. It just...sits there, for minutes, until finally I lose patience and try once more to reboot. Most of the time, it doesn't even get there, just sitting at a strange black screen that pops up after the ubuntu logo loads. It might just be that I'm being impatient, but this has occurred several times in a row. It happened before, too, but I was able to get past the "Try it" screen, once. Now I can't at all. I'll keep working at it, though...

---

### Post by wilee-nilee on 2011-04-14
As soon as you turn on the computer to boot the live media hold down the shift key, this will get you to the first menu, hit f6 choose  nomodeset and see if a low graphic startup will work.

---

### Post by walpurgisnacht on 2011-04-14
Got it.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   948,058,111   947,648,512   7 HPFS/NTFS
/dev/sda3         948,058,112   976,560,127    28,502,016   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       79067cab-78d2-4303-abdf-b1453098a6ef   ext4                                     
/dev/sda1        441ADFC61ADFB362                       ntfs       SYSTEM                        
/dev/sda2        2450D1BD50D19640                       ntfs                                     
/dev/sda3        F0DE59B8DE5977B4                       ntfs       RECOVERY                      
/dev/sda4        2E22-D381                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2450d1bd50d19640
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2450d1bd50d19640
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2450d1bd50d19640
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2450d1bd50d19640
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 441adfc61adfb362
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2450d1bd50d19640
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f0de59b8de5977b4
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

============================= sda2/Wubi/etc/fstab: =============================
```

---

### Post by wilee-nilee on 2011-04-14
You have the grub bootloader in the mbr you want the MS bootloader there. Watch Ubuntu for grub updates and don't install them you're using the MS boot.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
```
BootRec.exe /fixmbr
``` 
Visual helper
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

This will reload the mbr Ubuntu should boot from there, here is a W7 recovery ISO link if you don't have one.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You can load this to a thumb if needed in a Ubuntu set up, format the thumb to a NTFS partition, right click the partition then manage flags click boot, then right click the ISO and extract to the thumb using the file roller or what ever it is called.

---

### Post by bcbc on 2011-04-14
I see many people installing burg on Wubi and this is usually the result. Follow Wilee-nilee's advice to reinstall the windows boot loader.

Burg does actually have some Wubi-specific installation instructions - but for some reason it doesn't seem like everyone gets to see them (and I've never heard of anyone using it successfully on Wubi, nor have I tried it myself).

My advice: avoid messing with grub or bootloaders if you are using Wubi.

---

### Post by walpurgisnacht on 2011-04-14
Thank you so much! Once I got a Recovery Disk .iso (which involved searching around until I found a direct download...stupid school computers), it went perfectly. I appreciate all the help you've been. Sorry for the noobishness.

---

### Post by Ungrull on 2011-05-19
Geezus. i have looked through and through on these forums all to no avail. Grub rescue>....... arg. i have a no cd netbook. in windows i deleted ubuntu partition. there is another partition with my acer recovery on it. tried wiping and reinstalling grub. running off of my usb. i cant log onto anything else. im sorry if this has already been answered but after 5 hours reading these forums, all the answers and tips are starting to look the same. 

God help us all


results.txt 

                                      

  	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }```
Boot Info Script 0.60    from 17 May 2011   ============================= Boot Info Summary: ===============================   => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector      1 of the same hard drive for core.img. core.img is at this location and      looks in partition 5 for (,msdos5)/boot/grub.  => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.  sda1: __________________________________________________________________________      File system:       vfat     Boot sector type:  Windows XP: FAT32     Boot sector info:   No errors found in the Boot Parameter Block.     Operating System:       Boot files:        /ntldr /NTDETECT.COM  sda2: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows XP     Boot sector info:   No errors found in the Boot Parameter Block.     Operating System:  Windows XP     Boot files:        /boot.ini /ntldr /NTDETECT.COM  sda3: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  Unknown     Boot sector info:    sda5: __________________________________________________________________________      File system:            Boot sector type:  Unknown     Boot sector info:       Mounting failed:   mount: unknown filesystem type ''  sdb1: __________________________________________________________________________      File system:       vfat     Boot sector type:  SYSLINUX 3.85 2010-02-20     Boot sector info:   Syslinux looks at sector 7410152 of /dev/sdb1 for its                         second stage. No errors found in the Boot Parameter                         Block.     Operating System:       Boot files:        /syslinux.cfg /ldlinux.sys  ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics /dev/sda2    *     10,233,405   233,779,017   223,545,613   7 NTFS / exFAT / HPFS /dev/sda3         233,779,198   312,580,095    78,800,898   5 Extended Extended partition linking to another extended partition. /dev/sda5     ? 3,082,312,512 3,952,348,829   870,036,318  de Dell Utility  /dev/sda5 ends after the last sector of /dev/sda the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3  Drive: sdb _____________________________________________________________________  Disk /dev/sdb: 4032 MB, 4032626688 bytes 128 heads, 27 sectors/track, 2279 cylinders, total 7876224 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sdb1    *             56     7,876,223     7,876,168   b W95 FAT32   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        0159-6699                              vfat       PQSERVICE /dev/sda2        32F0B915F0B8DFF1                       ntfs       ACER /dev/sdb1        5613-16A9                              vfat       MR TINY  ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)   ================================ sda2/boot.ini: ================================  -------------------------------------------------------------------------------- [boot loader] timeout=30 default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect --------------------------------------------------------------------------------  ============================== sdb1/syslinux.cfg: ==============================  -------------------------------------------------------------------------------- default menu.c32 prompt 0 menu title UNetbootin timeout 100  label unetbootindefault menu label Default kernel /ubnkern append initrd=/ubninit file=/cdrom/preseed/ubuntu-netbook.seed boot=casper quiet splash --  label ubnentry0 menu label ^Help kernel /ubnkern append initrd=/ubninit   label ubnentry1 menu label ^Try Ubuntu Netbook without installing kernel /casper/vmlinuz append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-netbook.seed boot=casper  quiet splash --  label ubnentry2 menu label ^Install Ubuntu Netbook kernel /casper/vmlinuz append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu-netbook.seed boot=casper only-ubiquity  quiet splash --  label ubnentry3 menu label ^Check disc for defects kernel /casper/vmlinuz append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --  label ubnentry4 menu label Test ^memory kernel /install/mt86plus append initrd=/ubninit   label ubnentry5 menu label ^Boot from first hard disk kernel /ubnkern append initrd=/ubninit   --------------------------------------------------------------------------------  ================= sdb1: Location of files loaded by Syslinux: ==================             GiB - GB             File                                 Fragment(s)              ?? = ??             ldlinux.sys                                    1             ?? = ??             menu.c32                                       1             ?? = ??             syslinux.cfg                                   1  ============== sdb1: Version of COM32(R) files used by Syslinux: ===============   menu.c32                           :  COM32R module (v3.xx)  ======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda3  00000000  2d e6 18 c1 0c 2a 39 36  f5 89 a3 27 79 b7 75 75  |-....*96...'y.uu| 00000010  1a 51 85 ea 5f 56 f8 3b  02 a8 5a ff 96 34 e4 8b  |.Q.._V.;..Z..4..| 00000020  5f 66 32 d9 c8 1f 30 de  4f a6 4f 6d f1 99 0a f7  |_f2...0.O.Om....| 00000030  a6 6e 31 d8 e0 09 1b b4  92 32 e6 12 6f b5 ff 35  |.n1......2..o..5| 00000040  e9 ed bf b4 4a ff 21 65  d9 58 49 7f 8a b9 1c cc  |....J.!e.XI.....| 00000050  35 05 71 3a 9a d4 74 20  0c 8c 87 59 3f 36 b2 b0  |5.q:..t ...Y?6..| 00000060  94 6a 4e 25 bd 34 46 48  8c 19 37 be 14 27 52 e9  |.jN%.4FH..7..'R.| 00000070  ce 5b dc 17 37 35 4d 10  6e 30 b4 1d c7 d4 18 06  |.[..75M.n0......| 00000080  06 73 8a f5 ee b6 c8 a8  58 6e aa 07 73 68 74 cf  |.s......Xn..sht.| 00000090  43 00 22 49 01 c8 c6 01  b7 d8 ed c8 97 f9 c2 92  |C."I............| 000000a0  f7 c3 ab 64 bc 89 74 c0  92 43 bf 1a b6 25 c5 0a  |...d..t..C...%..| 000000b0  de 31 84 48 50 ae 1b 04  a7 3e 2d 68 b1 c0 6c 66  |.1.HP....>-h..lf| 000000c0  c7 49 f2 55 3a 17 e8 8e  b4 5d d8 cc e0 a4 5a 3f  |.I.U:....]....Z?| 000000d0  a5 57 9b 26 b9 8f 16 0a  84 56 dc 8d f0 54 41 11  |.W.&.....V...TA.| 000000e0  5e f0 53 31 b8 e7 14 5a  ce 1a 3d ac 7d 0a 63 49  |^.S1...Z..=.}.cI| 000000f0  ad 44 5b 87 4d 5e 3f 75  4e 41 9e b8 d4 e1 e7 40  |.D[.M^?uNA.....@| 00000100  07 ed 47 d1 48 7f a8 13  34 86 6b cc f8 84 ba 42  |..G.H...4.k....B| 00000110  0f 13 83 ca 4f 16 9a 72  30 e6 07 c8 f6 24 67 0f  |....O..r0....$g.| 00000120  f6 61 12 8f 23 89 02 e1  79 91 33 8a 83 e2 63 01  |.a..#...y.3...c.| 00000130  fa 79 70 60 b8 52 76 af  1e b9 7c e0 6a 1d 95 d5  |.yp`.Rv...|.j...| 00000140  ef 19 c6 31 bf cc 1c ce  ef 09 11 b3 97 7d 18 a5  |...1.........}..| 00000150  99 00 fd 78 9c 62 46 29  4e 32 e4 3a b3 a5 f4 17  |...x.bF)N2.:....| 00000160  3e 42 49 99 e3 4a 81 95  99 d6 cd 72 36 4c 43 5d  |>BI..J.....r6LC]| 00000170  ec da a3 8d 3d 23 f8 49  de 7e e8 a8 82 f7 4b 37  |....=#.I.~....K7| 00000180  92 ae aa 60 18 79 1d 52  a7 67 04 b1 d8 18 c0 d4  |...`.y.R.g......| 00000190  2a c9 55 52 62 da a0 d7  5e c7 40 bf 8c 7d 6b 24  |*.URb...^.@..}k$| 000001a0  e7 da a5 40 65 2e 6e a5  e7 30 b3 77 91 82 9d 42  |...@e.n..0.w...B| 000001b0  0f a0 b2 83 c2 36 8d 83  c9 ec d7 30 76 c1 00 fe  |.....6.....0v...| 000001c0  ff ff 05 fe ff ff c3 b7  7f 04 3f b0 32 00 00 00  |..........?.2...| 000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| * 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200  Unknown BootLoader on sda5    =============================== StdErr Messages: ===============================  hexdump: /dev/sda5: No such file or directory hexdump: /dev/sda5: No such file or directory  
```


Provehito In Altum,
*"Launch forth into the deep"*

---

### Post by bcbc on 2011-05-19
> **Ungrull said:**
> Geezus. i have looked through and through on these forums all to no avail. Grub rescue>....... 

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
After the first command hit enter to ignore the warning screen - not relevant as you are using a simple form of lilo. This will install a bootloader that is equivalent to Windows' bootloader.

---

### Post by Ungrull on 2011-05-19
BCBC!!!!!!!!! You rock. Thank you very much. :D

---

### Post by bcbc on 2011-05-19
> **Ungrull said:**
> BCBC!!!!!!!!! You rock. Thank you very much. :D

Great! You're welcome.

---

