---
title: "Not booting, disk cannot mount"
date: 2012-10-06
forum: General Help
---

### Post by bigred1 on 2012-10-06
I get this problem even in recovery mode, even with older versions of Ubuntu that are still in the Grub menu (latest is Maverick). I ran the default repair of the Boot Repair, to no avail.  

This is what comes up on boot:
```

...[sdb] Add. Sense: Unrecovered read error - auto real locate failed
...mount: mounting /dev/disk/bu-uuid/d818.... on /root failed: Invalid argument
...
Target filesystem doesn't have requested /sbin/init
BusyBox v1.18.4... built-in shell (ash)
...
(initramfs)

```

I then type ```
exit
``` and get
```

... Kernel panic ... not synching: Attempted to kill init!
... Pid: 1, com: init Not tainted 3.0.0-16-generic #28-Ubuntu

```

Here is what ```
dmesg |tail
``` gives me 

```

[ 1724.112966] Descriptor sense data with sense descriptors (in hex)
[ 1724.112970] 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1724.112991] 00 84 d3 21 
[ 1724.113000] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1724.113015] sd 2:0:0:0: [sdb] CDB: Read(10): 28 00 00 84 d3 1f 00 00 08 00
[ 1724.113030] end_request: I/O error, dev sdb, sector 8704801
[ 1724.113046] JBD2: Failed to read block at offset 6748
[ 1724.113057] ata3: EH complete
[ 1724.113059] JBD2: recovery failed
[ 1724.113063] EXT4-fs (sdb1): error loading journal

```

Below is a boot info summary. it seems that sdb1, where Ubuntu is located, is not mounting: "wrong fs type bad option, bad superblock."

How can I get my Ubuntu to boot?

```

	Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info September 18th 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
	the same hard drive for core.img. core.img is at this location and looks 
	for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
	the same hard drive for core.img. core.img is at this location and looks 
	in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

	File system:       ntfs
	Boot sector type:  Windows Vista/7: NTFS
	Boot sector info:  No errors found in the Boot Parameter Block.
	Operating System:  Windows 7
	Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
					   /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

	File system:       ext4
	Boot sector type:  -
	Boot sector info: 
	Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
	   missing codepage or helper program, or other error
	   In some cases useful info is found in syslog - try
	   dmesg | tail  or so


sdb2: __________________________________________________________________________

	File system:       Extended Partition
	Boot sector type:  -
	Boot sector info: 

sdb5: __________________________________________________________________________

	File system:       swap
	Boot sector type:  -
	Boot sector info: 

sdb3: __________________________________________________________________________

	File system:       ext4
	Boot sector type:  -
	Boot sector info: 
	Operating System:  
	Boot files:        

sdc1: __________________________________________________________________________

	File system:       ntfs
	Boot sector type:  Windows Vista/7: NTFS
	Boot sector info:  No errors found in the Boot Parameter Block.
	Operating System:  
	Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   160,071,659   160,071,597   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    19,535,039    19,534,977  83 Linux
/dev/sdb2         300,576,150   312,576,704    12,000,555   5 Extended
/dev/sdb5         300,576,213   312,576,704    12,000,492  82 Linux swap / Solaris
/dev/sdb3          19,535,040   300,576,149   281,041,110  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048 1,953,519,615 1,953,517,568   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1EC8A6D4C8A6AA0B                       ntfs       Local Disk
/dev/sdb1        d8183543-f97b-4f71-b27f-3fa8426ccfdd   ext4       
/dev/sdb3        f7d87294-1460-459b-a29a-76a8ca85526f   ext4       
/dev/sdb5        6036269d-9307-4ec0-b67e-0d28a0b2f790   swap       
/dev/sdc1        FCCE6E20CE6DD404                       ntfs       Elements

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /live/image              iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-10-04__20h16 ===================
boot-repair version : 3.193-0ppa22~lucid
boot-sav version : 3.193-0ppa39~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version :
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu) lucid main
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 32B18A1260D8DA0B
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 32B18A1260D8DA0B
W: Duplicate sources.list entry [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_lucid_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/) lucid/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_os-uninstaller_ubuntu_dists_lucid_main_binary-i386_Packages)

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
os-uninstaller

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
boot-repair
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Bus error
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit, 64-bit
initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

sudo: cannot get working directory

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="Local Disk" UUID="1EC8A6D4C8A6AA0B" TYPE="ntfs"
/dev/sdb1: UUID="d8183543-f97b-4f71-b27f-3fa8426ccfdd" TYPE="ext4"
/dev/sdb3: UUID="f7d87294-1460-459b-a29a-76a8ca85526f" TYPE="ext4"
/dev/sdb5: UUID="6036269d-9307-4ec0-b67e-0d28a0b2f790" TYPE="swap"
/dev/loop0: TYPE="squashfs"
/dev/sdc1: LABEL="Elements" UUID="FCCE6E20CE6DD404" TYPE="ntfs"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

=================== dmesg | grep EFI :
This live-session is not EFI-compatible.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	ntldr,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.
sdb3	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb3.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/media/Elements.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	63 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	63 sectors * 512 bytes
sdc	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Maxtor 6Y080L0 (scsi)
Disk /dev/sda: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  82.0GB  82.0GB  primary  ntfs         boot


Model: ATA WDC WD1600AAJS-2 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  10.0GB  10.0GB  primary   ext4            boot
3      10.0GB  154GB   144GB   primary   ext4
2      154GB   160GB   6144MB  extended
5      154GB   160GB   6144MB  logical   linux-swap(v1)


Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs         boot



																		  
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

																		  
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:82.0GB:scsi:512:512:msdos:ATA Maxtor 6Y080L0;
1:32.3kB:82.0GB:82.0GB:ntfs::boot;

BYT;
/dev/sdb:160GB:scsi:512:512:msdos:ATA WDC WD1600AAJS-2;
1:32.3kB:10.0GB:10.0GB:ext4::boot;
3:10.0GB:154GB:144GB:ext4::;
2:154GB:160GB:6144MB:::;
5:154GB:160GB:6144MB:linux-swap(v1)::;

BYT;
/dev/sdc:1000GB:scsi:512:512:msdos:WD Ext HDD 1021;
1:1049kB:1000GB:1000GB:ntfs::boot;


																		  
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

																		  
Error: /dev/sr0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdc1 on /media/Elements type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb3 on /mnt/boot-sav/sdb3 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart block bsg bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw fb0 fd full fuse hidraw0 hidraw1 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sdb sdb1 sdb2 sdb3 sdb5 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sndstat sr0 stderr stdin stdout urandom vga_arbiter xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sda1: ZFVNK Windows Users temp Information Volume System Shared RECYCLER $Recycle.Bin RebeccaNew Files Program ProgramData pagefile.sys ntldr NTDETECT.COM MSDOS.SYS MAXIS IO.SYS amvvideoconverter iOrgSoft hiberfil.sys FYI_movie found.004 found.003 found.002 found.001 found.000 DVDVideoSoft Settings and Documents config.sys Config.Msi changes.dat boot-sav bootmgr Boot $AVG autoexec.bat

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs   1008M   42M  967M   5% /
tmpfs        tmpfs   1008M     0 1008M   0% /lib/init/rw
udev         tmpfs   1003M  188K 1003M   1% /dev
tmpfs        tmpfs   1008M     0 1008M   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs   1008M   42M  967M   5% /live/cow
tmpfs        tmpfs   1008M     0 1008M   0% /live
tmpfs        tmpfs   1008M  8.0K 1008M   1% /tmp
/dev/sdc1  fuseblk    932G  167G  765G  18% /media/Elements
/dev/sda1  fuseblk     77G   61G   16G  80% /mnt/boot-sav/sda1
/dev/sdb3     ext4    132G   57G   69G  46% /mnt/boot-sav/sdb3

=================== fdisk -l:

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06e306e2

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe28a95a8

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2           18711       19457     6000277+   5  Extended
/dev/sdb3            1217       18710   140520555   83  Linux
/dev/sdb5           18711       19457     6000246   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023830

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976758784    7  HPFS/NTFS



=================== Recommended repair
Recommended-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s


Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 1 boot on

																		  
Information: You may need to update /etc/fstab.

sudo: cannot get working directory

Boot successfully repaired.

You can now reboot your computer.

```

---

