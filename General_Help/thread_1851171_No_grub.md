---
title: "No grub"
date: 2011-09-27
forum: General Help
---

### Post by ArbiterOfTruth on 2011-09-27
Good day all,

I reinstalled Windows 7 & when I restarted there was no grub. I tried booting through the LiveCD & installing grub then running the "sudo update-grub" command. No luck. So I decided to install 10.10 straight from the CD. I did the install the way I normally do except that in 10.10 there is a section that says "device for boot loader installation". Having never come across this in the install of 9.04, 9.10 or 10.04, I selected my main HD which has Win7/Ubuntu on it. Still no grub. I even tried using EasyBCD but to no avail.

If someone could point me in the direction of a link that solves this problem simply & step by step, I would appreciate it greatly.

Thanks in advance,

---

### Post by ArbiterOfTruth on 2011-09-28
Is there nobody out there who knows of this problem being solved?

---

### Post by oldfred on 2011-09-28
To see where everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by ArbiterOfTruth on 2011-09-30
Thanks for the info! I will try it.

---

### Post by ArbiterOfTruth on 2011-09-30
I tried it but no luck. :(

Everything seemed to go well:

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/cmd2.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/cmd2.png)

Any other suggestions?

---

### Post by garvinrick4 on 2011-09-30
[COLOR=Red]Boot sdb drive first in Bios[/COLOR], looks ok, installed grub to sdb.
When booted into sdb drive and Ubuntu then open a terminal and;
```
sudo update-grub
```

---

### Post by ArbiterOfTruth on 2011-09-30
It's not a separate drive, it's just a partition.

---

### Post by garvinrick4 on 2011-09-30
It shows drive sda and drive sdb and linux is on [COLOR=Red]sdb[/COLOR] and that is where you installed grub:
sudo grub-install --root-directory=/media/sdb3 /dev/[COLOR=Red]sdb[/COLOR]

That is a different drive and sdb3 is the partition that grub looks for boot files.

---

### Post by garvinrick4 on 2011-09-30
Are you booting now if so please mark as Solved in upper right under thread tools.
If you are not booting lets get you booting.

---

### Post by ArbiterOfTruth on 2011-09-30
When I boot up I go straight to Windows. I do not see the grub that will allow me to select Ubuntu. Yes Ubuntu is on sdb3 but what I meant was, it is not on a separate drive by itself. 

This is my 160GB IDE backup drive:
[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/drive1.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/drive1.png)

and this is my main drive, split into 4 partitions that has Windows 7 & Ubuntu:
[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/drive2.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/drive2.png)

This is the boot drive as this is how I get to Windows. This is the 1st time I'm getting this particular problem. Maybe it was because I installed 10.10 directly whereas before I installed 10.04 then upgraded, but this is supposed to work as a standalone install.

What else can I try?

---

### Post by garvinrick4 on 2011-09-30
So you are booting off of sdb drive and first in chain sda is a data drive.
Put in your live cd or USB and boot into it again and open a terminal and copy and paste these
one at a time. We are going right into the linux file system and installing grub to your mbr.
```
sudo mount /dev/sdb3 /mnt
``````
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
``````
sudo chroot /mnt
``````
grub-install /dev/sdb
``````
update-grub
``````
exit
``````
sudo umount /mnt
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo reboot
```Hopefully now into ubuntu or windows at your choice in a grub menu.

---

### Post by oldfred on 2011-09-30
I think Windows 7  is like grub, if you install windows to sdb, it puts the boot loader & the boot partition on sda. So OP may be booting from sda in BIOS even though all the operating systems are really on sdb.

Boot script would really help us and knowing whether in BIOS you are booting sda or sdb.

---

### Post by ArbiterOfTruth on 2011-10-01
OK garv here I go. OldFred it has to be sdb because that is the only drive that has an OS on it. (well 2 actually) The other drive is just a backup.

---

### Post by garvinrick4 on 2011-10-01
> **ArbiterOfTruth said:**
> OK garv here I go. OldFred it has to be sdb because that is the only drive that has an OS on it. (well 2 actually) The other drive is just a backup.
Go ahead and run the code I gave you and see if it does the trick if not then it is of
what oldfred has stated he knows of what he speaks, he is a great grub man and you would do well to listen. One step at a time. 
[COLOR=Red]If does not work then have to boot sdb first in boot[/COLOR] [COLOR=Red]order[/COLOR] because this will for certain put grub in mbr (master boot record) of sdb. (you do have a boot flag in sda your data drive)
And or give oldfred the boot script that will tell all tells. I will help you run it if we need it.

---

### Post by ArbiterOfTruth on 2011-10-01
OK we are getting closer but not there yet. As you can see when I did "update-grub" it DID see the Windows 7 loader which always did the trick before. I thought you nailed it there garv. However I encountered a problem when I tried to enter the 3rd to last command:

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/as_ordered.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/as_ordered.png)

As you can see it says it's busy & I wasn't sure what to do so I tried it again then when it still said it was busy I just entered the last two commands you wrote. 

Guys while I am not a power use in Ubuntu I have installed 9.04, 9.10 & 10.04 without this problem. My WD 320GB drive is the only drive that has an OS on it & is listed as my 1st HD in the Boot Device Priority in my BIOS. This is the drive that is booting because I am getting Windows. I do see the boot flag on the other drive so if that is the problem, please tell me what I need to do to fix it.

Should I load Parted Magic & remove the boot flag from there?

**EDIT**: looking at this again, I think I see what you're saying. It sees the Windows 7 on sda. How can this be possible when there is no OS on that drive? I am more confused now.

---

### Post by garvinrick4 on 2011-10-01
> OK we are getting closer but not there yet. As you can see when I did  "update-grub" it DID see the Windows 7 loader which always did the trick  before. I thought you nailed it there garv. However I encountered a  problem when I tried to enter the 3rd to last command: The errors are ok do not worry about them the grub was installed
but look where windows was found sda1 where your data drive is. sda not sdb.
oldfred looks pretty good right now. I do not know if you are booting sdb first in order or
not. Do you want to try to look into your BIOS and see or run the boot script and do it
right so we can see what is going on.

---

### Post by ArbiterOfTruth on 2011-10-01
I will attempt the Boot Script procedure. Here I go.

---

### Post by garvinrick4 on 2011-10-01
Download this script to your Desktop or drop it on your Desktop and extract.
Right click on and use archive manager to extract on Desktop. Then run this code in a terminal.
```
sudo bash ~/Desktop/boot_info_script.sh
```Will make a RESULTS file on Desktop copy and paste here. Is a bit long so
after you paste to Message box highlight whole thing and hit the # sign in upper
right of Message box and will make it easy to read.

---

### Post by ksrsubramanian on 2011-10-01
Coool Dude,
    I had also the similar kind of problem
    

Try the Boot-repair-disk [https://help.ubuntu.com/community/Re...tallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") 

If it doesn't work getback to me


Good Luck,
Kallis

---

### Post by ksrsubramanian on 2011-10-01
l

---

### Post by ArbiterOfTruth on 2011-10-01
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    83,969,706    83,969,644   7 NTFS / exFAT / HPFS
/dev/sdb2          83,971,755   574,645,049   490,673,295   7 NTFS / exFAT / HPFS
/dev/sdb3         574,645,050   616,590,764    41,945,715  83 Linux
/dev/sdb4         616,590,765   625,137,344     8,546,580  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7743 MB, 7743995904 bytes
80 heads, 16 sectors/track, 11816 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    15,124,991    15,116,928   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        797EDA7E4FDC56D8                       ntfs       Backup
/dev/sdb1        AE307A52307A218F                       ntfs       Windows 7
/dev/sdb2        0456C07707115A12                       ntfs       Data
/dev/sdb3        32d7380b-02dc-448b-b936-c558d2d75452   ext4       Ubuntu
/dev/sdb4        c557c838-7f72-4b81-ae94-e053fe4fab45   swap       linux-swap
/dev/sdc1        B4FC-7487                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
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
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=32d7380b-02dc-448b-b936-c558d2d75452 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=32d7380b-02dc-448b-b936-c558d2d75452 ro single 
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
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 797eda7e4fdc56d8
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=32d7380b-02dc-448b-b936-c558d2d75452 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=c557c838-7f72-4b81-ae94-e053fe4fab45 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 286.145443916 = 307.246330880  boot/grub/core.img                             1
 286.160553932 = 307.262555136  boot/grub/grub.cfg                             1
 275.097710609 = 295.383917568  boot/initrd.img-2.6.35-22-generic              2
 286.143990517 = 307.244770304  boot/vmlinuz-2.6.35-22-generic                 1
 275.097710609 = 295.383917568  initrd.img                                     2
 286.143990517 = 307.244770304  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 40 96 11  |.X.MSDOS5.0..@..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 aa e6 00 35 07 00 00  00 00 00 00 02 00 00 00  |....5...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 87 74 fc b4 4e  4f 20 4e 41 4d 45 20 20  |..).t..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 42 4f  |..............BO|
000001b0  4f 54 4d 47 52 20 69 73  20 6d 69 73 73 69 6e 67  |OTMGR is missing|
000001c0  ff 0d 0a 44 69 73 6b 20  65 72 72 6f 72 ff 0d 0a  |...Disk error...|
000001d0  50 72 65 73 73 20 61 6e  79 20 6b 65 79 20 74 6f  |Press any key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 ac c1 ce 00 00 55 aa  |..............U.|
00000200




```


If I did something wrong or didn't do something, please let me know.

---

### Post by garvinrick4 on 2011-10-01
sda1 is where your boot files are for Windows. Instead of sdb1 where they need to be now.
You had Windows on sda at one time or you installed boot files there? Take them
out of your data drive /Boot and bootmgr and drop them in Windows in sdb1
See what they look like. Use live Cd again.

---

### Post by garvinrick4 on 2011-10-01
Now while in live cd still:
```
sudo mount /dev/sdb3 /mnt
```
```
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
```
```
sudo chroot /mnt
```
```
sudo update-grub
```
```
exit
```
```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```
```
sudo reboot
```

## Do make sure you are booting off of right drive in BIOS sdb not your data drive sda

---

### Post by ArbiterOfTruth on 2011-10-01
Garv there hasn't been an OS on that drive in years. Also before I made it my backup drive, I wiped it with WipeDrive Pro. If you look you will see that sdb1 has boot info as well & it actually says Windows 7 in the OS section. Also as stated before, the 320GB is listed as #1 in Boot Device Priority in the BIOS. Nevertheless I will follow your advice & see what happens.

---

### Post by garvinrick4 on 2011-10-01
>  => Windows is installed in the MBR of /dev/[COLOR=Red]sda[/COLOR]..
> [COLOR=Red]sda1[/COLOR]:      File system:       ntfs 
    Boot sector type:  Windows Vista/7     Boot sector info: 
  No errors found in the Boot Parameter Block.     
Operating System:       
Boot files:        /bootmgr /Boot/BCD> menuentry "Windows 7 (loader) (on /dev/[COLOR=Red]sda1[/COLOR])"They are pretty much there now ArbiterOfTruth. Lets see if we can get it booting both.

oldfreds post in this Thread:
> I think Windows 7  is like grub, if you install windows to sdb, it puts  the boot loader & the boot partition on sda. So OP may be booting  from sda in BIOS even though all the operating systems are really on  sdb. Boot script would really help us and knowing whether in BIOS you are booting sda or sdb.
He was pretty much right on I would have to say.

---

### Post by ArbiterOfTruth on 2011-10-01
I found the problem! :):):):):):):):)

I tried what you said: I cut out the "Boot" folder & the "bootmgr" file from the backup drive (sda) & placed it in the Windows 7 partition on the main drive (sdb1). That made it worse. Nothing booted up. It gave me an error message: BOOTMGR missing. Press Ctrl+Alt+Delete to restart. 

So I put the folder & file back to its original location & I could boot back into Windows again but I got the same problem, no grub to allow me to choose Ubuntu. Taking your advice into consideration, I looked at the Ubuntu partition & noticed something odd. There was a "boot" folder (I didn't think the lowercase b would be a factor so I overlooked it) but no "bootmgr" file, so I copied the one I had in sda to the Ubuntu partition & when I restarted.................GRUB!!!! I could only choose Ubuntu & memtest though but since this is the problem I am accustomed getting & solving, I booted into Ubuntu, brought up the terminal & ran "sudo update-grub". It found the Windows 7 loader & when I rebooted again there was grub with the Ubuntu AND Windows 7 options.

Thanks a lot garvinrick4 & oldfred. I really appreciate you guys taking the time to help me out.

---

### Post by garvinrick4 on 2011-10-01
> Thanks a lot garvinrick4 & oldfred. I really appreciate you guys taking the time to help me out. Hey thats no problem at all was our pleasure.

Hey its running, I thought if you did post 22 and then post 23 before trying to reboot.
And booting off of sdb in Bios would have boot files in sdb1 for windows and sdb3 controlling grub2 in mbr and updating grub would get you booting all on sdb without
using sda for anything. You did something I would love to see and I am sure others
also. (your first boot script was a tad unusual, oldfred could sense the problem before boot script)
Another boot script would be nice just to see what is going on. It works right now so
leave it be but if you can just run the boot script in ubuntu again just to see. Will not
effect anything just show whats going on. Enjoy your Ubuntu sure we will see you in the
Forums in the future. Post new boot script if you would, thanks.

---

### Post by ArbiterOfTruth on 2011-10-01
Here you go.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /bootmgr 
                       /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    83,969,706    83,969,644   7 NTFS / exFAT / HPFS
/dev/sdb2          83,971,755   574,645,049   490,673,295   7 NTFS / exFAT / HPFS
/dev/sdb3         574,645,050   616,590,764    41,945,715  83 Linux
/dev/sdb4         616,590,765   625,137,344     8,546,580  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7743 MB, 7743995904 bytes
80 heads, 16 sectors/track, 11816 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064    15,124,991    15,116,928   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        797EDA7E4FDC56D8                       ntfs       Backup
/dev/sdb1        AE307A52307A218F                       ntfs       Windows 7
/dev/sdb2        0456C07707115A12                       ntfs       Data
/dev/sdb3        32d7380b-02dc-448b-b936-c558d2d75452   ext4       Ubuntu
/dev/sdb4        c557c838-7f72-4b81-ae94-e053fe4fab45   swap       linux-swap
/dev/sdc1        B4FC-7487                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
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
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=32d7380b-02dc-448b-b936-c558d2d75452 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=32d7380b-02dc-448b-b936-c558d2d75452 ro single 
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
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 32d7380b-02dc-448b-b936-c558d2d75452
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set ae307a52307a218f
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

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=32d7380b-02dc-448b-b936-c558d2d75452 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=c557c838-7f72-4b81-ae94-e053fe4fab45 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 286.145443916 = 307.246330880  boot/grub/core.img                             1
 286.160893440 = 307.262919680  boot/grub/grub.cfg                             1
 275.097710609 = 295.383917568  boot/initrd.img-2.6.35-22-generic              2
 286.143990517 = 307.244770304  boot/vmlinuz-2.6.35-22-generic                 1
 275.097710609 = 295.383917568  initrd.img                                     2
 286.143990517 = 307.244770304  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 40 96 11  |.X.MSDOS5.0..@..|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 aa e6 00 35 07 00 00  00 00 00 00 02 00 00 00  |....5...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 87 74 fc b4 4e  4f 20 4e 41 4d 45 20 20  |..).t..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 42 4f  |..............BO|
000001b0  4f 54 4d 47 52 20 69 73  20 6d 69 73 73 69 6e 67  |OTMGR is missing|
000001c0  ff 0d 0a 44 69 73 6b 20  65 72 72 6f 72 ff 0d 0a  |...Disk error...|
000001d0  50 72 65 73 73 20 61 6e  79 20 6b 65 79 20 74 6f  |Press any key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 ac c1 ce 00 00 55 aa  |..............U.|
00000200



```Hope this gives you what you wanted.

---

### Post by oldfred on 2011-10-01
I do not think the bootmgr in the Ubuntu partition does anything. Windows cannot read Linux file systems and bootmgr is a windows program.

You did end up moving bootmgr & the BCD to your windows install. I think the windows boot in the MBR of sda will not work as it just looks at sda. If you ever want to directly boot Windows you would have to restore a windows boot loader to sdb.

With two drives, I suggest installing Windows on one drive (usually sda) and Ubuntu on the other. Then there are fewer issues of conflicts. If you ever reinstall, you may want to consider separating the systems by drive. But if it works now I would nto change anything.

I also suggest a liveCD or repairCD for the current version of every system installed. 

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by ArbiterOfTruth on 2011-10-01
> I do not think the bootmgr in the Ubuntu partition does anything.  Windows cannot read Linux file systems and bootmgr is a windows program.

Clearly it did make a difference as I now have the grub.

> You did end up moving bootmgr & the BCD to your windows install. I  think the windows boot in the MBR of sda will not work as it just looks  at sda. If you ever want to directly boot Windows you would have to  restore a windows boot loader to sdb.

When I did that as I mentioned, I was even getting into Windows & moving it back only returned me to the problem I had before. As I said before I was getting Windows with no problem, I just did not get grub that gave me the option to choose Ubuntu. When the 160GB drive was my ONLY HD it had Windows on it but that was YEARS ago. As soon as I got the 320GB I not only formatted the 160GB I wiped it with WipeDrive Pro which uses DOD level technology. I have no idea why it has any remnants of Windows on the backup drive.

> With two drives, I suggest installing Windows on one drive (usually sda)  and Ubuntu on the other. Then there are fewer issues of conflicts. If  you ever reinstall, you may want to consider separating the systems by  drive. But if it works now I would nto change anything.

I have successfully dual booted 9.04, 9.10 & 10.04 without this  problem. While I may not be as experienced as you, this is not my 1st  rodeo.

> I also suggest a liveCD or repairCD for the current version of every system installed. 

I always have a LiveCD for the different versions of Ubuntu I am using. Again thank you for you & garv's help in guiding me through this matter.

---

