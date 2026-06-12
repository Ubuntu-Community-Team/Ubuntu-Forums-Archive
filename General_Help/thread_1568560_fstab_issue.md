---
title: "fstab issue"
date: 2010-09-05
forum: General Help
---

### Post by Coder68 on 2010-09-05
I working through the book "The practical guide to Ubuntu Linux ed 2 (8.04/8.10) and have come upon an issue. (There are several already in this book.)

The book has you run the following commands for access control lists. 

sudo aptitude install acl - succeeded

grep home /etc/fstab 

Which is supposed to give you the line that has home it in. It does not.
(LABEL=/home     /home            ext3          defaults,acl                  1,2) home does not exist in the default fstab file.

Adding in the authors line gives an error - error in line x. 
I went out and found some how to's and followed them, but I still get an error. It is a different error though.

Here is my new fstab file: (What I added is in blue.)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=476b2555-a755-46b1-8e72-0d4b1e2c4b3c /               ext3    relatime,errors=remount-ro 0       1
[COLOR=Blue]LABEL=c68 /home/coder68 ext3 default,acl 1 2
[COLOR=Black]# /dev/sda5[/COLOR][/COLOR]
UUID=40a35c9a-ad55-4b87-a5d4-08af138c5262 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```using sudo mount LABEL=c68 gives an error that c68 does not exist. I have tried giving different LABEL=someword, but that has not helped either - same error.

What am I doing wrong?

Any GOOD book suggestions out there?

---

### Post by drs305 on 2010-09-05
First, do you *have* a separate /home partition? /home will only be listed in fstab if you have a separate /home partition, which is not the default setup.

If you don't know, you can list your partitions with:
```
sudo blkid
```

As far as the "C68", you must label a partition "c68". Have you done that? You can add labels via gparted, disk utility (System, Administration, Disk Utility) or via the command line, *but your /home entry in fstab isn't correct if you are trying to make that your home partition, so remove it until things get sorted out*.

Give us a better idea of what you are trying to do - for instance: make a separate /home partition, make a new folder for storing data, etc.

---

