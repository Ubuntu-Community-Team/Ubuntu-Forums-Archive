---
title: "Multiple problems with mounted partitions after upgrade to Lucid Lynx"
date: 2010-05-03
forum: General Help
---

### Post by kumarldh on 2010-05-03
Hi,

I upgraded my installation to Lucid last weekend and encountered various issues. Before I go further here is the system detail.
I dual boot with windows xp and ubuntu
80 Gig drive divided into
40G c drive windows
30G d drive windows
2G swap
8G /
500MB /boot

windows partition were loaded in Karmic with following fstab
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  defaults                                               0  0  
# / was on /dev/sda8 during installation
UUID=44f537a7-1fb3-4063-8bd2-f6a0742117da  /            ext3  relatime,errors=remount-ro                             0  1  
# /boot was on /dev/sda7 during installation
UUID=0039115d-0f9e-4386-878b-ab20a8d2ddb6  /boot        ext3  relatime                                               0  2  
# swap was on /dev/sda6 during installation
UUID=5acdc34e-ddfe-42d4-8f63-ed940612618d  none         swap  sw                                                     0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,group=developer,users,exec,umask=000     0  0  
/dev/sda5                                 /media/sda5  ntfs  nls=iso8859-1,group=developer,users,exec,umask=000  0  0  

```
I have a Apache set up for which all doc root is set to /media/sda5/lamp/www where sda5/lamp/www is d:/lamp/www on windows. There are projects under www which are mapped to svn. The evolution data folder is basically linked to d:/mail/.evolution and hence all my important data is either in /media/sda2 or /media/sda5.
Now the problems
a) evolution says /media/sda5 is readonly
b) Apache cant write to log files in /media/sda5
c) svn says ```
svn: Can't set permissions on '.svn/tempfile.4.tmp': Operation not permitted
```
d) I lost chrome launcher from panel
e) firefox profile was corrupted
Before I upgraded everything was working fine. I can live w/out firefox profile and chrome launcher but point a, b and c are driving me insane and believe me or not I have spent whole day googling and irc. Can some one help me out?

---

### Post by kumarldh on 2010-05-04
Moderators can mark it as solved. The problem was solved after installing NTFS-3G. :-)

---

