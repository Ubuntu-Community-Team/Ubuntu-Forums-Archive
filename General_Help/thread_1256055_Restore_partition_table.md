---
title: "Restore partition table"
date: 2009-09-02
forum: General Help
---

### Post by slakkie on 2009-09-02
Hello all,

I want to know how I can restore a partition table.

Clonezilla somehow failed in recreating the partitions I had on my disk and now I am unable to restore my backup..

```

$ cat sda-pt.parted
Model: ATA ST980310AS (scsi)
Disk /dev/sda: 156301488s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      63s         42074234s   42074172s   primary   ext3         boot 
 2      42074235s   156296384s  114222150s  extended                    
 7      42074361s   42716834s   642474s     logical   ext3              
 6      42716898s   150288074s  107571177s  logical   ext3              
 8      150288138s  155268224s  4980087s    logical   ext3              
 5      155268225s  156296384s  1028160s    logical   linux-swap        

$ cat sda-pt.sf    
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 42074172, Id=83, bootable
/dev/sda2 : start= 42074235, size=114222150, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=155268225, size=  1028160, Id=82
/dev/sda6 : start= 42716898, size=107571177, Id=83
/dev/sda7 : start= 42074361, size=   642474, Id=83
/dev/sda8 : start=150288138, size=  4980087, Id=83

```

Can someone tell me how I can partition my disk with the layout as described in the files above?

Many thanks!

---

### Post by rbc on 2009-09-02
Two suggestions:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Or, and hopefully I am understanding your situation correctly. sda is the good drive? And you, not imaged, but cloned to a backup drive, sdb? And the partition table was not copied over to sdb? If that is the case, boot the Live CD, connect both drives (Make sure you know which one is which) and type this in terminal:
sudo dd if=/dev/sda of=/dev/sdb bs=512 count=1. That will copy the good MBR (including partition table) from sda to sdb.

---

### Post by asmoore82 on 2009-09-02
_[COLOR="Red"]**Use with extreme caution**[/COLOR]_

```
[COLOR="Red"]#[/COLOR] sfdisk --force /dev/sda < sda-pt.sf
```

This only partitions, it does not initialize filesystems.

---

### Post by jerrrys on 2009-09-02
hopefully testdisk will fix your problem.  for future reference clonezilla will ask if you want to use existing partitions. I suspect you missed that during the clone process...

---

### Post by slakkie on 2009-09-02
> **jerrrys said:**
> hopefully testdisk will fix your problem.  for future reference clonezilla will ask if you want to use existing partitions. I suspect you missed that during the clone process...

It did not ask me that, since the partition table got overwritten by a Fedora install (Fedora had problems with installing itself because I had an extended partition). So I cloned/backed up my disk. When I wanted to restore it again it failed on the lvm which Fedora installed. 
I then removed all partitions (it was different anyways) and redid the restore of my backup. Which failed again. I will try the sfdisk command. Is that available on the Ubuntu liveCD (have Jaunty) or on Puppy Linux or on Backtrack? I'll give it a try, I don't have anything now, it can't get any worse :)

---

### Post by slakkie on 2009-09-02
> **asmoore82 said:**
> _[COLOR="Red"]**Use with extreme caution**[/COLOR]_

```
[COLOR="Red"]#[/COLOR] sfdisk --force /dev/sda < sda-pt.sf
```

This only partitions, it does not initialize filesystems.

```

ubuntu@ubuntu:/media/disk/clonezilla_img/full_backup$ sudo sfdisk /dev/sda < sda-pt.sf 
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   1911    1912-  15358108+  83  Linux
/dev/sda2       1912    2042     131    1052257+  82  Linux swap / Solaris
/dev/sda3       2043    9728    7686   61737795    5  Extended
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       2043+   2107      65-    522081   83  Linux
/dev/sda6       2108+   2503     396-   3180838+  83  Linux
/dev/sda7       2504+   9728    7225-  58034781   83  Linux
Warning: given size (4980087) exceeds max allowable size (0)

sfdisk: bad input
ubuntu@ubuntu:/media/disk/clonezilla_img/full_backup$ echo $?
1

```

If I add the force option, it adds an addition line:

cannot build surrounding extended partition

---

### Post by slakkie on 2009-09-02
I've tested it with the current layout, it fails as well. However...

```

sudo sfdisk -dx /dev/sda > ~/test.sf
sudo sfdisk -fx /dev/sda < ~/test.sf

```

works without any problems.

After the -x flag, I can do the -d without the x...

I think I'm there:

I did the -x with the .sf file of clonezilla and it seems it worked:

```

ubuntu@ubuntu:/media/disk/clonezilla_img/full_backup$ sudo sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 42074172, Id=83, bootable
/dev/sda2 : start= 42074235, size=114222150, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=155268225, size=  1028160, Id=82
/dev/sda6 : start= 42716898, size=107571177, Id=83
/dev/sda7 : start= 42074361, size=   642474, Id=83
/dev/sda8 : start=150288138, size=  4980087, Id=83
ubuntu@ubuntu:/media/disk/clonezilla_img/full_backup$ cat sda-pt.sf 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 42074172, Id=83, bootable
/dev/sda2 : start= 42074235, size=114222150, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=155268225, size=  1028160, Id=82
/dev/sda6 : start= 42716898, size=107571177, Id=83
/dev/sda7 : start= 42074361, size=   642474, Id=83
/dev/sda8 : start=150288138, size=  4980087, Id=83

```

---

### Post by slakkie on 2009-09-02
> **asmoore82 said:**
> _[COLOR="Red"]**Use with extreme caution**[/COLOR]_

```
[COLOR="Red"]#[/COLOR] sfdisk --force /dev/sda < sda-pt.sf
```

This only partitions, it does not initialize filesystems.

I want to kiss you dude. I love you :)

---

