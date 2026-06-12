---
title: "DD  cloning disc &gt;&gt;  partition , file system broken"
date: 2011-07-18
forum: General Help
---

### Post by Ordes on 2011-07-18
First time i am using DD. Tried DD & DDRESCUE so far. I want to clone my sda to sdb for backup. They are both the same size.
>> sda has: sda1, sda2, sda3, sda4;
>> sda1+2 is ntfs windows
>> sda3 is ext4 ubuntu /
>> sda4 is swap

after cloning i cannot mount sdb. and get the error "wrong fs type, bad option, bad superblock"
when looking into gparted i get a invalid argument error, for sda1 the ntfs is invalid.
sda1-3 are all invalid only sda4 (swap) is ok.

for ddrescue i used $ ddrescue -v /dev/sda /dev/sdb;
for dd $ dd if=/dev/sda of=/dev/sdb;

any idas why this keeps happening, or how to solve it ?

txs

---

### Post by oldfred on 2011-07-18
If using dd you cannot have both drives plugged in at the same time. It is an exact copy & they will have same UUIDs and system cannot tell one from the other. 

If you had issues before the copy then the copy will have exactly the same issue.

---

### Post by Ordes on 2011-07-18
No issues on sda. I just want to keep a clone of my system drive.

When you say not plugged in at the same time. You mean after the cloning is done. they cannot be plugged in together as they share the same UUID?
So in this case the only way to check if my clone worked or not would be to unplug sda.

Question on the side:
If you have a different application tipp for making clone backups, i am glad to hear.

TXS

---

### Post by oldfred on 2011-07-19
I am not a full clone person. I install several versions of Ubuntu. I keep each old version and install the newest to another partition. Then use my backups to restore my configuration.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

Since install and restore data is only about an hour I do not see clone as really the best way. You cannot easily mount clone regularly and copy changes over. I prefer rsync my unique data only.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Ordes on 2011-07-26
txs ...

yes the problem was the simultanious mounted HDDs...

so for backing up i decided to use rsync and tar .. ^^

---

### Post by SlugSlug on 2011-07-26
clonezilla is good

---

