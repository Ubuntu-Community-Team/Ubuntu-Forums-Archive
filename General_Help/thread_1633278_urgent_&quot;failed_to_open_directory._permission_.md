---
title: "urgent &quot;failed to open directory. permission denied&quot;"
date: 2010-11-29
forum: General Help
---

### Post by nalsanj on 2010-11-29
Hi everyone!

i need urgent help. i have messed up and i cant make out. i will try to explain - what i have here is a desktop running on xubuntu karmic. the additional hard drive partitions were accessed thru /media. 

the problems are a result of my unsuccessful attempts at mounting a ".nrg" file using mount manager. after trying a few times without any discernible results, i  gave up. But in the meantime mountmanager gave a warning that some files (possibly /etc/fstab or /etc/mtab) have been changed. to put further fuel to fire i shifted the image file from the desktop to the data hard-drive and shut the computer down. So next day various folders were not accessible and i got the above eror message viz. "Failed to open directory. Permission denied." whenever i tried to access any of the folders. As far as i can make out the folders which are not accessible include /root, /lost&found and the data drive partition in /media. also many files in the /dev folder have a x-mark on them, as well as many other files and folders...

i tried remounting the data partition - the error message is "mount: can't find /media/data in /etc/fstab or /etc/mtab"

The contents of /etc/fstab are

UUID=4CB04E02B04DF2CE /media/Win-Programs ntfs-3g defaults 0 0
UUID=4CA0A2DFA0A2CF30 /media/data ntfs-3g defaults 0 0
UUID=44FC08FFFC08ED4C /media/Win77 ntfs-3g defaults 0 0
UUID=87def84b-8ed3-48c0-9b66-57387edbc798 swap swap sw 0 0
UUID=83571e80-1a10-43c7-8e2b-d47bc2aff356 / ext4 defaults 0 1

The contents of /etc/mtab are

/dev/sda1 / ext4 rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb2 /media/Win-Programs fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/Win77 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0


the data partition is /dev/sda5.

i havent even started trying to get the other folders/ files back.
how do i fix this?

---

### Post by dasan on 2010-11-29
to mount nrg file you need not do this much 
you can directly install acetone iso from repo and do that

When running some thing as root be very careful it can damage your installation

take terminal and goto the folder just before your required folder
and give [COLOR="Blue"]chmod 777 -R  "your dir name"[/COLOR]
insted of 777 you can give some other combination also

---

### Post by nalsanj on 2010-11-29
various threads talked about the chmod command. so im a bit confused. before i attempt it can the significance of the number be more clear?

---

### Post by nalsanj on 2010-11-29
okay so i did 

sudo chmod 777 -R data

now the folder is accessible on the Places menu but i cant see any files or folders in it - tho the available space it is saying is 27 GB out of partition of 190  odd GB. so the data is there but i cant see it!!! Help

---

### Post by ajgreeny on 2010-11-29
It is not so simple that the permissions can be explained in just a couple of words, but it is , nevertheless a logical system of the three digits in the numbers relating to the permissions for owner, group and root.

Here is a summary of the meanings for individual octal digit values:

0 --- no permission
1 --x execute 
2 -w- write 
3 -wx write and execute
4 r-- read
5 r-x read and execute
6 rw- read and write
7 rwx read, write and execute

These are the examples from the Symbolic notation section given in octal notation:

"-rwxrwxrwx" would be represented as777 in the three-digit octal.
"-rwxr-xr-x" would be represented as 755 in three-digit octal.
"-rw-rw-r--" would be represented as 664 in three-digit octal.
"-r-x------" would be represented as 500 in three-digit octal.

I hope that helps you sort it out that side of the above answer.

However, **you should not** mess around with the permissions of any folders in the root file system or you may make your whole operating system unbootable.  The permissions of many files and folders in the OS are set in stone and if you change some, the system will throw errors and tell you that it can not do some important activity.

Tell us what exactly the problem is, with details of any error messages you get at the moment.  It sounds as if you have changed the partition identifications in /etc/fstab in some way, and that should be what is put right rather than rushing in and changing permissions without knowing what you're doing.

---

### Post by nalsanj on 2010-11-29
algreeny i agree. i just tried out the chmod command since the other (windows data) partitions have a 777 i.e. full permission as i could make out from (after changing the permissions)

waqif@waqif-desktop:/media$ ls -l
total 40
drwxrwxrwx 2 root root 4096 2010-09-20 16:08 data
lrwxrwxrwx 1 root root    6 2010-09-20 12:05 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-09-20 12:05 cdrom0
drwxr-xr-x 2 root root 4096 2010-09-20 12:05 cdrom1
drwxr-xr-x 2 root root 4096 2010-09-20 13:59 NTFS-200gb
drwxr-xr-x 2 root root 4096 2010-09-20 14:04 NTFS-miniData
drwxr-xr-x 2 root root 4096 2010-09-20 14:03 NTFS-Win77
drwxrwxrwx 1 root root 8192 2010-09-20 23:31 Win77
drwxrwxrwx 1 root root 8192 2010-11-29 15:58 Win-Programs


Anyway it didnt work in giving me access to the data on that partition.

the problem is much more widespread than that. Of the 3 cdroms above one must be the remnants of the mounting of the nrg file i tried since i have 2 physical cd-drives. i dont understand the time/dates above...

---

### Post by nalsanj on 2010-11-29
i have given the details of my /etc/fstab and /etc/mtab above.

now when i try to access the data i get below message

waqif@waqif-desktop:/media$ ls
data  cdrom0  NTFS-200gb     NTFS-Win77  Win-Programs
cdrom       cdrom1  NTFS-miniData  Win77
waqif@waqif-desktop:/media$ cd /data
bash: cd: /data: No such file or directory

so i can see the folder but it says no such folder. and in the GUI file manger the folder is no longermarked with an x but it doesnt show any contents.

how do i repair the fstab and mtab?

---

### Post by ajgreeny on 2010-11-29
Using a live CD if necessary can you please show the output of ```
sudo fdisk -l
``` and then ```
sudo blkid
```It should then be possible to sort out your /etc/fstab file, but what I'm not sure about is the effect that your chmod commands may have had on some of the files and folders in your system files.

---

### Post by nalsanj on 2010-11-29
ajgreeny (i got your name wrong last time and sorry for the delay - i went for my workout), here are the results of 

sudo fdisk -l


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85fb8fa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            5100       30400   203230282+   f  W95 Ext'd (LBA)
/dev/sda3            4864        5099     1895670   82  Linux swap / Solaris
/dev/sda5            5100       30400   203230251    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99e5138c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2583    20747916    7  HPFS/NTFS
/dev/sdb2            2584        9730    57405440    7  HPFS/NTFS

The results of 
sudo blkid

/dev/sda1: UUID="83571e80-1a10-43c7-8e2b-d47bc2aff356" TYPE="ext4" 
/dev/sda3: UUID="87def84b-8ed3-48c0-9b66-57387edbc798" TYPE="swap" 
/dev/sda5: UUID="4CA0A2DFA0A2CF30" LABEL="data" TYPE="ntfs" 
/dev/sdb1: UUID="44FC08FFFC08ED4C" LABEL="Win77" TYPE="ntfs" 
/dev/sdb2: UUID="4CB04E02B04DF2CE" LABEL="Win-Programs" TYPE="ntfs" 


now?

---

### Post by ajgreeny on 2010-11-29
I have just noticed in your post #7 > waqif@waqif-desktop:/media$ ls
data  cdrom0  NTFS-200gb     NTFS-Win77  Win-Programs
cdrom       cdrom1  NTFS-miniData  Win77
waqif@waqif-desktop:/media$ cd /data
bash: cd: /data: No such file or directorythe final command you tried should be ```
cd data
```not ```
cd /data
```as you are in /media and data is a subfolder of media.

---

### Post by nalsanj on 2010-11-29
okay my bad. here see result of commands again without slash

waqif@waqif-desktop:/home$ cd ..
waqif@waqif-desktop:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
waqif@waqif-desktop:/$ cd /media
waqif@waqif-desktop:/media$ ls
data  cdrom0  NTFS-200gb     NTFS-Win77  Win-Programs
cdrom       cdrom1  NTFS-miniData  Win77
waqif@waqif-desktop:/media$ cd data
waqif@waqif-desktop:/media/backup old$ ls
waqif@waqif-desktop:/media/backup old$

which is that it shows nothing...
data is actually the same as NTFS-200gb but somehow it mounted as data. in the terminal above the different folders are shown in different colors - data, Win77 and Win-Programs are in blue with green highlight; cdrom is in light-blue and the rest are in dark blue. This is possibly specific to xubuntu. 

for the previous 9th post i didnt need to use the live cd. 
any clues for rescuing the /etc/fstab and /etc/mtab...

as a final solution, will reinstalling from live CD work? 

all help is deeply appreciated

---

### Post by ajgreeny on 2010-11-29
Now you have completely lost me!

Where did you get the entry ```
waqif@waqif-desktop:/media/backup old$
``` from, as there does not appear to be a file or folder with the name **backup** or **backup old** in media, but the ```
cd data
```from /media seems to have taken you to /media/backup old, which contains nothing.

I think either you, or I, or perhaps both of us, are a bit confused about what you are doing, or are trying to do.

As for the fstab file, I can see no obvious problems in that related to the UUIDs of the partitions or in the entries, and I'm afraid I can not help with the mtab file, as my knowledge of that is just about nil.

If you decide to reinstall the live CD should work with no problem, but you should backup all your home files and folders first.

---

### Post by nalsanj on 2010-11-30
well a bit silly but to not distract i called my data partition data but actually it is called "backup old". as the things got longer somewhere it had to fail into confusion and it did in the end. 

anyway its sorted out now by reinstalling xubuntu. 

thanks very much all the same.

---

### Post by ajgreeny on 2010-11-30
Just for your information, it will make life a lot easier for you if you avoid spaces in file and folder names, so your **backup old** would be better as **backup-old**.

It is just a small point, but when typing full file and folder pathways in terminal it is a great help if no spaces are present, as it means you do not need to put the pathway in " " marks or use the escape \ before the space, ie, no need for **"/media/backup old"** or **/media/backup\ old**

---

