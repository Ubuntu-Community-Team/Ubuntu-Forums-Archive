---
title: "New hard disk partioning"
date: 2011-07-04
forum: General Help
---

### Post by sami8519 on 2011-07-04
Hi,

I have just bought a new hard disk 2tb WD green and run gparted but it says: There is no partition table and I have to make one! I go to device>make a new partition table but nothing happens. I tried then fdisk and it says something like this hdd is more than 2tb and I need to use gnu parted. I went to parted and run the command mklabel gpt but for some reason parted outputs that I have discovered a bug and need to report it:( Now I really don't know what should I do next. Do you know guys if there are things I can try or this HDD is defective?

Thanks and best regards,
Sami

---

### Post by aeiah on 2011-07-04
i suggest you launch gparted from the command line to see what happens when 'nothing happens' - hopefully it'll give you some information.

```

gksu gparted
```

---

### Post by srs5694 on 2011-07-04
First, when reporting problems like this it's generally best to cut-and-paste all of the programs' output rather than try to summarize it. When you do so, please start the quoted text with [noparse]```
[/noparse] and end it with [noparse]
```[/noparse]; that keeps it legible, since the forum software tends to mangle some types of program output otherwise. Posting the complete output will tell us exactly what the program is saying, which may include an important message that somebody who's having problems with it would overlook.

Second, new internal disks generally come unpartitioned. This is perfectly normal.

Third, a 2 TB disk is small enough to use with the Master Boot Record (MBR) partitioning system that fdisk creates. A *3* TB disk, though, is too big for MBR (at least without playing "fast and loose" with the rules). (This is one of those cases where the exact program output would be useful -- we could see the disk size as reported by fdisk, which would tell us if you've got a bigger disk than you believed or if there's something weird going on.)

Fourth, if you've got an over-2TiB disk that needs GPT and if parted is flaking out because of a bug (as opposed to a problem like a hardware fault), [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) will probably work. This is an fdisk-like tool for handling GUID Partition Table (GPT) disks, GPT being the partitioning system that's useful on over-2TiB disks.

---

### Post by sami8519 on 2011-07-04
Thanks guys for your help.

Gparted outpus this when run in terminal:

```
/dev/sdf: unrecognised disk label

```**fdisk -l says:**

```
Disk /dev/sdf: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table
```**fdisk /dev/sdf says:**

```
root@ubuntu:~# fdisk /dev/sdf
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xf8128048.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: The size of this disk is 2.2 TB (2199023255552 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').
/CODE]

**GNU parted outputs:**

[CODE]root@ubuntu:~# parted /dev/sdf
GNU Parted 2.3
Using /dev/sdf
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Error: /dev/sdf: unrecognised disk label                                  
(parted) mklabel gpt                                                      


You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Command History:
print
mklabel gpt

Error: FPE_INTDIV (Integer: divide by zero)Aborted
```:(I got a feeling that this HDD has some hardware problems.

---

### Post by srs5694 on 2011-07-04
Your disk is extremely unusual because its size is precisely 2 TiB (2 tebibytes; 2x2^40 bytes, or 2^41 bytes). I've never before heard of a disk like this; manufacturers generally aim for SI (power-of-10) values, which they hit approximately, not precisely. Thus, a "2 TB" disk would be approximately 2x10^12 bytes, which is significantly less than 2x2^40 bytes.

It's conceivable that this peculiarity is a sign of defective electronics on the drive; however, it's also possible that WD has decided to release a disk of precisely this size. You might download the spec sheet for your model from WD's Web site or contact them to resolve this issue. (Note that "2tb WD green" is an imprecise description; you'll need the exact model number, which is printed on a sticker on the drive, and may appear on the box if it's a retail unit.)

I'd just tried creating a virtual disk of precisely 2 TiB in VirtualBox and I didn't run into the problems you had; however, it is plausible that there'd be a divide-by-0 bug that might crop up on such drives, since the software might be dividing values based on the size of the disk, and since disks that are precise power-of-2 multiples in size are so rare, this bug might never before have manifested. If this is the case, though, the bug must be specific to the version of libparted (used by both GParted and parted) installed on your system, vs. the one on my system (which could be a slightly different version).

It seems that fdisk has a very minor bug in its comparison that determines when it can work; it's reporting that the disk is too big when in fact it's precisely at the traditional MBR limit. That is, the code probably uses a "<" comparison when it should have used "<=". If you've got an fdisk "Command (m for help):" prompt, you can go ahead and try partitioning the disk and see if it works. At worst, you'll lose a sector or two of capacity. If you don't get such a prompt, I recommend -- again -- that you try [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/). (Type "sudo apt-get install gdisk" to install it from Ubuntu's repositories.) This program is *not* based on libparted, so if you're seeing a libparted bug, it won't affect gdisk. OTOH, if there is such a bug, it might affect the Ubuntu installer no matter what you use to partition the disk. On yet another hand, if you partition using fdisk or gdisk before installation, the installer might not run into this bug, which manifested for you when you tried to create a new GUID partition table. If you partition ahead of time, you won't have to do that. Even just creating the partition table by launching fdisk or gdisk and then typing "w" might work around the bug. In any event, trying gdisk will give you another view of the disk, which might also help test the hypothesis that there's a hardware problem with the disk -- if gdisk crashes or reports a ridiculous disk size or something, that would tend to support the idea that the disk is faulty. If gdisk works fine and you can then use the disk normally (even if libparted-based tools flake out), then that suggests the disk is fine.

---

### Post by sami8519 on 2011-07-04
wow Thanks so much for your comprehensive reply. You seem to know your stuff very well:)

The Drive model is WD20EARS-00MVWB0

** Just tried gdisk and this is the output:**

```
root@ubuntu:~# gdisk
GPT fdisk (gdisk) version 0.6.14

Type device filename, or press <Enter> to exit: /dev/sdf
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): print
Disk /dev/sdf: 4294967296 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6BFB1572-18E8-474C-B742-40C04835F0F8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4294967262
Partitions will be aligned on 2048-sector boundaries
Total free space is 4294967229 sectors (2.0 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help): help
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): o
This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): Y

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): Y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.

```The thing that makes me doubt gdisk is really doing anything is that it takes almost nothing to report that the operation has completed successfully. However, I then run fdisk -l and it still reports same message:

```
[Disk /dev/sdf: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

```Now I am running fdisk and it is saying writing inode table:

```
root@ubuntu:~# fdisk /dev/sdf
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xc6754adc.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: The size of this disk is 2.2 TB (2199023255552 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT).


WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-267349, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-267349, default 267349): 
Using default value 267349

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
root@ubuntu:~# mkfs.ext3 /dev/sdf
mke2fs 1.41.14 (22-Dec-2010)
/dev/sdf is entire device, not just one partition!
Proceed anyway? (y,n) Y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
134217728 inodes, 536870912 blocks
26843545 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
16384 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000

Writing inode tables:  7370/16384

```The process is running now for 7 hours and I guess another 7 hours are needed to finish. Do you think it could fix this problem or am I just wasting time?

Thanks again for your enormous help.

Regards,

Sami

---

### Post by srs5694 on 2011-07-04
You're confusing two very different tasks, although in some cases they're done by the same program:


[list]
[*]**Disk partitioning** -- This involves assigning ranges of sectors to specific partitions. Disk partitioning can occur almost instantaneously.
[*]**Creating filesystems** -- This involves writing more complex data structures *within* a partition that's already been created by disk partitioning. Depending on the filesystem type (FAT, ext3fs, XFS, etc.), the size of the disk, the speed of the disk, and the options chosen, creating a filesystem can take anywhere from a fraction of a second to several hours, although it's rare for this action to take more than a minute or two on a hard disk.
[/list]


The fdisk, gdisk, parted, and GParted programs can all do disk partitioning, but of these only GParted and pre-3.0 versions of parted can create filesystems. The mkfs program (and various programs with related names, such as mkfs.ext3) create filesystems but do not partition disks.

The fact that gdisk returned very quickly is *not* a sign that it was ineffective. Because fdisk is used for partitioning MBR disks and gdisk is used for GPT disks, you shouldn't expect to be able to use fdisk on a disk to do anything useful after using gdisk on it; however, GPT includes a "protective MBR," which is intended to keep MBR tools from messing with the disk. The fact that this did not show up in fdisk after you used gdisk is a very bad sign. So is the fact that your mkfs.ext3 operation has been running for several hours; I'd expect that to finish after a few minutes at most, even on a 2 TiB disk. (BTW, you shouldn't normally create a filesystem on a whole disk; you should create a filesystem only within a partition. The mkfs.ext3 command warned you about this, but you seem to have ignored the warning. It is legal to use a whole disk for a filesystem, but it limits your options for what to do with the disk in the future.)

I recommend you do the following:


[list=1]
[*]If it's still running, stop the filesystem creation process you've got running. If it runs to completion, don't worry; just go on to the next step.
[*]Launch gdisk again ("sudo gdisk /dev/sdf").
[*]Type "p" to view the partition table (it should be empty) to confirm you're working on the correct disk. If you see partitions defined, type "q" to quit and try again with the correct disk device.
[*]Use gdisk's "n" option to create a partition. just use the default values, which will create a partition that fills the disk.
[*]Type "p" in gdisk to view the partition table. It should have one partition.
[*]Type "w" in gdisk to save your changes. This operation will take a fraction of a second once you confirm it. The program will exit.
[*]Type "sudo gdisk /dev/sdf" again to launch gdisk on the disk again.
[*]Type "p" to view the partition table. If you don't see the partition you created just moments before, then something is very seriously wrong -- probably the disk or some other hardware is defective. Likewise if gdisk complains about damaged partition table data.
[*]Type "q" to exit from gdisk.
[*]If your partition appeared in gdisk, you can try creating a filesystem on it by typing "sudo mkfs.xfs /dev/sdf1". Note the "1" after "sdf" -- that refers to the first partition on the device. Note also I've specified mkfs.xfs, since it's quicker at creating a filesystem than is mkfs.ext3. (If you prefer ext3fs, you can switch to it later.)
[*]If mkfs.xfs reports that it completed successfully, mount the partition by typing "sudo mount /dev/sdf1 /mnt". You should now be able to copy files to /mnt (although you may need to change its permissions first by typing "sudo chmod 0777 /mnt").
[*]Test your ability to copy files to the disk and read them back. If you get error messages, long delays while copying files, etc., then something is wrong.
[/list]


If I had to guess, I'd guess that your disk is defective and that it will fail early in this test procedure -- probably when you try to read the partition table back in gdisk. If so, you shouldn't bother with the rest of the tests. It's also possible, though, that the disk is acting weird for some other reason, such as a loose or defective cable, a defective disk controller, or a buggy Linux driver for the disk controller. (You may have two separate disk controllers on your motherboard, so the fact that other disks work OK isn't an indication that everything's OK for the controller that handles /dev/sdf.)

---

### Post by sami8519 on 2011-07-04
Thanks again:)

The gdisk creating GPT is taking a long time, almost 30 minutes now(maybe this is it, the HDD is dead:(

```
$ sudo gdisk /dev/sdf
[sudo] password for sami: 
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): p
Disk /dev/sdf: 4294967296 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): C3CA334C-2E60-46C3-B22A-047410728DF0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4294967262
Partitions will be aligned on 2048-sector boundaries
Total free space is 4294967229 sectors (2.0 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help): n
Partition number (1-128, default 1): 
First sector (34-4294967262, default = 34) or {+-}size{KMGTP}: 
Information: Moved requested sector from 34 to 2048 in
order to align on 2048-sector boundaries.
Use 'l' on the experts' menu to adjust alignment
Last sector (2048-4294967262, default = 4294967262) or {+-}size{KMGTP}: 
Current type is 'Linux/Windows data'
Hex code or GUID (L to show codes, Enter = 0700): 
Changed type of partition to 'Linux/Windows data'

Command (? for help): p
Disk /dev/sdf: 4294967296 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): C3CA334C-2E60-46C3-B22A-047410728DF0
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4294967262
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      4294967262   2.0 TiB     0700  Linux/Windows data

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed, possibly destroying your data? (Y/N): Y
OK; writing new GUID partition table (GPT).

```

---

### Post by sami8519 on 2011-07-05
I just would like to say thanks a lot for our great buddy SRS5694 for his great troubleshooting.

Officially disk is dead:( Hopefully it get replaced for me with a functioning one!


Best Regards,

Sami

---

### Post by srs5694 on 2011-07-05
I'm sorry to hear the disk is dead. On the bright side, at least you discovered this before filling it with 2 TB of data!

---

