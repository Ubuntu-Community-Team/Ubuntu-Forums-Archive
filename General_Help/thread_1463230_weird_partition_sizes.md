---
title: "weird partition sizes"
date: 2010-04-26
forum: General Help
---

### Post by tropdoug on 2010-04-26
I asked this once before but did not get a conclusive answer, so the issue has arisen again lets try once more.

I have a partition containing 41.3 gigs of files (see screen shot) but in Gparted and in the graphic of space used it shows 54.7 gigs. 

I have highlighted all files (including the hidden ones) and still the size records as 41.3

can anyone tell me what the extra space is being taken up with? 

Thanks in advance

---

### Post by hopstah on 2010-04-27
My first question would be to check that you are displaying your hidden files and folders.  Anything that begins with a "." is hidden from view unless you are displaying those folders.  In Gnome, I'm pretty sure it's under your View menu to show those files.  If that's not it, I'll try to think of something else.

---

### Post by rnerwein on 2010-04-27
hi
use the command tune2fs in a terminal window ( you must be super user - root  to run this command ).
tune2fs /dev/sdaX -l ( l -> ell not ee ) ( the device name depends on your configuration) shows you the contents of your partition.
you will find there a lot of stuff. even "Reserved block count:". this value is the default ( 5% ) if a filesystem is setup
without any options ( my opinion is that's coming form history - small disks ). but now - if you have a 1TB disk that means
there a 50 GB reserved by default - ups. this space is reserved for system deamons ( e.g. syslogd ). if a deamon wants
to tell you that a filesystem is full and there is no free space - you are the looser. but don't panic.
you can manupulate this value via tune2fs - but don't set it to 0 !!.
--> tune2fs -m 1 /dev/sdaX   will set the reseverd part to 1 percent. i guess that's enough.
and have a look at the other stuff you see with the -l option. this space is real - not virtual - and must be stored on the
partition too.
hope this will help you to understand the layout of partitions.
and remember: real programmers don't use mice !
ciao

---

### Post by john newbuntu on 2010-04-27
Intriguing!  13GB difference on a filesystem.  Could you please post the outputs of "df -Th" and "sudo fdisk -l" just for comparison?

---

### Post by tropdoug on 2010-04-27
This is the output from the tune2fs command

douglas@desktop:~$ sudo tune2fs /dev/sda6 -l
tune2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          48ff847c-b3a5-4f8c-a2af-30ce17c500d1
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              4218880
Block count:              16850169
Reserved block count:     842508
Free blocks:              3078936
Free inodes:              4190660
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Tue Jul 28 19:40:21 2009
Last mount time:          Mon Apr 26 22:36:26 2010
Last write time:          Mon Apr 26 22:36:26 2010
Mount count:              12
Maximum mount count:      26
Last checked:             Tue Apr 20 07:32:20 2010
Check interval:           15552000 (6 months)
Next check after:         Sun Oct 17 07:32:20 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      34dc1850-fdba-461d-99c1-35ce36773c41
Journal backup:           inode blocks

---

### Post by tropdoug on 2010-04-27
Ok df -th gives 

douglas@desktop:~$ df -Th
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sda1     ext3    9.2G  4.8G  4.0G  55% /
udev         tmpfs   1007M  304K 1007M   1% /dev
none         tmpfs   1007M   28K 1007M   1% /dev/shm
none         tmpfs   1007M  288K 1007M   1% /var/run
none         tmpfs   1007M     0 1007M   0% /var/lock
none         tmpfs   1007M     0 1007M   0% /lib/init/rw
/dev/sdb1     ext3     98G   16G   78G  17% /mnt/musicpart
/dev/sdb2     ext3     99G  7.2G   87G   8% /mnt/PhotoPart
/dev/sdb5     ext4    263G   52G  199G  21% /home
/dev/sda6     ext3     64G   52G  8.6G  86% /media/48ff847c-b3a5-4f8c-a2af-30ce17c500d1


sda6 is the offending partition. Its mounted this way because I have succesfully moved the /home to a new larger partition. However before I delete the old /home I would love to find out what is causing the difference in size. 

And this is the output from fdisk

douglas@desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d4aca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        9729    68380672+   5  Extended
/dev/sda5            1217        1338      979933+  82  Linux swap / Solaris
/dev/sda6            1339        9729    67400676   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b63cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12890   103538893+  83  Linux
/dev/sdb2           12891       25931   104751832+  83  Linux
/dev/sdb3           25932       60801   280093275    5  Extended
/dev/sdb5           25932       60801   280093243+  83  Linux

---

### Post by john newbuntu on 2010-04-27
Like rnerwein explained, dividing "Reserved block count” by “Block count” gets the 5% for reserved.  842508/16850169 = 0.05 (or 5%)

df -Th correctly reports the total size of the disk as 64GiB that corresponds to 69GB.  It also says available as 8.4GiB and used as 52GiB which is fairly close to what we see on the graph.  But still not sure on how it is getting 41.3GB?  Now if you unmount the partition "/media/da..da..", is there another directory mounted on /dev/sda6?

---

### Post by tropdoug on 2010-04-28
Ok I think I found the answer. after reading your replies I went searching for a terminal command and found du. Using this command 

du -ch  (the -c totals the file size and the -h puts into human read format)

the result was

52G    /media/48ff847c-b3a5-4f8c-a2af-30ce17c500d1/douglas.old
52G    total

and when I did the same restricted to the** hidden files** only it came to a total of 12Gigs. So it may be academic, but if you want to know the _**true total size**_ of files occupying a directory, partition or disc, make sure you use the command line, not the GUI options available from nautilus or other apps, and get the true calculation. 

So it appears that even though I DID have ALL the hidden files showing the right click > Properties in Nautilus does not give a true total of folder size as it does not count the hidden files sizes at all, thus the discrepancy of 12+ gigs.

Thanks for the help, the suggestions made me think, go looking and finds the tool to find the result. Ergo a better understanding of file management linux style. 

Hope this may help someone else one day.

Douglas  :popcorn::popcorn:

---

