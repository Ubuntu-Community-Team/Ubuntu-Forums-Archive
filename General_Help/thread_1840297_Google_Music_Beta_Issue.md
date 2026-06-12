---
title: "Google Music Beta Issue"
date: 2011-09-07
forum: General Help
---

### Post by spielnicht on 2011-09-07
This is such a strange issue. I had Google Music Beta installed on 11.04 64bit and it worked perfectly, found all my MP3s on a mounted network drive and uploaded with no issue. However, I've since rebuilt my machine with 11.04 32bit (couldn't get my Canon drivers working on 64bit), but Google Music fails to find any files (mp3s) on the same exact mounted network drive. Any attempt just says "There are no music files available in the folders you are sharing".

Here is how I'm mounting the drive if it makes a difference:

//192.168.1.102/Music /media/Music cifs auto,iocharset=utf8,uid=*****,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

If I add a local folder, Google Music does see all the MP3s under it.

Help.

---

### Post by djja3x on 2011-12-14
Spielnicht, did you ever resolve your issue?  I'm having the same problem under 10.04 32bit.  Thanks.

---

### Post by beaton on 2012-01-16
Try adding the "noserverino" option to your mount, as described in the [mount.cifs]("http://linux.die.net/man/8/mount.cifs") man page.

In my case, this fixed the problem.  You can double check the root cause by looking in ~/.config/google-musicmanager/config.log.  In my case, it showed output like this:


2012-01-15 12:37:05,182 -0800 ERROR TId 0xb32c0b70 errno 75 calling lstat() on file <blah> [QuickFileCounter.cpp:199 QuickFileCounter::scanDirectory()]

If you see that "errno 75", you're running into a bug in the google music manager beta code; it doesn't support file systems that use 64 bit inodes.  The noserverino mount option can be used to work around this kind of bug.  This will break certain *other* applications that use inode numbers to detect hard links, so do be cautious before you enable noserverino.

---

