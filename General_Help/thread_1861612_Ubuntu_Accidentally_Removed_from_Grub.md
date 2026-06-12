---
title: "Ubuntu Accidentally Removed from Grub"
date: 2011-10-15
forum: General Help
---

### Post by Unknownlight on 2011-10-15
I was using a grub customizer to clean up some of the clutter that's always displayed, and apparently I did something extremely wrong because now Grub only displays Windows 7 as an option to boot, no Ubuntu 11.10.

I assume that I have to boot Ubuntu from the grub command line or something, but I have no idea how to do that. Please help.

---

### Post by gsmanners on 2011-10-15
Try this (a very similar situation):

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Unknownlight on 2011-10-15
I used Boot Repair Disk and put on my USB. Boot Repair Disk did its whole deal, and at the end it said things have been repaired and I can now restart my computer.

It didn't work.

---

### Post by gsmanners on 2011-10-15
That's... not too surprising. I suggest using the Live desktop CD (or USB) method.

---

### Post by Unknownlight on 2011-10-15
What's that method?

Edit: Oh. you mean the first method listed?
...Okay, first that means it's time to download Ubuntu again. This'll take some time...

---

### Post by Unknownlight on 2011-10-15
Wait, how is the Live CD method different from what I just did?

---

### Post by drs305 on 2011-10-15
If you can boot the LiveCD, please download and run the boot info script. Chances are good we just need to get everything pointing to the correct location and can do it with a few simple commands. Post the contents of the file the script generates: RESULTS.txt

Click on the "BIS" link to go to the script's download page.

---

### Post by gsmanners on 2011-10-15
I would suggest using torrent or finding a good mirror (like [this one]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/11.10/release/")).

---

### Post by Unknownlight on 2011-10-15
Thanks for helping.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

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
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......!..:...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 21350 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    11,182,079    11,180,032  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     11,182,080    11,386,879       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          11,386,880   293,132,540   281,745,661   7 NTFS / exFAT / HPFS
/dev/sda4         293,134,334   488,396,799   195,262,466   5 Extended
/dev/sda5         293,134,336   480,364,543   187,230,208  83 Linux
/dev/sda6         480,366,592   488,396,799     8,030,208  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2048 MB, 2048728064 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001422 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            245     3,999,743     3,999,499   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B0BC5C94BC5C5746                       ntfs       Recovery
/dev/sda2        964018A640188EDD                       ntfs       System Reserved
/dev/sda3        08CE1A33CE1A1A10                       ntfs       
/dev/sda5        51441117-d2ee-4b3c-9cfc-fa9d7baf4c3b   ext4       
/dev/sda6        02e58ed0-9296-40b0-b345-603334617654   swap       
/dev/sdb1        1C12-2648                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 51441117-d2ee-4b3c-9cfc-fa9d7baf4c3b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 51441117-d2ee-4b3c-9cfc-fa9d7baf4c3b
  set locale_dir=($root)/boot/grub/locale
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 51441117-d2ee-4b3c-9cfc-fa9d7baf4c3b
insmod jpeg
if background_image /home/tomaszelig/Pictures/Wallpaper/Chell.jpg; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 964018A640188EDD
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=51441117-d2ee-4b3c-9cfc-fa9d7baf4c3b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=02e58ed0-9296-40b0-b345-603334617654 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-10-generic              3
               =                boot/initrd.img-2.6.38-11-generic              1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-2.6.38-10-generic                 2
               =                boot/vmlinuz-2.6.38-11-generic                 2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by gsmanners on 2011-10-15
Looks like you should boot the live CD and then get a terminal and type:

```
sudo grub-install /dev/sda
```

---

### Post by Unknownlight on 2011-10-16
Result:

```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

```

---

### Post by garvinrick4 on 2011-10-16
Boot your live cd (install cd using Try Ubuntu)
Open a terminal and copy and paste these one at a time.
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu
```
sudo update-grub
```Now should have both windows and Ubuntu in as menuentrys below to check it out.
```
grep menuentry /boot/grub/grub.cfg
```Keep link below for good tutorial and in drs305 signature will have lots of tutorials on all things grub.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Unknownlight on 2011-10-16
Well, I followed those instructions, and unfortunately they failed. Then I followed the instructions for "chroot"ing and re-installing grub from there. At the end of that, grub still thinks Windows 7 is the only OS on my computer. I don't understand it.

So now I have a new question: How do I purge everything relating to Ubuntu, including Grub, from my computer? So that I only have Windows left. 

I already have a backup of all my files on the Ubuntu side, so I'm thinking that it would be easier and faster to just re-install Ubuntu from scratch than deal with this.

---

### Post by garvinrick4 on 2011-10-16
Grub is in mbr not windows grub would need to restore with Windows cd.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Try this one time for me, I see no reason why we cannot point grub to look in sda5 for
Ubuntu.
```
sudo mount /dev/sda5 /mnt
```
```
sudo mount -o bind /dev /mnt/dev; sudo mount -o bind /dev/pts /mnt/dev/pts; sudo mount -o bind /proc /mnt/proc; sudo mount -o bind /sys /mnt/sys
```
```
sudo chroot /mnt
```
```
grub-install /dev/sda
```
```
update-grub
```
Should now show both Ubunut and windows when updates grub.
```
exit
```
```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys; sudo umount /mnt
```
```
sudo reboot
```
Should give you both operating systems to boot into.

---

### Post by gsmanners on 2011-10-16
To get Windows 7 fixed without Grub, you do this:

- insert your Windows 7 disc
- reboot
- select default language, time and keyboard
- select "Repair Your Computer", then "Command Prompt"

Then type the following:

```
bootsect /nt60 ALL
```

- eject the disc and reboot

---

### Post by Unknownlight on 2011-10-16
I can already tell something's gone wrong.

```
root@ubuntu:/# update-grub
Generating grub.cfg ...
using custom appearance settings
Found background image: /home/[name]/Pictures/Wallpaper/Abstract.jpg
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```

All this happens because I wanted to add a background image to Grub...

The thing is, I wanted to re-install Ubuntu because doing all this is making me think that the problem isn't with Grub, it's with Ubuntu. I think this might be the first time I restarted the computer since I updated to 11.10 (other than the initial restart to complete the update). I'm thinking something might have gone wrong with the upgrade.

---

### Post by Unknownlight on 2011-10-16
@gsmanners: No, Windows 7 works fine. I just would rather purge the computer of Ubuntu to save storage space before re-installing it.

---

### Post by garvinrick4 on 2011-10-16
> **Unknownlight said:**
>  I just would rather purge the computer of Ubuntu to save storage space before re-installing it.
Hello unknownlight,
Run this for me in the live cd and I will tell you how to install manually. We will not waste any space.
```
sudo fdisk -l
``` (lower case L)
```
sudo parted -l
``` (lower case L)
You have now become a official quest for me, we must get it running now.

---

### Post by Unknownlight on 2011-10-16
Thank you. Will do in just a moment. Just going to quickly back-up a few files first...

---

### Post by garvinrick4 on 2011-10-16
> Thank you. Will do in just a moment. Just going to quickly back-up a few files first... 	
Not going anywhere, have you subscribed.

---

### Post by Unknownlight on 2011-10-16
So sorry for taking so long, but now at least I'll lose nothing but a few Chrome bookmarks.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69bd4048

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11182079     5590016   27  Hidden NTFS WinRE
/dev/sda2   *    11182080    11386879      102400    7  HPFS/NTFS/exFAT
/dev/sda3        11386880   293132540   140872830+   7  HPFS/NTFS/exFAT
/dev/sda4       293134334   488396799    97631233    5  Extended
/dev/sda5       293134336   480364543    93615104   83  Linux
/dev/sda6       480366592   488396799     4015104   82  Linux swap / Solaris

Disk /dev/sdb: 2048 MB, 2048728064 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001422 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         245     3999743     1999749+   c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD2500BEVT-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  5725MB  5724MB  primary   ntfs            diag
 2      5725MB  5830MB  105MB   primary   ntfs            boot
 3      5830MB  150GB   144GB   primary   ntfs
 4      150GB   250GB   100GB   extended
 5      150GB   246GB   95.9GB  logical   ext4
 6      246GB   250GB   4111MB  logical   linux-swap(v1)


Model: SanDisk U3 Titanium (scsi)
Disk /dev/sdb: 2049MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      125kB  2048MB  2048MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 
```

---

### Post by garvinrick4 on 2011-10-16
#Ok you have 11.10 installation disk or USB. If not have to download one and BURN to
a disk. Link with show me hows in graphics below. USB installation flash drive is fine.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 

#Boot off of disk and hit space bar when icons show up on bottom at start.
Choose install Ubuntu
#Go through normal questions when asks you how to install choose.
"something else" on the bottom
#When it gets to the point where it shows partition table you double click on sda5
#Choose ext4, choose format (check box), choose / for mount point.
#Make sure it says boot loader (grub) go's in sda (defaults there but check it to make sure.
Now complete your install.
When through and boot into Ubuntu and:
sudo update-grub
Just to make sure all is fine.
Done. (You already have swap in sda6 do not need another one.)
All else will stay as is only partition effected is sda5 and it is being formatted with fresh install of / file system.  Good to go.

---

### Post by Unknownlight on 2011-10-16
> **garvinrick4 said:**
> #Make sure it says boot loader (grub) go's in sda (defaults there but check it to make sure.

Sorry, where does it say this?

---

### Post by garvinrick4 on 2011-10-16
> Sorry, where does it say this?
. Give me a second be right back give you specific page.

---

### Post by Unknownlight on 2011-10-16
Never mind, I see it, sorry. It's the thing at the bottom of the page. (I was scanning for the word "grub" and not "boot loader").

Thank you so much for the help.

This better work. XD

---

### Post by garvinrick4 on 2011-10-16
> **Unknownlight said:**
> Never mind, I see it, sorry. It's the thing at the bottom of the page. (I was scanning for the word "grub" and not "boot loader").

Thank you so much for the help.

This better work. XD Yes bottom of same page when partition table shows up. Looks like you are
making headway.

---

### Post by garvinrick4 on 2011-10-16
> Thank you so much for the help.

This better work. XD
Well I imagine you are up and going by now or would have heard something.
You enjoy your Ubuntu Unknownlight. Will keep this thread subscribed if you have
any more questions.

---

### Post by Unknownlight on 2011-10-16
Yup, everything's good now. Thanks so much for the help. Once it re-installed and was working properly I went to sleep; now it's morning and I'm changing all the settings to put it back the way it was.

It's ridiculous how many settings I changed since I first got Ubuntu. It's way more than I ever would've thought. XD

---

