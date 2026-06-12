---
title: "Can't delete file after crash"
date: 2009-10-04
forum: General Help
---

### Post by brandon88tube on 2009-10-04
I was booting up off a live cd to get a file from my laptop that has been crashing lately and when I was in the middle of copying a file, a 2GB one, it crashed and now I have this file that has a weird foreign character in it that I can't delete. I can't change the name, copy the same file over again etc. I'm at a loss here and I really need to fix this ASAP as this tends to be my backup drive and if its messed up I'm screwed.

---

### Post by DasEi on 2009-10-04
cd into that directory and then use <TAB> to autocomplete, like for
somewirdfilename here :

cd /path/to/file
sudo rm -rf some<TAB>

---

### Post by tuxxy on 2009-10-04
If you can boot the machine then you could enter this command and then navigate to the file and delete as normal.

```
sudo nautilus 
```

This could also be done via terminal and not needing nautilus but you will need to know the specific location of the file.  So if it was at /home/brandon/filename then you would enter this command.

```
sudo rm -rf /home/brandon/filename.tar.gz
```

Be careful running this command make sure you edit the directory exactly to your file.

---

### Post by brandon88tube on 2009-10-04
It seems that it is actually a file with a similar name and it screwed it up. This is just great. I'm going to give those commands a shot and let you know what happens.

---

### Post by brandon88tube on 2009-10-04
Ok, two things.
1. If I open a terminal and do an ls it shows the file that I was copying in black and also the "now" messed up file.

2. When I try any of the commands I get an Input/output error

---

### Post by tuxxy on 2009-10-04
Input/output can be related to hardware problems.  Sounds like you might be getting bad sectors.

---

### Post by brandon88tube on 2009-10-04
Well it did crash a few times during some copies... So what should I do?

---

### Post by DasEi on 2009-10-04
first try a :

sudo e2fsck -p /dev/sdXX  

on the partition, sudo fdisk -l tells you correct identifier.
to do so , boot a live cd and make sure the hd is NOT mounted


second there will be smartmontools, after installing read the manpages for
helthcheck of disk

---

### Post by brandon88tube on 2009-10-04
> **DasEi said:**
> first try a :

sudo e2fsck -p /dev/sdXX  

on the partition, sudo fdisk -l tells you correct identifier.
to do so , boot a live cd and make sure the hd is NOT mounted


second there will be smartmontools, after installing read the manpages for
helthcheck of disk

what is e2fsck? I like to know what it is I'm doing.

---

### Post by DasEi on 2009-10-04
e2fsck is used to check a Linux second  extended  file  system  (ext2fs).   E2fsck  also  supports  ext2    filesystems  containing a journal, which are also sometimes known as ext3 filesystems, by first applying the journal to the filesystem before continuing with normal e2fsck processing.  After  the  journal  has been  applied,  a filesystem will normally be marked as clean.  Hence, for ext3 filesystems, e2fsck will normally run the journal and exit, unless its superblock indicates that further checking is required.

from: man e2fsck

---

### Post by brandon88tube on 2009-10-04
Sorry for the late reply, but its an NTFS drive so what I ended up doing was running a disk check from a Windows machine and that may have fixed the problem.

---

