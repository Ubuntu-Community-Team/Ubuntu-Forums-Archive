---
title: "filesystem ext2,ext3 and ext4"
date: 2010-04-30
forum: General Help
---

### Post by rnerwein on 2010-04-30
hello
today i run an upgrade and an update on a lucid lynx beta 2. --- got no problems.
but about the filesystems i have some questions because it seems for me that at every system boot
the system will run an fsck. somtimes it's shown up, somtimes not. but in /var/log/messages and in syslog 
i have always following messages ( occured in beta 2 too ).
Apr 30 22:58:49 tschang kernel: [   60.691296] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Apr 30 22:58:49 tschang kernel: [   60.691991] EXT3 FS on sdc7, internal journal
Apr 30 22:58:49 tschang kernel: [   60.691996] EXT3-fs: mounted filesystem with ordered data mode

but first before i continue - here my disk layout:
   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1   *           1        5229    42001911   83  Linux
/dev/sdc2            5230       44552   315861967    5  Erweiterte
/dev/sdc5            5230        5785     4466038+  82  Linux Swap / Solaris
/dev/sdc6            5786       18659   103410373+  83  Linux
/dev/sdc7           18660       31470   102904326   83  Linux
/dev/sdc8           31471       44552   105081133+   7  HPFS/NTFS

and here my filesystem types:
sdc1    --> ext 2 ( ext2 is using for all informations Little Endian - there for it's useable on      
                 different  architectures. ext2 is not the default i know but is this a problem ??  )
    boot.log tells me:
           fsck from util-linux-ng 2.17.2
           /dev/sdc1: clean, 154413/5259264 files, 1388779/10500477 blocks
     but tune2fs always tells me:
           Filesystem state:         [COLOR=Red]not clean[/COLOR]             what's up ????     :confused:
     can't see any message about that filesystem.

 sdc6   ---> always ok (  /dev/sdc6: clean )

 sdc7  ---> ext3  --> not ! in boot.log but have a look at tune2fs.
        ext3:
      Mount count:                       [COLOR=Red]35[/COLOR]     :confused:
      Maximum mount count:       [COLOR=Red]21[/COLOR]    :confused:
this is my problem because those values are seems to be static !  ( note: this partiton is mounted but 
not in use )
and last not least: the drive is an external usb scsi disk.
i think will forward this thread to the development ?

but on the other side lucid lynx is running fine on my box ( karmic koala too )
have a nice day

ciao

---

### Post by rnerwein on 2010-05-01
hi
bump di bump
i think it's a serious problem and i think i know what i am talking about.
ciao

---

### Post by ranch hand on 2010-05-01
First bumping in less than 24 hours is not encouraged.  It makes it look like you have had a reply so many will just skip it.

How about running and posting the results from;

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by rnerwein on 2010-05-06
hi
about ranch hand - i had no problems with any boot stuff and i realy no the offerd script.
1. the ext2 filesytem on /dev/sdc1 always stays at not clean  ( i can live with it ).
2. the Max count and the Max mount count now, after i used tune2fs to correct it , works now as designed.

ciao

---

