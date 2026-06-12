---
title: "Need help recovering Windows"
date: 2011-09-17
forum: General Help
---

### Post by Triblaze on 2011-09-17
I got this laptop around nine months ago, and it came pre-installed with Windows 7 and Windows Vista. I didn't really care much for them, just checked to make sure they worked (they both did), then installed Ubuntu in a dual (triple?) boot. Ubuntu's been working perfectly ever since, but ever since I installed Ubuntu, I can't get into Windows. I have a feeling I might have messed something up while re-partitioning, or something of that nature. Windows 7 and Vista are still on GRUB at the bottom, but when I try to load 7, it says there was an error and I can either boot into safe launch/recovery mode or start normally. Choosing the safe launch tells me that there's an issue with it and I can fix it by inserting the Windows installation disk and selecting repair. However, since this came pre-installed with Windows, I do not have that disk. Choosing to start normally starts to load Windows, the logo starts to fill in like it normally does on seven, then about halfway through it stops and blue screens on me. Uh oh. I believe it said something about the device not working right or something.

I don't really need Windows, but there are some games that I can't get working in Wine, so I figured I'd finally get around to fixing it.

So, what do I need to do? Edit the partitions? Tell grub which device it needs to boot into if it's booting into the wrong one? I'm not sure really what to do.

Oh, but to be clear, all the Windows stuff is still there, it's not like it got wiped. I can access the Windows filesystem through Ubuntu, and everything looks like it's still there and fine, I just can't boot into it.

I can look up any info you need, right now I'm on 10.10, if that helps any, and I installed off a liveCD.

---

### Post by Blasphemist on 2011-09-17
Please install this in ubuntu. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

First, just do the create boot-info summary and post that back here for us to review. That should help to ensure the wrong action isn't taken.

---

### Post by Triblaze on 2011-09-17
Will do, I'll edit in the information here once I have it.

```

               Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   383,801,343   383,391,744  42 SFS
/dev/sda4         383,803,390   622,082,047   238,278,658   5 Extended
/dev/sda5         383,803,392   387,706,879     3,903,488  82 Linux swap / Solaris
/dev/sda6         387,708,928   622,082,047   234,373,120  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        6C3CBB173CBADB72                       ntfs       SYSTEM
/dev/sda3        80E24B98E24B9178                       ntfs       
/dev/sda5        16934d39-8980-4e7b-ace5-0b4980198cf8   swap       
/dev/sda6        61293781-cc7c-4fc7-a880-d10a8210bfc3   ext4       

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6C3CBB173CBADB72
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 80E24B98E24B9178
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
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 189.032711029 = 202.972327936  boot/grub/core.img                             1
 259.982059479 = 279.153610752  boot/grub/grub.cfg                             1
 185.766799927 = 199.465582592  boot/initrd.img-2.6.35-24-generic-pae          2
 187.032455444 = 200.824569856  boot/initrd.img-2.6.35-25-generic-pae          2
 188.295898438 = 202.181181440  boot/initrd.img-2.6.35-27-generic-pae          2
 187.319335938 = 201.132605440  boot/initrd.img-2.6.35-28-generic-pae          2
 194.126247406 = 208.441470976  boot/initrd.img-2.6.35-30-generic-pae          2
 189.006027222 = 202.943676416  boot/vmlinuz-2.6.35-24-generic-pae             1
 189.036834717 = 202.976755712  boot/vmlinuz-2.6.35-25-generic-pae             1
 189.066322327 = 203.008417792  boot/vmlinuz-2.6.35-27-generic-pae             1
 189.082763672 = 203.026071552  boot/vmlinuz-2.6.35-28-generic-pae             1
 189.261043549 = 203.217498112  boot/vmlinuz-2.6.35-30-generic-pae             1
 194.126247406 = 208.441470976  initrd.img                                     2
 187.319335938 = 201.132605440  initrd.img.old                                 2
 189.261043549 = 203.217498112  vmlinuz                                        1
 189.082763672 = 203.026071552  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-09-17__11h52 ****************
boot-repair version : 3-0ppa7~maverick
clean-ubiquity-common version : 3-0ppa6~maverick
internet: connected
boot-repair-common version : 3.0-0ppa7~maverick
LIVESESSION is : no
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
OSPROBER: /dev/sda6:The OS now in use - Ubuntu 10.10 CurrentSession:linux
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Vista (loader):Windows1:chain
BLKID: /dev/sda2: LABEL="SYSTEM" UUID="6C3CBB173CBADB72" TYPE="ntfs"
/dev/sda3: UUID="80E24B98E24B9178" TYPE="ntfs"
/dev/sda5: UUID="16934d39-8980-4e7b-ace5-0b4980198cf8" TYPE="swap"
/dev/sda6: UUID="61293781-cc7c-4fc7-a880-d10a8210bfc3" TYPE="ext4"
sda6 contains The OS now in use - Ubuntu 10.10 (linux)
sda2 contains Windows 7 (windows)
sda3 contains Windows Vista (windows)
1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 3 OS detected on sda disk.
sda contains minimum one OS
FDISK
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82337274

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   383801343   191695872   42  SFS
/dev/sda4       383803390   622082047   119139329    5  Extended
/dev/sda5       383803392   387706879     1951744   82  Linux swap / Solaris
/dev/sda6       387708928   622082047   117186560   83  Linux

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82337274

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   383801343   191695872   42  SFS
/dev/sda4       383803390   622082047   119139329    5  Extended
/dev/sda5       383803392   387706879     1951744   82  Linux swap / Solaris
/dev/sda6       387708928   622082047   117186560   83  Linux
sda6 : sda, not-sepboot, grub, aptget, 32, with boot, , with-os, no-gpt, fstab-without-efi.
sda2 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda2, with-os, no-gpt, no-fstab.
sda3 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda3, with-os, no-gpt, no-fstab.
PARTED: Model: ATA SAMSUNG HM321HI (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  1049kB  1016kB  primary
2      1049kB  210MB   209MB   primary   ntfs            boot
3      210MB   197GB   196GB   primary   ntfs
4      197GB   319GB   122GB   extended
5      197GB   199GB   1999MB  logical   linux-swap(v1)
6      199GB   319GB   120GB   logical   ext4
MOUNT /dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cd)
/dev/sda2 on /mnt/clean/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/clean/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  ati autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fd full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill root rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 v4l vga_arbiter video0 zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext4    111G   37G   68G  36% /
none      devtmpfs    1.9G  300K  1.9G   1% /dev
none         tmpfs    1.9G  128K  1.9G   1% /dev/shm
none         tmpfs    1.9G  224K  1.9G   1% /var/run
none         tmpfs    1.9G     0  1.9G   0% /var/lock
/dev/sda2  fuseblk    199M   29M  171M  15% /mnt/clean/sda2
/dev/sda3  fuseblk    183G   34G  150G  19% /mnt/clean/sda3
FDISK
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82337274

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   383801343   191695872   42  SFS
/dev/sda4       383803390   622082047   119139329    5  Extended
/dev/sda5       383803392   387706879     1951744   82  Linux swap / Solaris
/dev/sda6       387708928   622082047   117186560   83  Linux
Logs saved into /var/log/clean/log/2011-09-17__11h52boot-repair45
Logs saved into /mnt/clean/sda2/clean/log/2011-09-17__11h52boot-repair45
Logs saved into /mnt/clean/sda3/clean/log/2011-09-17__11h52boot-repair45
combobox_ostoboot_bydefault_fillin
combobox_efi_fillin sda6
combobox_separateboot_fillin
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
************************Before mainwindow appear
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda6)
FSCK_ACTION yes PASTEBIN_ACTION no
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 1 (sda6) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no () grub-pc ()
RETOURCOMBO_purge_grub : sda6 (The OS now in use - Ubuntu 10.10)
/usr/share/clean/bootrepair-gui.sh: line 214: 16285 Terminated              while true; do
done
RETOURCOMBO_ostoboot_bydefault : sda6 (The OS now in use - Ubuntu 10.10)
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
internet: connected
************************Before Repairing
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda6)
FSCK_ACTION no PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION nombraction UNHIDEBOOT_ACTION no (10.s)
PART_TO_REINSTALL_GRUB 1 (sda6) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no () grub-pc ()
Freed space function
/dev/sda6            115345960  38661032  70825600  36% /
/dev/sda2               203772     29104    174668  15% /mnt/clean/sda2
/dev/sda3            191695868  34607308 157088560  19% /mnt/clean/sda3
internet: connected
dpkg-preconfigure: unable to re-open stdin:
```
Ok, it said "boot successfully repaired" after it created this, not sure if that means what I think it means, as it seems to have just checked stuff.
*Yeah, just checked, still not working.

---

### Post by Blasphemist on 2011-09-17
It looks to me like the win 7 partition is too small to be a working installation. Have you tried to run vista from grub? It looks like that should work.

I'd try running vista first and see if that works. If the math I did in my head is right, it looks like the win 7 partition is about 1GB. That partition is also missing the /Windows/System32/winload.exe file. I also have a small windows partition but it is recognized by boot-repair as a recovery environment while yours isn't. I don't know if the 1GB is even big enough to be a copy of the install disks.

Are you sure booting the sda2 windows partition ever worked? I also see the windows partitions recognized as partition type 42 SFS which is an encrypted file system type for DOS on 386 pc's as best I know. Please let us know if vista will boot and if not what happens. It may be that it's just that sda2 won't boot and I don't want us to take more action than needed.

---

### Post by Triblaze on 2011-09-17
Just checked, Vista didn't work. Unlike 7 though, instead of giving me a start normally or start in safe mode option, it just said that it failed to boot, and asked for the installation disk like 7 does in its recovery mode, and I believe it said the problem was that a device was inaccessible.

Come to think of it, I don't really remember 7 working. I mean, I know that I didn't find any errors before installing Ubuntu, and I know I checked Windows, but I'm not sure I checked 7. I'm pretty sure I did, but I can't specifically remember it, so I can't say for sure. As for the partition being too small, maybe I messed that up while repartitioning for Ubuntu, but Vista still isn't working...hmm.

---

### Post by Blasphemist on 2011-09-17
Can you describe what partitioning you did in preparation for adding ubuntu? Maybe that will help for us to figure this out. I looked over the output from boot-repair again and I don't think it will harm anything to let it try and do it's recommended repair. I also don't know that I think it will fix it. 

There are others in forums right now that are very good with this kind of thing and maybe one of them will have ideas.

---

### Post by Triblaze on 2011-09-17
To be honest, I can't really remember, it was nine months ago, but I believe I had trouble using Ubuntu's partition editor and had to instead edit them from within Windows. I believe I used Vista for doing this...
I forget whether this worked or if I went back and figured it out in Ubuntu.

I can post the partition information, but I take it it's explained in the boot information?

---

### Post by Blasphemist on 2011-09-17
Yes the partition information is already in what you posted. There looks to me some disagreement in the script results about file system types and I can't explain that but don't know if it is the issue or not. I pinged another person to take a look and maybe he'll have a new insight. When I ran boot-repair on my own system as part of this, I also just chose to just create the results and it did tell me it had successfully repaired the system when I don't believe it made any changes. Did you try letting it do its recommended changes yet? If yes, do post the new script results.

---

### Post by oldfred on 2011-09-17
I believe you used Windows to create partitions. Windows has a nasty habit of converting from 'basic' to dynamic which fdisk shows as SFS partitions. Dynamic are like LVM is in Linux as there does not have to be a one to one match of physical partitions to logical. If the partitions are still one to one you may be able to convert back. 

I have seen where not all of Windows repair tools seem to work (or they need different directions which I do not know) for dynamic partitions. 

If you use any of these suggestions be sure to back up the Windows install or all your data before trying these.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Triblaze on 2011-09-17
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for (,msdos6)/boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   383,801,343   383,391,744  42 SFS
/dev/sda4         383,803,390   622,082,047   238,278,658   5 Extended
/dev/sda5         383,803,392   387,706,879     3,903,488  82 Linux swap / Solaris
/dev/sda6         387,708,928   622,082,047   234,373,120  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        6C3CBB173CBADB72                       ntfs       SYSTEM
/dev/sda3        80E24B98E24B9178                       ntfs       
/dev/sda5        16934d39-8980-4e7b-ace5-0b4980198cf8   swap       
/dev/sda6        61293781-cc7c-4fc7-a880-d10a8210bfc3   ext4       

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro  vga=775 quiet  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=61293781-cc7c-4fc7-a880-d10a8210bfc3 ro single  vga=775 quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 61293781-cc7c-4fc7-a880-d10a8210bfc3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6C3CBB173CBADB72
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 80E24B98E24B9178
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
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 189.032711029 = 202.972327936  boot/grub/core.img                             1
 244.999053955 = 263.065731072  boot/grub/grub.cfg                             1
 185.766799927 = 199.465582592  boot/initrd.img-2.6.35-24-generic-pae          2
 187.032455444 = 200.824569856  boot/initrd.img-2.6.35-25-generic-pae          2
 188.295898438 = 202.181181440  boot/initrd.img-2.6.35-27-generic-pae          2
 187.319335938 = 201.132605440  boot/initrd.img-2.6.35-28-generic-pae          2
 194.126247406 = 208.441470976  boot/initrd.img-2.6.35-30-generic-pae          2
 189.006027222 = 202.943676416  boot/vmlinuz-2.6.35-24-generic-pae             1
 189.036834717 = 202.976755712  boot/vmlinuz-2.6.35-25-generic-pae             1
 189.066322327 = 203.008417792  boot/vmlinuz-2.6.35-27-generic-pae             1
 189.082763672 = 203.026071552  boot/vmlinuz-2.6.35-28-generic-pae             1
 189.261043549 = 203.217498112  boot/vmlinuz-2.6.35-30-generic-pae             1
 194.126247406 = 208.441470976  initrd.img                                     2
 187.319335938 = 201.132605440  initrd.img.old                                 2
 189.261043549 = 203.217498112  vmlinuz                                        1
 189.082763672 = 203.026071552  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-09-17__14h04 ****************
boot-repair version : 3-0ppa7~maverick
clean-ubiquity-common version : 3-0ppa6~maverick
internet: connected
boot-repair-common version : 3.0-0ppa7~maverick
LIVESESSION is : no
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
OSPROBER: /dev/sda6:The OS now in use - Ubuntu 10.10 CurrentSession:linux
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sda3:Windows Vista (loader):Windows1:chain
BLKID: /dev/sda2: LABEL="SYSTEM" UUID="6C3CBB173CBADB72" TYPE="ntfs"
/dev/sda3: UUID="80E24B98E24B9178" TYPE="ntfs"
/dev/sda5: UUID="16934d39-8980-4e7b-ace5-0b4980198cf8" TYPE="swap"
/dev/sda6: UUID="61293781-cc7c-4fc7-a880-d10a8210bfc3" TYPE="ext4"
sda6 contains The OS now in use - Ubuntu 10.10 (linux)
sda2 contains Windows 7 (windows)
sda3 contains Windows Vista (windows)
1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.
Total of 3 OS detected on sda disk.
sda contains minimum one OS
FDISK
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82337274

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   383801343   191695872   42  SFS
/dev/sda4       383803390   622082047   119139329    5  Extended
/dev/sda5       383803392   387706879     1951744   82  Linux swap / Solaris
/dev/sda6       387708928   622082047   117186560   83  Linux

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82337274

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   383801343   191695872   42  SFS
/dev/sda4       383803390   622082047   119139329    5  Extended
/dev/sda5       383803392   387706879     1951744   82  Linux swap / Solaris
/dev/sda6       387708928   622082047   117186560   83  Linux
sda6 : sda, not-sepboot, grub, aptget, 32, with boot, , with-os, no-gpt, fstab-without-efi.
sda2 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda2, with-os, no-gpt, no-fstab.
sda3 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda3, with-os, no-gpt, no-fstab.
PARTED: Model: ATA SAMSUNG HM321HI (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  1049kB  1016kB  primary
2      1049kB  210MB   209MB   primary   ntfs            boot
3      210MB   197GB   196GB   primary   ntfs
4      197GB   319GB   122GB   extended
5      197GB   199GB   1999MB  logical   linux-swap(v1)
6      199GB   319GB   120GB   logical   ext4
MOUNT /dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cd)
/dev/sda2 on /mnt/clean/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/clean/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  ati autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fd full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill root rtc rtc0 scd0 sda sda1 sda2 sda3 sda4 sda5 sda6 sdb sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 v4l vga_arbiter video0 zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext4    111G   28G   77G  27% /
none      devtmpfs    1.9G  300K  1.9G   1% /dev
none         tmpfs    1.9G  128K  1.9G   1% /dev/shm
none         tmpfs    1.9G  220K  1.9G   1% /var/run
none         tmpfs    1.9G     0  1.9G   0% /var/lock
/dev/sda2  fuseblk    199M   29M  171M  15% /mnt/clean/sda2
/dev/sda3  fuseblk    183G   34G  150G  19% /mnt/clean/sda3
FDISK
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x82337274

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3          409600   383801343   191695872   42  SFS
/dev/sda4       383803390   622082047   119139329    5  Extended
/dev/sda5       383803392   387706879     1951744   82  Linux swap / Solaris
/dev/sda6       387708928   622082047   117186560   83  Linux
Logs saved into /var/log/clean/log/2011-09-17__14h04boot-repair41
Logs saved into /mnt/clean/sda2/clean/log/2011-09-17__14h04boot-repair41
Logs saved into /mnt/clean/sda3/clean/log/2011-09-17__14h04boot-repair41
combobox_ostoboot_bydefault_fillin
combobox_efi_fillin sda6
combobox_separateboot_fillin
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
************************Before mainwindow appear
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda6)
FSCK_ACTION yes PASTEBIN_ACTION no
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 1 (sda6) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no () grub-pc ()
/usr/share/clean/bootrepair.sh: line 56:  5553 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sda6 (The OS now in use - Ubuntu 10.10)
RETOURCOMBO_ostoboot_bydefault : sda6 (The OS now in use - Ubuntu 10.10)
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda6
efi_show_hide 1 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
internet: connected
************************Before Repairing
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda6)
FSCK_ACTION yes PASTEBIN_ACTION no
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 1 (sda6) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no () grub-pc ()
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda3
Freed space function
/dev/sda6            115345960  28838328  80648304  27% /
/dev/sda2               203772     29320    174452  15% /mnt/clean/sda2
/dev/sda3            191695868  34607524 157088344  19% /mnt/clean/sda3
Reinstall the GRUB of sda6 into the MBR of sda
Unmount (force) all OS partitions except / and partition where we reinstall GRUB (sda6)
dpkg_function
grub-install (GRUB) 1.98+20100804-5ubuntu3.3
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-30-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-27-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3
done
Mount all the partitions for the logs
Unhide boot menu (10 seconds) if Wubi detected
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg
internet: connected

```
That's what it gave me after I selected "repair boot". I'll test it now.


Oh, late, didn't see the new post, will read.

---

### Post by Blasphemist on 2011-09-17
Do let us know if anything has changed Triblaze.

Thanks for jumping in oldfred. I'll work on learning more on these dang dynamic partitions.

---

### Post by Triblaze on 2011-09-17
Ok, I know almost nothing about partitions and dynamic drives and stuff, before I jump in, do you mind explaining it simply and straightforward? I assume I can download partition wizard 4.2 for Ubuntu (it wasn't on the software center, but I'll check online next obviously), then I assume it'll open up and let me edit partitions, and there will be some button that says "convert from dynamic to basic", or something like that. That it? I'm hoping it's that simple, I don't want to jump into this and realize it'll take more knowledge/work than I can understand.

Apparently Partition Wizard is only for Windows, and seeing as I can't boot into Windows, I think I need a Ubuntu partitioner that can convert dynamic to basic.

---

### Post by srs5694 on 2011-09-17
> **Triblaze said:**
> Ok, I know almost nothing about partitions and dynamic drives and stuff, before I jump in, do you mind explaining it simply and straightforward? I assume I can download partition wizard 4.2 for Ubuntu (it wasn't on the software center, but I'll check online next obviously), then I assume it'll open up and let me edit partitions, and there will be some button that says "convert from dynamic to basic", or something like that. That it? I'm hoping it's that simple, I don't want to jump into this and realize it'll take more knowledge/work than I can understand.

[Partition Wizard](http://www.partitionwizard.com/) is a Windows program, not a Linux program, so you'll need to be able to boot Windows to use it. Unless I've missed something, you can't currently boot Windows, so that creates a bit of a chicken-and-egg problem.

If you've got files you want to recover, it looks like you may be able to get at them by mounting /dev/sda2 and/or /dev/sda3 -- but be very careful and don't write to the partitions; Windows' dynamic disks might not work the way the simple /dev/sda2 and /dev/sda3 partition assignments assume. If there are deviations, the filesystems will appear to be damaged to Linux, which will make some (perhaps even all) of the files inaccessible, and writing to the filesystem will damage it from Windows' perspective.

Beyond that, the simplest approach to getting Windows to boot is probably to re-install it; however, you should exercise extreme caution, especially if you delete /dev/sda1, /dev/sda2, and /dev/sda3, since the Windows installer is known to delete logical partitions in some cases if there are empty primary partition slots available. Thus, you might want to use Linux's fdisk to change those partitions' type codes to 0x07 (NTFS), use mkntfs to create new NTFS filesystems on them, and then re-install Windows. Before you do any of this, though, back up your important Linux data to an external medium, just in case the Windows installation goes badly south. Also, type "sudo sfdisk -d /dev/sda > parts.txt" and save the resulting parts.txt file on an external medium. This is a backup of your partition table, so you'll be able to easily restore it in case the partition table is damaged.

You mentioned that you didn't have any installation media from your computer's vendor. There are several ways to get around this problem:


[list]
[*]Contact the computer manufacturer to get media. Be aware, however, that they may ship you restore media, which restores the disk to its original from-the-factory state, rather than an installation disc, which you can use to install normally. Restore discs will wipe out your Linux installation. The manufacturer may also charge you money for whatever they send you.
[*][This  site](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/) offers what is described as Microsoft-approved downloads of  Windows 7 installation discs. Note that you'll need a valid license  number (probably printed on a sticker on your computer) for this to be  legal. Be sure to download the version your computer originally used;  your license won't be good for the other versions.
[*]You can buy a copy in a retail store. That'll set you back a lot of money, though. It might not be unreasonable if you wanted to upgrade, though.
[*]You can try the [Windows 8 Developer Preview](http://msdn.microsoft.com/en-us/windows/apps/br229516) instead of Windows 7. This is a free download from Microsoft, but it's alpha-quality software, so IMHO it's only worth trying for occasional non-critical use. I've not yet done much with it, but so far it's been unreliable for me, and the new user interface is the worst idea Microsoft has had in at least a decade, IMHO.
[/list]

---

### Post by oldfred on 2011-09-17
Partition Magic has a bootable version on the linked page. That still is the best choice I think. But the real issue is how Windows converts with only a simple warning that most users do not understand.

Some have used Linux tools to convert, I think those are more risky as they just convert back. Windows does require NTFS signatures in the partitions, so if partition is not at  correct start or end then it can have big issues.

Users have done this:
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

Another windows tool:
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

---

### Post by Blasphemist on 2011-09-17
Here's a guy that blogged about using Testdisk that is available in the software center to convert. [http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)
This includes screenshots of doing it.

---

### Post by srs5694 on 2011-09-17
I've heard of TestDisk working for this; however, my concern is that, as I understand it, LDM/dynamic disks support non-contiguous filesystems, similar to Linux's LVM. If the filesystems have been rendered non-contiguous, TestDisk won't be able to recover the filesystems into standard partitions. I have no idea of how to check for this condition, so I can't provide advice on how to do it safely.

If the bootable Partition Wizard does the job, then it's probably the safest way to recover the existing Windows system. If not, then I suppose trying with TestDisk, or just changing the type codes on the existing partitions and running the Windows recovery tools, may be worth a try. In a worst-case scenario, it'll just trash the partitions. This would make re-installation necessary, but that would be the next option anyhow.

---

### Post by Triblaze on 2011-09-17
Sorry I was gone, back now, reading the proposed solutions, I think using partition wizard will be my best bet. I'll test that out now.


Oldfred, you said it's in the link, but there are a lot of links and there were several versions of partition wizard, do you mind providing the exact link to the download that'd work best for me on Ubuntu?

And once I have that, which partition do I use it on? The 196GB NTFS one, I assume? Do I have to use it on any other ones that contain information for windows?

---

### Post by Triblaze on 2011-09-17
Bump, still not sure exactly which one or version that I can boot on Ubuntu. And when you say it's bootable, do you mean I can download and boot it, or will it just boot automatically or something?

And still just wondering which I'd need to convert, just sda2 and sda3?

---

### Post by oldfred on 2011-09-18
I just scrolled down on the downloads page and it said they had a bootable verison. It is not for Ubuntu, but is a liveCD of its own. Not sure what it boots with.

[B][SIZE=1]Free Download Bootable CD Now![/SIZE]
[/B]

[http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html)

---

### Post by Triblaze on 2011-09-18
Okay, got the iso and I'm gonna burn it to a cd now, I'll post the results of it.

And just checking again, which partitions? Everything in dynamic form?

---

### Post by Triblaze on 2011-09-18
Ok, I got the disc burned and everything, but I don't know how to boot  it. It doesn't seem to do anything in Ubuntu, I can't make it run, I can  just look at what's in it, there are some odd files, but nothing that  looks like a run prompt. When I start the computer, I don't believe  there's any option to start up whatever's on the disk.

It's for Windows, but seeing as I can't get into windows...what do?

---

### Post by Blasphemist on 2011-09-18
I believe you downloaded an iso file and burned it to cd, right?

If so, reboot and go into the bios. You'll see a prompt quickly after the system starts to come up telling you to press an F key to access bios. You can access a menu in bios that will allow you to select what device should be first in the boot preference order. Set that to the cd. You might also see a prompt for a boot menu when the system first starts to come up. That lets you select a specific device such as the cd to boot from just for that boot episode. On my laptop the boot menu is F12.

---

### Post by Triblaze on 2011-09-18
Okay, I got it working and can get into partition wizard and I see everything, the partition for windows is there and seems healthy, just booting it won't work, but now...what do I do to fix it?

You guys talked about dynamic disks or something and I need to convert it back. I didn't really see anything talking about dynamic stuff except one tab saying something about dynamic, but all the stuff in it was greyed out and didn't seem to apply to any of the partitions I had. The Windows partitions are "Primary", and the Ubuntu ones are "Logical", do I need to change the windows partitions to logical? There was an option for that.


I feel so close, yet so far away. Thanks to all for your patience. Just right now I don't know what I need to do to fix it, so I'm kinda stuck.


Just backing up, I have the partitions and all the files but can't boot into it. So I need to convert the partitions to something bootable, right? Or do I need to fix the devices, like sda2?

---

### Post by Blasphemist on 2011-09-18
I've never needed to do what you are needing to do but I looked at their site for instruction on doing this. [http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)

Does this page or the video at the bottom of it help?

---

### Post by oldfred on 2011-09-18
Windows has to be a primary partition, formated NTFS and the bootable copy of Windows has to have the boot flag. Do not change any of that. 

Not sure how others used the software to convert.

---

### Post by Triblaze on 2011-09-18
Okay, I think I may have found something related to the problem. on each of the ntfs partitions, I could choose the options "set as windows boot", or something like that. I assume that means they aren't currently set as the boot. However, choosing this option for both them returns an error: "could not detect windows directory" or "no windows directory", or something of that nature.

Trying to boot into them tells me a device is inaccessible.


So...I have a problem with sda2 or sda3, or my windows directory is not there? Don't know what to make of the information.

Is grub just not calling up the right thing?

---

### Post by Blasphemist on 2011-09-18
Hold up there a minute cowboy! I thought you had determined the files are in your windows partitions. What happened to the trying to convert the partitions?

---

### Post by Triblaze on 2011-09-18
> **Blasphemist said:**
> Hold up there a minute cowboy! I thought you had determined the files are in your windows partitions. What happened to the trying to convert the partitions?

That's just it, I don't know what I'm trying to convert them to! They're not dynamic, they're set to primary as they should be, but it seems they aren't set as bootable.

Or do you think I'm trying to recover my files? I have nothing on there. I just want to get windows working again so I can game on it, and so it's there in case I ever need it.


When I say files, I mean the windows filesystem and all the os stuff is there. I haven't added any of my personal stuff.

---

### Post by Blasphemist on 2011-09-18
If the disc is not dynamic it is basic, not primary. Basic disk partitions are primary, extended (also primary) or logical. So partition wizard shows nothing as dynamic? It give you no option as shown on the link I included to convert the disk? Please answer that as I go back to what the other guys have said in the event these partitions aren't dynamic.

---

### Post by Triblaze on 2011-09-18
> **Blasphemist said:**
> If the disc is not dynamic it is basic, not primary. Basic disk partitions are primary, extended (also primary) or logical. So partition wizard shows nothing as dynamic? It give you no option as shown on the link I included to convert the disk? Please answer that as I go back to what the other guys have said in the event these partitions aren't dynamic.
It says the disk (and thus everything in it, I assume), is basic.

The windows partitions are primary, the linux partitions are logical.

---

### Post by Blasphemist on 2011-09-18
I've now done a lot of looking and reading on this and I'm still not sure I've found anything that helps. Do look at this.
> 42 Windows 2000 dynamic extended partition marker
If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM). As the Microsoft KnowledgeBase writes: Pure dynamic disks (those not containing any hard-linked partitions) have only a single partition table entry (type 42) to define the entire disk. Dynamic disks store their volume configuration in a database located in a 1-MB private region at the end of each dynamic disk.
If I understand this right, and I'm not sure at all of that, the installation of linux may have caused the dynamic disks volume configuration to be lost or changed. It would seem this could come from using a proprietary partition table and ignoring the legacy partition table.

Do I understand correctly though that you can from ubuntu see the windows partitions and the files/directories on them? Can you see and successfully copy files from those drives for instance? Don't try to write to them. If you can, then I'd think that linux is using the normal "legacy" partition table to do that. Am I right that you have access to those files but just can't boot either windows?

---

### Post by Triblaze on 2011-09-18
> **Blasphemist said:**
> I've now done a lot of looking and reading on this and I'm still not sure I've found anything that helps. Do look at this.

If I understand this right, and I'm not sure at all of that, the installation of linux may have caused the dynamic disks volume configuration to be lost or changed. It would seem this could come from using a proprietary partition table and ignoring the legacy partition table.

Do I understand correctly though that you can from ubuntu see the windows partitions and the files/directories on them? Can you see and successfully copy files from those drives for instance? Don't try to write to them. If you can, then I'd think that linux is using the normal "legacy" partition table to do that. Am I right that you have access to those files but just can't boot either windows?
I can see the files, and I can copy them into the Ubuntu partition.

And I really didn't get what you quoted much, but I believe the main windows partition is 0x42. And there is a second ntfs part called "system", which I believe is about 1MB in size, like it said.

But Partition Wizard seems to say they're not dynamic. I'm not sure what to make of it all.

*Edit: Correction/more info: There is a ntfs partition that's 198 gb, this is the main one, with all the windows stuff in it. Disk Utility says it has a bootable flag. Partition manager says it is "active". This is on sda3. It is 0x42.
The System partition is actually 209 MB, also 0x42, not marked as bootable or active, and is on sda2.
Then, there is a 1MB partition on sda1; 0x42. This doesn't seem to have any labels on it, it doesn't say its usage, it doesn't say ntfs or anything else like that, no flags, and it's called "unknown". Maybe this is the "inaccessible device" that windows refers to when it says it can't boot? I don't really know.

Hmm, this unknown partition also doesn't seem mountable, I can't find it, and disk utility doesn't display the usual "mount point" part in the information on it. I can set it to bootable. Would that help?

---

### Post by oldfred on 2011-09-18
0x42 is the dynamic partition type.

[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)
> **42  Windows 2000 dynamic extended partition marker** If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM). As the Microsoft KnowledgeBase writes: *Pure dynamic disks (those not containing any hard-linked partitions) have only a single partition table entry (type **42**) to define the entire disk. Dynamic disks store their volume configuration in a database located in a 1-MB private region at the end of each dynamic disk.*
  

---

### Post by Blasphemist on 2011-09-18
> I can see the files, and I can copy them into the Ubuntu partition.

And I really didn't get what you quoted much, but I believe the main windows partition is 0x42. And there is a second ntfs part called "system", which I believe is about 1MB in size, like it said.

But Partition Wizard seems to say they're not dynamic. I'm not sure what to make of it all.
f
Well at least you can get to the files.
> *Edit: Correction/more info: There is a ntfs partition that's 198 gb, this is the main one, with all the windows stuff in it. Disk Utility says it has a bootable flag. Partition manager says it is "active". This is on sda3. It is 0x42.

This partition doesn't show as ntfs in the boot info script. This does have at least some of the files needed to boot. The boot info script says that is the vista partition. Is that right? I don't have vista but I think you could google to find exactly what files vista needs to boot. In the end you may have to try using GParted to just change the partition to ntfs and hope nothing gets lost.
> The System partition is actually 209 MB, also 0x42, not marked as bootable or active, and is on sda2.
Grubs OS prober thinks this is Win 7 for some reason but it is too small for that. There are at least some boot manager files on this partition but there may not be much to gain from salvaging this partition. But that assumes that what we see is real and with the dynamic confusion I'm not sure that it is.
> Then, there is a 1MB partition on sda1; 0x42. This doesn't seem to have any labels on it, it doesn't say its usage, it doesn't say ntfs or anything else like that, no flags, and it's called "unknown". Maybe this is the "inaccessible device" that windows refers to when it says it can't boot? I don't really know.

Hmm, this unknown partition also doesn't seem mountable, I can't find it, and disk utility doesn't display the usual "mount point" part in the information on it. I can set it to bootable. Would that help?
I think this one is the least of your concerns but it is unusual. I wouldn't do anything with it.

Summary, it looks like Vista is the only thing potentially salvageable. I don't know how to tell you to salvage it as I can't explain the file system type. If I were you and the partition was win 7 I think I'd keep trying. But for vista I'm not at all sure that I would. Maybe someone else will see this that it will make sense to. I wish I could be of more help.

---

### Post by Triblaze on 2011-09-18
> **oldfred said:**
> 0x42 is the dynamic partition type.

[http://www.win.tue.nl/~aeb/partitions/partition_types-1.html]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types-1.html")

Oooooh.

That would explain it. So I just need to change that? I can do that. But change it to what?

0x07 for Windows ntfs?

And on both partitions, even if the system one apparently might not be salvagable?


Sorry for being so slow, but seeing as a partition change got me into this mess, I don't want to make an incorrect change and drive myself into a further mess.

Oh, and I should be able to just change the partition size after it's in basic, right? Sorry, don't know too much about partitions, just want to know if I should wait until after I get it working to change the size, because I wouldn't mind getting a few more GBs in my Ubuntu partition.

---

### Post by Blasphemist on 2011-09-18
> **Triblaze said:**
> Oooooh.

That would explain it. So I just need to change that? I can do that. But change it to what?

0x07 for Windows ntfs?

And on both partitions, even if the system one apparently might not be salvagable?


Sorry for being so slow, but seeing as a partition change got me into this mess, I don't want to make an incorrect change and drive myself into a further mess.

Oh, and I should be able to just change the partition size after it's in basic, right? Sorry, don't know too much about partitions, just want to know if I should wait until after I get it working to change the size, because I wouldn't mind getting a few more GBs in my Ubuntu partition.
I can't say what will happen when you change the partition type but yes you would change it to 07. And you are also right, wait until it is and has been working before changing the size.

---

### Post by Triblaze on 2011-09-18
Ok, I tried to just do it in Disk Utility because that was quicker, and I set it to 0x07.

It chugged away at 90% CPU usage for a while, and then gave me an error saying it couldn't convert it. However, disk utility still seems to be doing something and it still has the little loading symbol. Right now it's around 15% CPU usage.

I figure I should try again on Partition Wizard, but I don't want to halt Disk Utility if it's in the middle of something. Would I be able to halt it safely? It's been like this for a while now.

---

### Post by Blasphemist on 2011-09-18
Given the situation, I'd give it as long as you can. It may be undoing what it had done.

---

### Post by Triblaze on 2011-09-18
Posting from Windows 7, just installed Steam!:p


I made it quit, fortunately nothing bad happened, then used partition manager, changed them to 0x07, and fired up windows. Haven't checked Vista yet, but 7 is working!

Thanks to you all for being so patient.

I've never used 7 really, my mom has vista and my school uses xp. I'd say 7 is definitely looking better than both, but I still prefer Ubuntu. I just need Windows for gaming. Got some of them working in Wine, but some just wouldn't work.


Uh, where in the edit post window do I change it to "solved"?
*Found it.

---

### Post by oldfred on 2011-09-18
Glad that worked.

I think it only works where partitions have not really been modified to be logically different than the physical partitions as suggested by some others also. If the logical overlapped a physical then just converting it back could lead to major corruption.

---

