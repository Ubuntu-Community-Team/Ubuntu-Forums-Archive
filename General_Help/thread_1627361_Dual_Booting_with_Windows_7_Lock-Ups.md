---
title: "Dual Booting with Windows 7 Lock-Ups"
date: 2010-11-21
forum: General Help
---

### Post by silver boost on 2010-11-21
Whats up all.

Well to get started i need help understanding why grub locks up during boot. 

I installed Mint 2 weeks ago and this has been happening since day one.
For some reason when trying to either boot from my distro or os the keys lock not letting me chose any of the options.

what ever option is selected during the boot that would be the selection i will be entering into.

This happen randomly not always sometime i would have to boot 4 or 5 times before grub let's me chose any of the option's.
Here is where my Window's and Linux partition stand.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0c5913d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2551       45773   347184128    7  HPFS/NTFS
/dev/sda3           45773       60802   120719360    5  Extended
/dev/sda5           45773       60802   120718336    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1959    15727616   83  Linux
/dev/sdb2            1959        3133     9435136   82  Linux swap / Solaris
/dev/sdb3            3133        9660    52427776   83  Linux
/dev/sdb4            9660       60802   410793985    5  Extended
/dev/sdb5            9660       35769   209715200    7  HPFS/NTFS
/dev/sdb6           35769       60802   201077760    7  HPFS/NTFS

Disk /dev/sdc: 8220 MB, 8220645888 bytes
255 heads, 63 sectors/track, 999 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x142c182d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1000     8027943    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(998, 254, 63) logical=(999, 111, 21)

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              15G  2.7G   12G  19% /
none                  3.9G  316K  3.9G   1% /dev
none                  3.9G  216K  3.9G   1% /dev/shm
none                  3.9G   88K  3.9G   1% /var/run
none                  3.9G     0  3.9G   0% /var/lock
/dev/sdb3              50G  247M   47G   1% /home
/dev/sdc1             7.7G  7.1G  649M  92% /media/PENDRIVE


Maybe  i did something wrong during installation if so is there a way to  correct this problem that is occurring with out me having to do any  fresh in stall's on both part's. Thank you for taking your time I  appreciate it in advance

---

### Post by oldfred on 2010-11-21
Welcome to the forums. 

Do you have the grub boot loader in the MBR of sda or sdb?

There are known issues with some win7 software that cause issues with grub2 in the MBR. If you have the grub2 on a separate drive (and boot from that drive) it eliminates all those type of issues.

To see the details of your entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by silver boost on 2010-11-21
> **oldfred said:**
> Welcome to the forums. 

Do you have the grub boot loader in the MBR of sda or sdb?

There are known issues with some win7 software that cause issues with grub2 in the MBR. If you have the grub2 on a separate drive (and boot from that drive) it eliminates all those type of issues.

To see the details of your entire configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.


Ok here is the log file you requested I'm not sure where i loaded grub i suspect it was either or. This is my first time loading linux distro. I know that i partitioned the second drive for linux and used the advance option when i loaded the usb stick for install.
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    40,965,749    40,965,687  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     40,966,144   735,334,399   694,368,256   7 HPFS/NTFS
/dev/sda3         735,334,400   976,773,119   241,438,720   5 Extended
/dev/sda5         735,336,448   976,773,119   241,436,672   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    31,457,279    31,455,232  83 Linux
/dev/sdb2          31,457,280    50,327,551    18,870,272  82 Linux swap / Solaris
/dev/sdb3          50,327,552   155,183,103   104,855,552  83 Linux
/dev/sdb4         155,185,150   976,773,119   821,587,970   5 Extended
/dev/sdb5         155,185,152   574,615,551   419,430,400   7 HPFS/NTFS
/dev/sdb6         574,617,600   976,773,119   402,155,520   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8220 MB, 8220645888 bytes
255 heads, 63 sectors/track, 999 cylinders, total 16055949 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    16,055,948    16,055,886   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E5F-3A2B                              vfat       RECOVERY                      
/dev/sda2        1A2D055B298324BF                       ntfs       Hell                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0C2426FE184CD93A                       ntfs       Pictures Games and Stuff      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        562b8613-68ec-41cf-bcb2-c5c8510b2c38   ext4                                     
/dev/sdb2        20eee3bb-8bc7-4919-98f9-55fa40839f5d   swap                                     
/dev/sdb3        add0a003-57f9-4a5c-83d6-ded5047d84af   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        2E7B0E886F52775D                       ntfs       back-up                       
/dev/sdb6        49FEF57A58BF79CC                       ntfs       Heaven                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4CF1-55C4                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="5"
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
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
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sdb1)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=562b8613-68ec-41cf-bcb2-c5c8510b2c38 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sdb1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=562b8613-68ec-41cf-bcb2-c5c8510b2c38 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 562b8613-68ec-41cf-bcb2-c5c8510b2c38
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e5f-3a2b
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 1a2d055b298324bf
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
UUID=562b8613-68ec-41cf-bcb2-c5c8510b2c38 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=add0a003-57f9-4a5c-83d6-ded5047d84af /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=20eee3bb-8bc7-4919-98f9-55fa40839f5d none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.35-22-generic
   2.4GB: boot/vmlinuz-2.6.35-22-generic
    .6GB: initrd.img
   2.4GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Start Linux Mint" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Start Linux Mint (compatibility mode)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed xforcevesa boot=casper noapic noapci nosplash irqpoll --
    initrd    /casper/initrd.lz
}
menuentry "Check the integrity of the CD" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

---

### Post by oldfred on 2010-11-21
Boot script looks normal to me. I do prefer to have the grub2 in the MBR of sdb if booting Linux from sdb, and leave windows booting sda. That makes each hard drive independent in case of one drive's failure. But that would not solve your issue and you do not have to do it.

On my system grub did not see keyboard at all when I installed a new motherboard. I had to go into BIOS and change settings to allow USB keyboards. Windows and Linux did not seem to read the BIOS setting and worked but grub did not until changed.

If you want to install grub2 to sdb. 

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates (not sure if Mint has this or not):
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then change BIOS to boot sdb - the other 500GB drive. If it works then you can install a windows boot loader to sda.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by silver boost on 2010-11-21
> **oldfred said:**
> Boot script looks normal to me. I do prefer to have the grub2 in the MBR of sdb if booting Linux from sdb, and leave windows booting sda. That makes each hard drive independent in case of one drive's failure. But that would not solve your issue and you do not have to do it.

On my system grub did not see keyboard at all when I installed a new motherboard. I had to go into BIOS and change settings to allow USB keyboards. Windows and Linux did not seem to read the BIOS setting and worked but grub did not until changed.

If you want to install grub2 to sdb. 

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates (not sure if Mint has this or not):
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then change BIOS to boot sdb - the other 500GB drive. If it works then you can install a windows boot loader to sda.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR


Let see what i can do :p and thank's i checked bios setting and seems to be normal not sure what is happening with the lockup's on the keyboard it even happens with out the usb connected.

If i would to reinstall grub on sdb would grub still be the bootloader when i turn on my pc? I tried installing grub before on the second hd /root but for some reason it wouldn't boot with out me getting into bios.

---

### Post by oldfred on 2010-11-21
Some old BIOS do not let you choose which drive. As long as you can switch boot drives in BIOS you should be able to boot grub2. I have 2 160GB drives and in BIOS I sometimes just have to change it as I cannot tell which is sda and which is sdb, but I know which boot loader I have in each drive and I have different boot loader in each drive.

---

