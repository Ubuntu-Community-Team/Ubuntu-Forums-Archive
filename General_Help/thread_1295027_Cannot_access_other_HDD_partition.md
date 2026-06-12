---
title: "Cannot access other HDD partition"
date: 2009-10-19
forum: General Help
---

### Post by ArkticMud on 2009-10-19
Hello!
My set up it this: 250GB HDD with windows and a 500GB HDD partitioned into two parts, one with ubuntu installed and one with no-os.

The plan was to load music, movies and other such things that I may want when using both windows and linux onto the no-os partition of my 500GB HDD. However I can't see the other partition when using ubuntu. The 500GB HDD if formatted with NTFS but I assume this is not a problem since ubuntu has no problems using the files on the 250GB HDD. 

I can see and access the partition when booting windows.

So the question is how can I see and use the other partition on the 500GB HDD?

---

### Post by nigel_nb on 2009-10-19
Open a terminal and type

```
$ sudo parted /dev/sda print
```you should get something like 
```

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  122GB  122GB   primary   ntfs         boot 
 2      122GB   181GB  59.1GB  primary   ntfs              
 3      181GB   240GB  59.0GB  extended                    
 6      181GB   235GB  54.0GB  logical   ext4              
 5      235GB   240GB  4993MB  logical   linux-swap        
 4      240GB   250GB  9747MB  primary   ntfs  

```Okay, you'd have only 5.  So, the one thats isn't ext4, linux-swap, not flagged as boot, and the one that isn't already mounted is the one that you have to mount.  Take a note of the number of the drive u have to mount.

Make a directory to place the drive you are going to mount.
```
$ sudo mkdir /media/drive2
```Mount the drive (NOTE:  Replace X in sdaX with the number of u get from above).
```
$ sudo mount /dev/sdaX /media/drive2 -t ntfs -r
```When you want to unmount (NOTE: There is no n in the command)
```
$ umount /media/drive2
```

---

### Post by monroetransfer on 2009-10-19
I've got a similar setup except that my windows partition is on the same HDD as the other two. However for my shared space, I'm using FAT32, which I would recommend you do. Ubuntu has gotten pretty good at writing & reading ntfs but I've still encountered a few problems here and there. Fat32 is read/write/visable to both windows and ubuntu and I've never had any trouble. It wouldn't take long to format, and since you haven't put anything important into the partition already, there's no loss.

Also, I'm not sure how windows goes about mounting external HDD at boot. If I read you correct, you're trying to get windows to see the partition? I think the poster above me gave you instructions for using the shared partition when in linux, but no info for windows. If you'd like the partition to be mounted automatically when you boot ubuntu, read up on /etc/fstab.

I have a line which mounts my shared partition for example:

```
/dev/sda2	/media/storage	vfat	    defaults,user,exec,uid=1000,gid=100,umask=000	     0	     1
```

where the partition is at /dev/sda2, I'd like to mount it at /media/storage (I had to mkdir it), the filesystem is Fat32 which is written as "vfat" for some reason, and the rest is permissions stuff I think? When I wrote the line I had a bunch of fstab knowledge in my short-term memory, but I don't think a lot of it has stuck with me.

Anyways, it seems your problem is with windows. I'm not sure I can help much. Maybe google around for windows and mounting external hdd partitions?

---

### Post by ArkticMud on 2009-10-20
It works fine with windows, its just ubuntu that encounters a problem. I have a few files that are over 4GB so I believe that this makes FAT32 unsuitable. When typing in the command above it tells me that the only HDD is the 250GB, it doesn't mention the partition it is installed on or the other partition on the 500GB HDD

Here is the command output:

******@******:~$ sudo parted /dev/sda print
Model: ATA ST3250310AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  ntfs         boot

---

### Post by oldfred on 2009-10-20
post the results of :

$ sudo parted /dev/sdb print

---

### Post by nigel_nb on 2009-10-20
can you see the other HDD when booting into live CD?

---

### Post by nigel_nb on 2009-10-20
Just to add to [oldfred]("http://ubuntuforums.org/member.php?u=852711")
Can you paste the out put of 
```
sudo fdisk -l
```

---

### Post by ArkticMud on 2009-10-26
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdadbdadb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59194   475475773+   7  HPFS/NTFS
/dev/sdb2           59195       60801    12908227+   5  Extended
/dev/sdb5           59195       60727    12313791   83  Linux
/dev/sdb6           60728       60801      594373+  82  Linux swap / Solaris

---

### Post by nigel_nb on 2009-10-26
Okay, so the partition that you have to mount is sdb1.  It is the NTFS formatted partition in your 500 GB hard disk.

So you can do the following steps
Make a directory to place the drive you are going to mount.
 ```
$ sudo mkdir /media/drive2
```Mount the drive.
 ```
$sudo mount /dev/sdb1 /media/drive2 -t ntfs -o nls=utf8,umask=0222
```When you want to unmount (NOTE: There is no n in the command)
 ```
$ umount /media/drive2
```Alternatively, you could use a GUI tool called ntfs-config
Step 1
Open a terminal window and type [FONT=courier new]sudo apt-get install ntfs-config
[/FONT]
Step 2
Run NTFS configuration in the menu (System > Administration)

Step 3
Choose the drives that you want to be automatically mounted.

Step 4
Put a check next to "Enable Write Support for Internal Drives"

---

