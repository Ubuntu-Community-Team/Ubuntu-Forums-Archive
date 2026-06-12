---
title: "Gparted Error"
date: 2012-03-09
forum: General Help
---

### Post by sumanshu on 2012-03-09
I was resizing the partition for linux using gparted and got the following error.
Any help
[I]"ERROR: Current NTFS volume size is bigger than the device size!
Corrupt partition table or incorrect device partitioning?[/I]"

complete gparted details are attached
Thanks

---

### Post by oldfred on 2012-03-09
Post this:

sudo parted /dev/sda unit s print

If size is wrong and partition table is corrupted you may be able to use fixparts. And/or you may need to run chkdks from a Windows repairCD/USB on your NTFS partition.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by sumanshu on 2012-03-10
> **oldfred said:**
> Post this:

sudo parted /dev/sda unit s print

If size is wrong and partition table is corrupted you may be able to use fixparts. And/or you may need to run chkdks from a Windows repairCD/USB on your NTFS partition.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
Hi Oldfred,
Here is the output of command you asked for:

Model: ATA WDC WD3200BEVT-7 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      63s         160649s     160587s     primary   fat16           diag
 2      160713s     31615919s   31455207s   primary   ntfs
 3      31619072s   200185964s  168566893s  primary   ntfs            boot
 4      200186026s  625141759s  424955734s  extended                  lba
 5      200186028s  437460991s  237274964s  logical   ntfs
 6      595646464s  623806463s  28160000s   logical   ext4
 7      623808512s  625141759s  1333248s    logical   linux-swap(v1)

---

### Post by sumanshu on 2012-03-10
> **oldfred said:**
> Post this:

sudo parted /dev/sda unit s print

If size is wrong and partition table is corrupted you may be able to use fixparts. And/or you may need to run chkdks from a Windows repairCD/USB on your NTFS partition.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
the following command:
sudo sfdisk -d /dev/sda > parts.txt
resulted an error saying

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

any help

---

### Post by oldfred on 2012-03-10
Partitions do not use cylinders since hard drives went over 8GB or about 15 years ago. BIOS should have LBA or large as the setting. But almost no BIOS still allow the setting of cylinders. 

The newer rules now for large 4K drives & SSDs is to use 1K boundaries, but you really want 8 sector boundaries.

Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

