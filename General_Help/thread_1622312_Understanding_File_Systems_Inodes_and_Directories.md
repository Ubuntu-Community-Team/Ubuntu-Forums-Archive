---
title: "Understanding File Systems: Inodes and Directories"
date: 2010-11-15
forum: General Help
---

### Post by Konbuntu on 2010-11-15
My fellow ubuntu brothers and sisters, I'm having some problem following this tutorial. Is anyone willing to give me some advice? I've been trying to follow the instructions carefully but nothing came out of it...
as you can see im a newbie =/
 
anyways, thanks in advance for all the help i might get from this post =)


1. Locate an Ext2 or Ext3 file system on your machine. Make sure files on the file system
cannot be accessed while working in debugfs. You could consider remounting the file system using 
mount -o remount /yourfilesystem

2. Open a directory on the device that you want to monitor and use the -l command
to display a list of all file names and their inode numbers. Every file has one inode
that contains its complete administration. Make sure that you’ll remember the inode
number later, as you will need it in step 4 of this procedure.

3. Use the debugfs command to access the file system on your device in debug mode. For example, if your file system is /dev/sda1, you would use debugfs /dev/sda1

4. Use the stat command that is available in the file system debugger to show the contents of the inode. When done, use exit to close the debugfs environment.

---

### Post by Konbuntu on 2010-11-15
so far this is where i am at:

```
root@konlah-laptop:/home/konlah# debugfs /dev/sda5
debugfs 1.41.11 (14-Mar-2010)
debugfs:  
```

from here on i don't know what the tutorial is telling me to do

---

### Post by endotherm on 2010-11-15
not sure if you need sudo to run debugfs, but what you are looking at there is a command prompt for the debugfs program. you can enter stuff like 'ls' or 'stat'

for instance:
```

Lucid:~$ sudo debugfs /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs:  stat home

```

brings up:
```

Inode: 130305   Type: directory    Mode:  0755   Flags: 0x80000
Generation: 880737564    Version: 0x00000000:00000001
User:     0   Group:     0   Size: 4096
File ACL: 0    Directory ACL: 0
Links: 2   Blockcount: 8
Fragment:  Address: 0    Number: 0    Size: 0
 ctime: 0x4bfe9ebd:a4587b54 -- Thu May 27 12:33:01 2010
 atime: 0x4bfe9ebd:a4587b54 -- Thu May 27 12:33:01 2010
 mtime: 0x4bfe9ebd:a4587b54 -- Thu May 27 12:33:01 2010
crtime: 0x4bfe9ebd:a4587b54 -- Thu May 27 12:33:01 2010
Size of extra inode fields: 28
EXTENTS:
(0): 532464
(END) 

```

note: to exit the stat page, enter ':q', and to exit debugfs, use 'q'.

---

### Post by Konbuntu on 2010-11-15
thank you! =)

---

