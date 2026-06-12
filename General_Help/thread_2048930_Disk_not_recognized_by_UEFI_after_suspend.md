---
title: "Disk not recognized by UEFI after suspend"
date: 2012-08-27
forum: General Help
---

### Post by jtwigg00 on 2012-08-27
Hello,

I currently can't boot into Ubuntu after a failed restore from suspend. After restoring the left-hand monitor just showed my wallpaper, and the right-hand was black (though the display was on). Entering my password did not work. I tried dropping to a terminal but if I typed anything it would give an I/O error, so I did a hard reset.

The disk with Ubuntu on it is not available in the UEFI boot menu. The setup utility says that that SATA port is empty (it's not). My other disks are still detected correctly and the PC boots into Windows when powered on.

I've installed SeaTools on windows to try and diagnose the disk but it's not discovered by that tool either.

I'm using Ubuntu 12.04. Help?

Thanks for reading.

---

### Post by oldfred on 2012-08-27
Welcome to the forums.

Windows does not see Linux formated partitions. Does BIOS see drive?

From Ubuntu liveCD install this or download its full bootable liveCD. Run the BootInfo report and post link it makes.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by drmrgd on 2012-08-27
> **jtwigg00 said:**
> Hello,

I currently can't boot into Ubuntu after a failed restore from suspend. After restoring the left-hand monitor just showed my wallpaper, and the right-hand was black (though the display was on). Entering my password did not work. I tried dropping to a terminal but if I typed anything it would give an I/O error, so I did a hard reset.

The disk with Ubuntu on it is not available in the UEFI boot menu. The setup utility says that that SATA port is empty (it's not). My other disks are still detected correctly and the PC boots into Windows when powered on.

I've installed SeaTools on windows to try and diagnose the disk but it's not discovered by that tool either.

I'm using Ubuntu 12.04. Help?

Thanks for reading.

I might also ask what motherboard you have, and if you tried to do a full power off (maybe even unplug?) and power on, or just a system reset?

---

### Post by jtwigg00 on 2012-08-27
drmrgd,

My motherboard is an Asus "P8Z77-V LX". If necessary I can boot into the uefi setup to get the firmware version or other info.

I have done a complete power off. I flipped the switch on the power supply and waited for all the LEDs on the motherboard to go out before restarting. I confirmed that the power and SATA cables are connected to the disk.

oldfred,

I have three disks: ext4 (Ubuntu), ext4 (no OS/storage), and NTFS (Windows 7). SeaTools can detect the storage disk, but not the one with Ubuntu on it. The UEFI/BIOS does not see the drive, it says that nothing is connected to the sata port.

I will try to run boot-repair and report back with the results.

---

### Post by jtwigg00 on 2012-08-27
Below is the result of the bootinfo script. It also failed to detect my Ubuntu disk.
sda: USB flash drive, the "liveUSB" I'm currently booted from.
sdb: NTFS, win7
sdc: ext3 storage

I said the storage was ext4 but I must have remembered incorrectly. I'm pretty sure the disk with "/" on it is ext4 though.

While booting the live session I got the following error three times:
ata3: COMRESET failed (errno: -16)

Thanks for your help.

[QUOTE=bootinfo]   Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........`.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 779976 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /menu.lst /boot.ini /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /grldr.mbr

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             32     3,932,159     3,932,128   6 FAT16


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   625,139,711   625,137,664   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   488,392,064   488,392,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4563-A2CC                              vfat       
/dev/sdb1        C010C6BF10C6BBA2                       ntfs       
/dev/sdc1        cfa67a05-e20e-4401-af51-2aa115cf38d3   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /live/image              vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)


============================== sda1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit boot=live config   quiet 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label 32bits session 
kernel /live/vmlinuz 
append initrd=/live/initrd.img boot=live config   quiet 
 
label ubnentry2 
menu label 64bits session 
kernel /live/vmlinuz2 
append initrd=/live/initrd2.img boot=live config   quiet 
 
label ubnentry3 
menu label 32bits session (failsafe) 
kernel /live/vmlinuz 
append initrd=/live/initrd.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal 
 
label ubnentry4 
menu label 64bits session (failsafe) 
kernel /live/vmlinuz2 
append initrd=/live/initrd2.img boot=live config   noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal 
 
label ubnentry5 
menu label Memory test 
kernel /live/memtest 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

================================ sdb1/menu.lst: ================================

--------------------------------------------------------------------------------
timeout 7 
default 0 
title grub2 
find --set-root /boot/grub/core.img 
kernel /boot/grub/core.img 
boot--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=c:\grldr.mbr 
[operating systems] 
C:\grldr.mbr="Grub4Dos"--------------------------------------------------------------------------------

========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1

title find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst
    errorcheck off
    configfile /menu.lst
    configfile /boot/grub/menu.lst
    configfile /grub/menu.lst
    find --set-root --ignore-floppies --ignore-cd /menu.lst && configfile /menu.lst
    find --set-root --ignore-floppies --ignore-cd /boot/grub/menu.lst && configfile /boot/grub/menu.lst
    find --set-root --ignore-floppies --ignore-cd /grub/menu.lst && configfile /grub/menu.lst
    errorcheck on
    commandline

title commandline
    commandline

title reboot
    reboot

title halt
    halt


--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       0

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[61441]) leaked on lvscan invocation. Parent PID 10145: bash
File descriptor 8 (pipe:[61441]) leaked on lvscan invocation. Parent PID 10145: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-08-27__11h59 ===================
boot-repair version : 3.18-0ppa49~lucid
boot-sav version : 3.192-0ppa11~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
boot-repair updated
File descriptor 7 (pipe:[61441]) leaked on lvs invocation. Parent PID 5597: /bin/sh
File descriptor 8 (pipe:[61441]) leaked on lvs invocation. Parent PID 5597: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 02.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sdb1:Windows 7 (loader):Windows:chain

=================== blkid:
/dev/sdb1: UUID="C010C6BF10C6BBA2" TYPE="ntfs"
/dev/sdc1: UUID="cfa67a05-e20e-4401-af51-2aa115cf38d3" TYPE="ext3"
/dev/sda1: SEC_TYPE="msdos" UUID="4563-A2CC" TYPE="vfat"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


=================== dmesg | grep EFI :
This live-session is not EFI-compatible.




=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
sdc1    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdc1.

sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    2048 sectors * 512 bytes
sdc    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes

=================== parted -l:

Model: Sony Storage Media (scsi)
Disk /dev/sda: 2013MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  2013MB  2013MB  primary  fat16        boot


Model: ATA ST3320620AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  320GB  320GB  primary  ntfs         boot


Model: ATA ST3250620AS (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  250GB  250GB  primary  ext3


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /live/image type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type ext3 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dmmidi dri dvd dvdrw fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem midi net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sdb sdb1 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sndstat sr0 stderr stdin stdout urandom vga_arbiter xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sdb1: Windows Users Information Volume System $Recycle.Bin Recovery (x86) Files Program Files Program ProgramData PerfLogs pagefile.sys menu.lst hiberfil.sys grldr.mbr grldr eclipse-java-galileo-win32 Settings and Documents BOOTSECT.BAK boot-sav bootmgr boot.ini Boot

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.8G   61M  1.7G   4% /
tmpfs        tmpfs    1.8G     0  1.8G   0% /lib/init/rw
udev         tmpfs    1.8G  200K  1.8G   1% /dev
tmpfs        tmpfs    1.8G     0  1.8G   0% /dev/shm
/dev/sda1     vfat    1.9G  371M  1.6G  20% /live/image
tmpfs        tmpfs    1.8G   61M  1.7G   4% /live/cow
tmpfs        tmpfs    1.8G     0  1.8G   0% /live
tmpfs        tmpfs    1.8G  8.0K  1.8G   1% /tmp
/dev/sdb1  fuseblk    299G   56G  243G  19% /mnt/boot-sav/sdb1
/dev/sdc1     ext3    230G  214G  4.2G  99% /mnt/boot-sav/sdc1

=================== fdisk -l:

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa825a825

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f9f8bf4

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux

Disk /dev/sda: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cdc4

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         953     1966064    6  FAT16
Partition 1 has different physical/logical endings:
phys=(960, 128, 32) logical=(952, 71, 32)



=================== Default settings
Recommended-Repair
This setting would restore the [(generic mbr)] MBR in sdb, and make it boot on sdb1.
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.[/QUOTE]

---

### Post by drmrgd on 2012-08-27
> **jtwigg00 said:**
> drmrgd,

My motherboard is an Asus "P8Z77-V LX". If necessary I can boot into the uefi setup to get the firmware version or other info.

I have done a complete power off. I flipped the switch on the power supply and waited for all the LEDs on the motherboard to go out before restarting. I confirmed that the power and SATA cables are connected to the disk.

oldfred,

I have three disks: ext4 (Ubuntu), ext4 (no OS/storage), and NTFS (Windows 7). SeaTools can detect the storage disk, but not the one with Ubuntu on it. The UEFI/BIOS does not see the drive, it says that nothing is connected to the sata port.

I will try to run boot-repair and report back with the results.

Oldfred is much, much better at diagnosing this kind of thing than me.  I can't seem to see any linux system listed there (is there another drive that is just not being reported by the script?).  There certainly doesn't look to be a bootable partition on sdc; is that where you have Ubuntu installed?  If you have another drive that's not being reported in the script, I wonder about plugging it into a different SATA port and trying again.

The only reason I ask about the motherboard is that I have an ASUS board too (one of the X79 boards), and since I upgraded the kernel last week, I had a the same failure to bring anything up on the monitor after restoring from hibernation as well.  I only have 1 monitor set up at the moment, and I thought it was interesting that you could see something on the left monitor but not the right one.  I'm not sure what's going on, but I'm sort of wondering if there is a kernel / motherboard conflict.  I might be over-reaching with that, though.  Let's see what Oldfred has to say.

---

### Post by jtwigg00 on 2012-08-27
> **drmrgd said:**
> Oldfred is much, much better at diagnosing this kind of thing than me.  I can't seem to see any linux system listed there (is there another drive that is just not being reported by the script?).  There certainly doesn't look to be a bootable partition on sdc; is that where you have Ubuntu installed?  If you have another drive that's not being reported in the script, I wonder about plugging it into a different SATA port and trying again.

There is no bootable partition on sdc, this is expected. This is not the disk where I have Ubuntu installed. Ubuntu is installed on another disk which is not detected by the script at all.

I have tried swapping the SATA ports for my misbehaving disk and my DVD drive, to no avail. The DVD drive is detected just fine and the Ubuntu disk is still missing. Good idea though.

> **drmrgd said:**
> The only reason I ask about the motherboard is that I have an ASUS board too (one of the X79 boards), and since I upgraded the kernel last week, I had a the same failure to bring anything up on the monitor after restoring from hibernation as well.  I only have 1 monitor set up at the moment, and I thought it was interesting that you could see something on the left monitor but not the right one.  I'm not sure what's going on, but I'm sort of wondering if there is a kernel / motherboard conflict.  I might be over-reaching with that, though.  Let's see what Oldfred has to say.

I haven't updated the kernel since the last time it worked properly.

---

### Post by drmrgd on 2012-08-27
> **jtwigg00 said:**
> There is no bootable partition on sdc, this is expected. This is not the disk where I have Ubuntu installed. Ubuntu is installed on another disk which is not detected by the script at all.

I have tried swapping the SATA ports for my misbehaving disk and my DVD drive, to no avail. The DVD drive is detected just fine and the Ubuntu disk is still missing. Good idea though.

I haven't updated the kernel since the last time it worked properly.

I kind of thought that was the case, but wanted to confirm the script is  not seeing the drive at all.  If you've confirmed that the SATA port is  OK, and there's not been a kernel upgrade, I'm starting to wonder if there is a major problem with the drive or the cable (which would be extremely rare I think).  Even if the drive is unformatted, it should be picked up by the Bootinfo script and listed as such.  Can you hear it clicking or showing any signs of life when you boot up or try to access it?

---

### Post by jtwigg00 on 2012-08-27
> **drmrgd said:**
> Can you hear it clicking or showing any signs of life when you boot up or try to access it?

If I touch it then I can feel it vibrating very slightly and it's rather warm, so I'm pretty sure it's on and spinning.

---

### Post by oldfred on 2012-08-27
If BIOS/UEFI does not see drive, none of the tools in Linux nor Windows will see the drive. 

In old days I have partially disconnected the parallel cable and drive would light up but not work. But with new SATA that should not be an issue.

Others with various versions of Asus posted these, do any apply to you?

> Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.


---

### Post by jtwigg00 on 2012-08-27
I didn't see any menus relating to "I/O interface security". I tried the setting the sata configuration as described (which was to enable hot swap for that port), but it did not work.

---

### Post by oldfred on 2012-08-27
If BIOS does not see drive, it just about has to be a hardware issue. Again check connections, try different cables and different ports.

If none of that works try drive in another system if you can.

---

### Post by jtwigg00 on 2012-08-27
Confirmed the connections. Previously confirmed it's not the port because the same port works with another device. Swapped the cables and the same cable works with a different device.

Unfortunately I don't have another desktop to plug it into.

I guess it just died. If the uefi/bios can't recognize it then I suppose I shouldn't get my hopes up about recovering any data from it. Maybe I'll set up a RAID1 this go around. Thanks for your time today.

---

