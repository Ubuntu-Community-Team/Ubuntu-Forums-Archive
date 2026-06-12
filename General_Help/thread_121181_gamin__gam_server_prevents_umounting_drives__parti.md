---
title: "gamin / gam_server prevents umounting drives / partitions even as root"
date: 2006-01-24
forum: General Help
---

### Post by ender42 on 2006-01-24
I've kept getting errors when trying to umount a drive or a partition, after I have closed all their windows. Even from the commandline, and even as root.

root@machine:~# umount /dev/hdb1
umount: /mountpoint: device is busy
umount: /mountpoint: device is busy
root@machine:~#

I've used 'fuser /mountpoint' and 'ps aux | grep psnumberreturned' and found it to be /usr/lib/gamin/gam_server .

Suppossedly this was fixed in 0.0.25 according to:
[http://bugzilla.gnome.org/show_bug.cgi?id=168175](http://bugzilla.gnome.org/show_bug.cgi?id=168175)

apt-get show gamin
Description: File and directory monitoring system
Gamin is a file and directory monitoring system defined to
be a subset of the FAM (File Alteration Monitor) system.
Filename: pool/main/g/gamin/gamin_0.0.26-0ubuntu3_i386.deb


The debian package appears to *NOT* be the most current version:
[http://www.gnome.org/~veillard/gamin/sources/gamin-0.1.7.tar.gz](http://www.gnome.org/~veillard/gamin/sources/gamin-0.1.7.tar.gz)

I'd like to know how to tickle the gam_server into releasing the drive so that I can umount it. Hints on repackaging the most current gamin into Debian (and boy, what will that break on me?)

I had luck killing the process once, but I have no idea if that's causing further errors (I've had more issues since then). Do I need to restart gamin/gam_server?


[http://lists.centos.org/pipermail/centos/2005-May/006610.html](http://lists.centos.org/pipermail/centos/2005-May/006610.html)
recommends what I've been doing, find the process id via fuser and kill it. 

[http://www.slackercentral.com/sckb/index.php/Linux_Tips_for_New_Users](http://www.slackercentral.com/sckb/index.php/Linux_Tips_for_New_Users)
suggests: 'killall -9 gam_server && umount /my/mountpoint'

I finally got this forum to work (after many days of trying):
[http://ubuntuforums.org/printthread.php?t=57855](http://ubuntuforums.org/printthread.php?t=57855)
But no real information there... other than use 'lsof' to find wha'ts holding the file open.



It appears to only occur when I'm using the GUI to access the drive/partition in question. When I copied files via commandline from a USB drive to the new HD, I didn't have an issue.

Now, if I could just get 'apt-get -u upgrade' to not automatically mount my partitions and drives and open GUI'd folders to them, then I'd have a work-around...

---

