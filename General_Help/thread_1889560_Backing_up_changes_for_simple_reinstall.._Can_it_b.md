---
title: "Backing up changes for simple reinstall.. Can it be done?"
date: 2011-12-01
forum: General Help
---

### Post by jaylc005 on 2011-12-01
Hey guys, I was wondering if anyone could give me some advice.

How easy is it to preserve my 10.10 install once I have set it up to a certain way, my laptop requires a few changes for SSD, backlight issue and aircrack issue, and while I have created a fast method of setting all these things up quickly from a fresh install, I would still prefere to be able to get myself back to a state of which I have already customized my install, for instance the set up of docky, wallpapers, frequently used programs and stuff, I guess what I am trying to achieve is comparable to one of those lame HP restore disks, or the like..

I was thinking an image, but I need for the image installer to be part of the disc and bootable, not relying on any usb drives or other swap disks if possible..

Also, what are my size limits, I guess I can get my SSD up to around 4gb full of customizations before I had to make an ISO, that could mean a lot of helpful changes which would usually take a long time to install individually.. There would need to be room for the image manager and boot stuff but that would be kbs.. 

Any suggestions guys?

Thanks
Jay

---

### Post by oldfred on 2011-12-01
Some like a full image restore, but it gets outdated quickly. I prefer to just backup the things that change and do a reinstall. I then can use that same info on a new install, but often do not copy all of it over. One disadvantage of Linux is too many choices.:)

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
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I used this and modified it for my use.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Some files to exclude:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by Bobhuber on 2011-12-01
For some reason I see very few posts on a very good program for backup.
Fsarchiver allows you to backup a mounted partition and is fast and very reliable.
Here's a simple bash script I use daily to backup my system (sdb1) to a second partition (sdb2).
I can't even count the number of times I've restored using it LOL
```
#!/bin/bash
mount -t ext4 /dev/sdb2 /mnt
mfile=$(date +%Y-%m-%d-ONERIC).fsa
echo $mfile
fsarchiver -v -o -A -j4 savefs /mnt/$mfile /dev/sdb1
```

---

### Post by jaylc005 on 2011-12-02
Wow, thanks for the information both you guys, I cant really comment right now, I will have to dig down into every link provided, plus the fsarchive method too, i have fluffed gnome now so will see how long my reinstall plan takes just to get me to a baseline level of config to my standards, only really patching wifi and stuff, but still it takes a while, the fsarchive method sounds really good apart from the fact my machine isnt running 24/7, but that will be nice for the server, this is for my laptop, but I could still make use, just without the daily occurrence.

Thanks again chaps.
jay

---

