---
title: "problem mounting solaris 10 EFI GPT labeled hard drive"
date: 2010-02-09
forum: General Help
---

### Post by siliconlunch on 2010-02-09
I have a 1.5TB hard drive that was initially set up on a Solaris 10 x86 host system. Due to the large device size, Solaris labeled the disk with an EFI (GPT) label instead of the traditional SMI (VTOC) label when it was partitioned. 4 slices are defined in the GPT: root (128 MB), swap (128 MB), usr (1.4 TB) and reserved (8 MB). This was the default suggested layout. A standard Solaris UFS filesystem was created on the 1.4TB usr slice.

I have now physically removed the hard drive from the solaris system and have installed it in an Ubuntu 9.10 system.

I have no trouble mounting regular Solaris UFS filesystems on _SMI_-labeled drives:

```
# mount -v -r -t ufs -o ufstype=sunx86 /dev/sdb1 /mnt

```However for EFI-labeled drives such as the one I described above, there are multiple issues.

1. Ubuntu believes the GPT is incorrect, as witnessed by these syslog messages:

```
kernel: [    2.559777] scsi 4:1:6:0: Direct-Access              ST31500341AS     CC1H PQ: 0 ANSI: 5
kernel: [    2.600193] sd 4:1:6:0: Attached scsi generic sg11 type 0
kernel: [    2.614916] sd 4:1:6:0: [sde] 2925506560 512-byte logical blocks: (1.49 TB/1.36 TiB)
kernel: [    2.616350] sd 4:1:6:0: [sde] Write Protect is off
kernel: [    2.618661] sd 4:1:6:0: [sde] Write cache: enabled, read cache: enabled, supports DPO and FUA
kernel: [    2.637529]  sde:
kernel: [    2.664565] GPT:Primary header thinks Alt. header is not at the end of the disk.
kernel: [    2.664567] GPT:2925506558 != 2925506559
kernel: [    2.664568] GPT:Alternate GPT header not at the end of the disk.
kernel: [    2.664570] GPT:2925506558 != 2925506559
kernel: [    2.664571] GPT: Use GNU Parted to correct GPT errors.
kernel: [    2.664573]  sde1 sde2 sde7 sde9
kernel: [    2.684908] sd 4:1:6:0: [sde] Attached SCSI removable disk

```Notice that the 4 slices are detected as reported as sde1, sde2, sde7 and sde9. I assume Ubuntu has mapped the 4 slices in the GPT as follows:

```
slice 0  [root]     128MB   = sde1?
slice 1  [swap]     128MB   = sde2?
slice 6  [usr]      1.4TB   = sde7?
slice 8  [reserved] 8MB     = sde9?

```Notice how Ubuntu is not recognizing or reporting the Solaris ufs filesystem on sde7.

2: the UFS filesystem is not mountable.

```
# mount -v -r -t ufs -o ufstype=sunx86 /dev/sde7 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sde7,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```The message in syslog is:
```
Feb 10 10:54:24 hope kernel: [60605.157071] ufs_read_super: bad magic number

```I attempted to use GNU Parted to "fix" the issues reported. But after "fixing" the GPT, the entire disk became unrecognizable.

```
Feb  9 17:47:59 hope kernel: [   30.411097]  sde: unknown partition table
```This suggests that GNU Parted is somehow making the situation worse after it "fixes" the problems it sees. I had to restore several key LBAs from backups to get the disk back to where it was.

For extra information I have attached a dump of the GPT on this drive:

```
LBA 1
======
signature                 = [EFI PART]
revision                  = [0x00000100]
header_size               = [0x00000200] [512] bytes
header_crc32              = [0x579ee31c]
reserved1_zero            = [0x00000000]
current_lba               = [0x0000000000000001] 1
backup_lba                = [0x00000000ae5faffe] 2925506558
first_usable_lba          = [0x0000000000000022] 34
last_usable_lba           = [0x00000000ae5fafdd] 2925506525
disk_guid                 = [b5 77 87 5c 34 5e e6 e9 e5 d3 9f 87 b2 c7 bc 0e]
partion_entries_start_lba = [0x0000000000000002] 2
num_partition_entries     = [0x00000009] 9
size_of_partition_entry   = [0x00000080] 128
partition_array_crc32     = [0xe1714ee3]
reserved2_zero            = [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]

    PE 0
    ======
    partition_type_guid                 = [4d cf 85 6a d2 1d b2 11 99 a6 08 00 20 73 66 31] [6A85CF4D-1DD2-11B2-99A6-080020736631] [Solaris:Root partition]
    unique_partition_guid               = [de 3b 19 22 44 3e c5 b9 e2 f4 9e 23 b9 d9 c0 11]
    first_lba                           = [0x0000000000000022] 34
    last_lba                            = [0x0000000000040021] 262177
    attribute_flags                     = [0b0000000000000000000000000000000000000000000000000000000000000000] [-]
    partition_name                      = [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]

    PE 1
    ======
    partition_type_guid                 = [6f c4 87 6a d2 1d b2 11 99 a6 08 00 20 73 66 31] [6A87C46F-1DD2-11B2-99A6-080020736631] [Solaris:Swap partition]
    unique_partition_guid               = [8d e8 46 7b 73 36 ef 35 b7 1d 8b fd ef d9 f5 a9]
    first_lba                           = [0x0000000000040022] 262178
    last_lba                            = [0x0000000000080021] 524321
    attribute_flags                     = [0b0000000000000000000000000000000000000000000000000000000000000001] [System]
    partition_name                      = [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]

    PE 6
    ======
    partition_type_guid                 = [c3 8c 89 6a d2 1d b2 11 99 a6 08 00 20 73 66 31] [6A898CC3-1DD2-11B2-99A6-080020736631] [Solaris:/usr partition]
    unique_partition_guid               = [c4 68 d5 73 89 8f e1 d6 86 85 98 b9 0d b2 22 ab]
    first_lba                           = [0x0000000000080022] 524322
    last_lba                            = [0x00000000ae5f6fdc] 2925490140
    attribute_flags                     = [0b0000000000000000000000000000000000000000000000000000000000000000] [-]
    partition_name                      = [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]

    PE 8
    ======
    partition_type_guid                 = [3b 5a 94 6a d2 1d b2 11 99 a6 08 00 20 73 66 31] [6A945A3B-1DD2-11B2-99A6-080020736631] [Solaris:Reserved-1 partition]
    unique_partition_guid               = [b9 bd a3 ab 54 a3 49 0a 96 be a4 2b 5b bc 1b e5]
    first_lba                           = [0x00000000ae5f6fdd] 2925490141
    last_lba                            = [0x00000000ae5fafdc] 2925506524
    attribute_flags                     = [0b0000000000000000000000000000000000000000000000000000000000000001] [System]
    partition_name                      = [00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00]

```Has anyone managed to get large UFS filesystems on EFI-labeled Solaris drives to mount on Ubuntu?

---

### Post by siliconlunch on 2010-02-10
I think I have identified the key problem:  When I read 512-byte blocks from /dev/sde7 (which is supposed to the the Solaris UFS slice), all I get back is zeros from LBA 0 onwards. This at least explains why the mount fails.

The issue is the part of the kernel that reads the partition table on disk [sde] and creates the Linux primary & extended partitions from the data therein. The sd(4) manpage says:

> The block device name has the following form: sdlp, where l is a
letter denoting the physical drive, and p is a number denoting
the partition on that physical drive.  Often, the partition
number, p, will be left off when the device corresponds to the
whole drive.

partition 0 is the whole drive
partitions 1-4 are the DOS "primary" partitions
partitions 5-8 are the DOS "extended" (or "logical") partitions
From this, the mapping of my [sde] partitions may be interpreted as:
```
sde1: primary partition
sde2: primary partition
sde7: extended partition
sde9: ? partition

```Clearly something is going wrong when the kernel reads the [sde] GPT and attempts to create devices from all the partitions.

---

### Post by siliconlunch on 2010-02-10
Another update. I have found a workaround to recover my data, which consisted of creating a VMWare Solaris 10 virtual machine and exposing /dev/sde as a "physical disk" to the host OS. When the Solaris virtual machine booted up, I was able to inspect the disk label and confirmed it was intact. Then I simply mounted the usr slice so I could access my data. By setting up a Shared Folder, I am thus now able to copy the data out of the usr partition via the Solaris vm, and save it on the Ubuntu native file system.

For the record, from Solaris' point of view, here is the disk partitioning information and VTOC for that drive:

```

# format -e
Searching for disks...done


AVAILABLE DISK SELECTIONS:
       0. c0d0 <DEFAULT cyl 4092 alt 2 hd 128 sec 32>
          /pci@0,0/pci-ide@7,1/ide@0/cmdk@0,0
       1. c2t0d0 <VMware,-VMware Virtual S-1.0-1.36TB>
          /pci@0,0/pci15ad,1976@10/sd@0,0

Specify disk (enter its number): 1
selecting c2t0d0
[disk formatted]
             Total disk size is 60701 cylinders
             Cylinder size is 48195 (512 byte) blocks

                                               Cylinders
      Partition   Status    Type          Start   End   Length    %
      =========   ======    ============  =====   ===   ======   ===
          1                 EFI               0  60701    60702    100

format> p
PARTITION MENU:
[...]
partition> p
Current partition table (original):
Total disk sectors available: 2925490141 + 16384 (reserved sectors)

Part      Tag    Flag     First Sector          Size          Last Sector
  0       root    wm                34       128.00MB           262177
  1       swap    wu            262178       128.00MB           524321
  2 unassigned    wm                 0            0                0
  3 unassigned    wm                 0            0                0
  4 unassigned    wm                 0            0                0
  5 unassigned    wm                 0            0                0
  6        usr    wm            524322         1.36TB           2925490140
  7 unassigned    wm                 0            0                0
  8   reserved    wu        2925490141         8.00MB           2925506524

partition>

``````

bash-3.00# prtvtoc /dev/dsk/c2t0d0p0
* /dev/dsk/c2t0d0p0 partition map
*
* Dimensions:
*     512 bytes/sector
* 2925506559 sectors
* 2925506492 accessible sectors
*
* Flags:
*   1: unmountable
*  10: read-only
*
*                          First     Sector    Last
* Partition  Tag  Flags    Sector     Count    Sector  Mount Directory
       0      2    00         34    262144    262177
       1      3    01     262178    262144    524321
       6      4    00     524322 2924965819 2925490140   /jbod1
       8     11    01  2925490141     16384 2925506524
bash-3.00# 

``````

bash-3.00# fdisk -W - /dev/rdsk/c2t0d0p0

* /dev/rdsk/c2t0d0p0 default fdisk table
* Dimensions:
*    512 bytes/sector
*    189 sectors/track
*    255 tracks/cylinder
*   60701 cylinders
*
* systid:
*    1: DOSOS12
*    2: PCIXOS
*    4: DOSOS16
*    5: EXTDOS
*    6: DOSBIG
*    7: FDISK_IFS
*    8: FDISK_AIXBOOT
*    9: FDISK_AIXDATA
*   10: FDISK_0S2BOOT
*   11: FDISK_WINDOWS
*   12: FDISK_EXT_WIN
*   14: FDISK_FAT95
*   15: FDISK_EXTLBA
*   18: DIAGPART
*   65: FDISK_LINUX
*   82: FDISK_CPM
*   86: DOSDATA
*   98: OTHEROS
*   99: UNIXOS
*  101: FDISK_NOVELL3
*  119: FDISK_QNX4
*  120: FDISK_QNX42
*  121: FDISK_QNX43
*  130: SUNIXOS
*  131: FDISK_LINUXNAT
*  134: FDISK_NTFSVOL1
*  135: FDISK_NTFSVOL2
*  165: FDISK_BSD
*  167: FDISK_NEXTSTEP
*  183: FDISK_BSDIFS
*  184: FDISK_BSDISWAP
*  190: X86BOOT
*  191: SUNIXOS2
*  238: EFI_PMBR
*  239: EFI_FS
*

* Id    Act  Bhead  Bsect  Bcyl    Ehead  Esect  Ecyl    Rsect      Numsect
  238   0    255    63     1023    255    63     1023    1          2925506558

```

---

