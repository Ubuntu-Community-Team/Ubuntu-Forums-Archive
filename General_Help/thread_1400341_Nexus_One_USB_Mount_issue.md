---
title: "Nexus One USB Mount issue"
date: 2010-02-06
forum: General Help
---

### Post by picklemonkey on 2010-02-06
Hoping there's another Google Nexus One phone owner out there who can help me with this problem!  I'd like to put a few MP3s on it but I'm not able to connect to the phone via USB on my xubuntu box to drop files onto it.   It works on my company computer (Windows XP) so I know it's not a problem with the phone.

I'm still somewhat of an ubuntu noob so it may be a quick fix that I have overlooked/don't understand yet.  Once I plug the phone in to the box, I tell Android to enable USB storage and mount the drive.  Here's the error I get afterwards:
> Failed to mount "3G Removable Volume".

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.


Here's the settings set in Storage Device Manager:

Mountpoint: /media/sdc1
Type: vfat
Options: defaults,users,utf8,mark=007,uid=1000,user


Is there a config change I need to make in Storage Device Manager to make this work, or am I missing something else?

---

### Post by wersdaluv on 2010-02-08
I had to follow this when I rooted [http://forum.xda-developers.com/showthread.php?t=624065&highlight=ubuntu](http://forum.xda-developers.com/showthread.php?t=624065&highlight=ubuntu)

For music, here's "[TIP] Using the Nexus One with Banshee/Rhythmbox on Linux" [http://forum.xda-developers.com/showthread.php?t=624240](http://forum.xda-developers.com/showthread.php?t=624240)

---

### Post by picklemonkey on 2010-02-27
I fixed my issue while troubleshooting a similar issue where I was unable to mount my USB flash stick.  My explanation on how I resolved it is described here:

[http://ubuntuforums.org/showthread.php?p=8891641#post8891641](http://ubuntuforums.org/showthread.php?p=8891641#post8891641)

---

