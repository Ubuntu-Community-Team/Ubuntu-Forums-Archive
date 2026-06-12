---
title: "Need to retrive deleted data"
date: 2009-12-25
forum: General Help
---

### Post by dink123 on 2009-12-25
Hi all,

this is an experiment to understand the file systems. 
i have created a virtual file system (ext3) using loop back and have mounted it successfully. 
what i want to try is....create a simple text file(with some data inside) and then remove that text file using the rm command. after removing i need to somehow access those data which i entered earlier into the file and want to get them back.

Any ideas about this???
Thank You.

---

### Post by dink123 on 2009-12-25
> 
[COLOR=#333333]#debugfs /dev/sdaX          (change X appropriate)
[/COLOR][COLOR=#333333]debugfs:lsdel[/COLOR]

it'll list the deleted inodes:
[COLOR=#333333]Inode Owner Mode Size Blocks Time deleted

[/COLOR][COLOR=#333333]dump inocdeNo /home/directory/path           (inodeNo is the node you want to retrive.)[/COLOR]


Hi,  i found that debugfs can only be used to recover files from a ext2 file system 'cause in a ext3 file system on deletion  it zeros out the block pointers in the inode. 

so i will have to convert my disk to a ext2 file system.

---

