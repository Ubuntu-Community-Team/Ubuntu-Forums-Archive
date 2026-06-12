---
title: "NTFS Partition Question"
date: 2012-03-13
forum: General Help
---

### Post by rigel4 on 2012-03-13
I have Ubuntu 11.10 and Windows 7 dual boot.
The Windows 7 I use for a couple of games I like and Ubuntu
for everything else.

I sorted out all my data into manageable folders from various external drives and copied it on to the Windows 7 data partition.

My question, is there a way so that Ubuntu can access this data, so that I don't need two sets of the same data. Seems like it should be do-able, I just don't know how.
If any one can help.. I'd be grateful.

Thanks

---

### Post by idoitprone on 2012-03-13
```
sudo apt-get install ntfs-3g
```
rsync might be useful while copying files that have minor changes

now ubuntu can write onto the window partition

---

### Post by rigel4 on 2012-03-13
> **idoitprone said:**
> ```
sudo apt-get install ntfs-3g
```rsync might be useful while copying files that have minor changes

now ubuntu can write onto the window partition

Aw thanks , I knew it would be possible.
Also knew one of you good people would know the 
answer. 

Cheers :)

---

### Post by flemur13013 on 2012-03-13
What idoitprone said.

FWIW, here's my /etc/fstab entry:
(# = commented out)

```
# LABEL=NTFS                                    /ntfs           ntfs-3g defaults        0       0
UUID=01xxxxxxxxxxxC00                           /ntfs           ntfs-3g defaults        0       0
#
```(But first do this before mounting, which'll happen at boot): 
$ sudo mkdir /ntfs (or whatever name)
$ sudo chown yourusername /ntfs

Ownership, read, write, all no problem.  (g)rsync works fine for backup.

Backup first if possible...!

---

### Post by oldfred on 2012-03-13
Some more info if interested:

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

A couple of more examples of fstab entries:

UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data2 ntfs defaults,uid=1000,windows_names,umask=000 0 0

---

