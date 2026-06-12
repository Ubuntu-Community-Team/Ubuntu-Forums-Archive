---
title: "Nautilus Running as Root"
date: 2012-01-09
forum: General Help
---

### Post by sceptre0 on 2012-01-09
I have a weird problem with my Ubuntu 11.04 installation.  It seems that Nautilus is running as root.  I don't know exactly what triggered this.  My username is displayed correctly in the upper right corner of the screen so I know the correct user is logged in, but Nautilus seems to be running as root (or some other unknown user).  The system has the following symptoms.
* Files copied or extracted in Nautilus are owned by root
* The root desktop is displayed
* Installed Wine applications do not populate in the Applications menu, but do show up on root desktop
* Opening my user home folder requires a root password be entered
* Dropbox does not have access to the Dropbox folder

My fstab file is below.  Not sure if it is relevant to this problem.  I may have been messing with it when the problem started.

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                               0  0  

# / was on /dev/sda1 during installation
UUID=48c8edf9-f238-41d3-94a8-e9b6209cb488  /              ext4         errors=remount-ro,user_xattr                                      0  1  

# swap was on /dev/sda5 during installation
UUID=9ed2aa36-3079-4c8d-aa67-72c3cf3b99f2  none           swap         sw                                                     0  0  

# Media
##/dev/sdb1                                  /media/Media   ntfs         nls=iso8859-1,users,umask=000,user,owner,uid=sceptre0  0  0
UUID=B880E7A880E76AF8                      /media/Media   ntfs         nls=iso8859-1,users,umask=000,user,owner,uid=sceptre0  0  0    

# RAID5
##/dev/md0p1                                /media/RAID5   ext4         rw,auto,user                                           0  1
#UUID=7fc519dd-f049-470a-a06d-e497bcc288ba   /media/RAID5   ext4         rw,auto,user                                           0  1

```

At this point, I don't know if this is a Nautilus problem or a problem with the system.  Any help would be much appreciated.  Thanks.

---

### Post by sceptre0 on 2012-01-11
Solved
[http://ubuntuforums.org/showthread.php?t=1754435](http://ubuntuforums.org/showthread.php?t=1754435)

---

