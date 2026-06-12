---
title: "repartitioning disk failed! help"
date: 2006-02-23
forum: General Help
---

### Post by kooshball on 2006-02-23
i was trying to repartition my ubuntu partition.
here's how it was setup

primary1 ntfs for windows
extended:
ext3 partition for linux
swap for linux

i was trying to make a new partition by resizing the ext3 one. so i booted up with the live disk, used gparted to resize the ext3 partition. after it finished, it said i had to restart. and when i did, the whole partition table is now wiped.

when i go to gparted in live now i get the whole disk as unallocated. grub fails to load with Error 22.

help :( is there anyway i can fix the partition table?

---

### Post by Ocxic on 2006-02-23
if you need to recover the data you could try this:
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Partition.pdf](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/pdf/Partition.pdf)

the guide is near the bottom of the contents.

if you don't need to reecover data just reformat everything agian.

---

### Post by lamego on 2006-02-23
To recover you can also try to use partition guess:

[http://www.stud.uni-hannover.de/user/76201/gpart/]("http://www.stud.uni-hannover.de/user/76201/gpart/")

---

### Post by procras on 2006-02-23
If you kept a copy of the partition table you can create it again.

fdisk will do this for you.

---

### Post by Trab on 2006-02-23
grub error 22...says no such partion...
use ur liveCD, and try to mount ur ubuntu partion (if u remember the number...)
if u CAN, your machine can be fixed easily (just by reparing grub) otherwise...
try some other methods to get it back...
your entire partion table is gone?
in live type this in a terminal
```
 fdisk -l 
```
and paste the results here...

---

### Post by kooshball on 2006-02-23
[QUOTE=lamego]To recover you can also try to use partition guess:

[http://www.stud.uni-hannover.de/user/76201/gpart/]("http://www.stud.uni-hannover.de/user/76201/gpart/")[/QUOTE]

i just tried thsi

it seems that the windows partition is found fine but the ext2 one is invalid

```


ubuntu@ubuntu:~$ sudo ./gpart /dev/sda

Begin scan...
Possible partition(Windows NT/W2K FS), size(40962mb), offset(0mb)
Possible extended partition at offset(40962mb)
   Possible partition(Linux ext2), size(15351mb), offset(40962mb)
   Possible partition(Linux swap), size(917mb), offset(56313mb)
End scan.

(Everything above here is correct)

Checking partitions...
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary
   Partition(Linux ext2 filesystem): invalid logical
   Partition(Linux swap or Solaris/x86): orphaned logical
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 40962mb #s(83891360) s(63-83891422)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(5221/254/56)r

Primary partition(2)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 15351mb #s(31439205) s(83891430-115330634)
   chs:  (1023/254/63)-(1023/254/63)d (5222/0/1)-(7178/254/63)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


```

the extended size is correct but the guessed table set the ext2 part as unused which is not correct.

is there any chance i can still recover my ext2 partition? if not i'll just reinstall ubuntu again and save my windows one.

i alsot ried 

fdisk -l

there was no output from that.

---

### Post by az on 2006-02-24
gpart is old.... "Last update: 15. February 2001"

I used parted last week to recover a lost partition.

sudo parted /dev/hda
rescue
(and then type in the approximate location in megabytes of your lost partition.  If it finds something, it will prompt you to add it to the partition table.  Easy.)

---

