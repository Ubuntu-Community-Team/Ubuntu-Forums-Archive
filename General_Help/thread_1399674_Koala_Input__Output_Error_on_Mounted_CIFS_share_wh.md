---
title: "Koala: Input / Output Error on Mounted CIFS share when viewed in Gnome"
date: 2010-02-06
forum: General Help
---

### Post by lleclerc on 2010-02-06
**The problem:**
On a recently installed Koala (9.10) on a home network as well as an office network.

I immediately ran into the problem where a mounted CIFS (smb / samba) share would get an Input/Output error, when contents of the share folders were viewed in Nautilus (file viewer in Gnome).

The below documents the problem, and the fix.

Server machine: Centos 5 (up2dated). Served mounts over CIFS just fine when the desktop below was running Hardy Heron
Desktop machine: Ubuntu Karmic Koala -  fresh install, all security patches updated

**Duplicate the Issue:**
In fstab on desktop:
//192.168.1.11/systemroot /a_mymount cifs username=myself,password=mypassword,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0

boot desktop machine: open /a_mymount in gnome-nautilus, click on a folder in the mount, and immediately get** 'input/output error'** in nautilus, and the mount breaks.

Oddly, accessing the mount through a command line prompt (before it was broken above) seemed to work fine though.

Mounting another mount to the same karmic koala desktop from a vanilla windows 2003 server works fine though. Things only break when I mount from Centos 5 servers.

The problem turns out to be LinuxExtensions to CIFS (which windows does not use, so the windows 2003 server is OK when mounted). Linux extensions in CIFS seems to be brain damaged in Koala, so when the Centos server (which may also be buggy, runs samba 3.0.33-3.15.el5_4.1.i386, the latest update from Centos) misunderstands one of the extensions, CIFS on koala crashes the mount..permanently.

**The fix:**
To fix it, you need to set the flag LinuxExtensionsEnabled in /proc/fs/cifs to 0.
But this can only be done once that directory structure in /proc exists (when CIFS is started). However it seems to be ignored if the mount is already active. So the flag must be set after CIFS is started, but before the mount is mounted.


*in /etc/fstab*
//192.168.1.11/systemroot /a_mymount cifs username=myself,password=mypassword,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0
(I am using UTF8 above to support chinese / Japanese characters..things were just as broken before without this though).


Now we need a hack to automatically set the flag which tells CIFS to not attempt LinuxExtensions (ie. to pretend we are talking to a real windows machine so CIFS doesn't crash when trying to use the extensions) [I].
Add this kludgy hack at the end of /etc/rc.local:[/I]

echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
/bin/mount /a_mymount
exit 0


----

Now reboot. 
Everything now works as expected, mount mounts automatically, in a working and stable condition!

---

### Post by lleclerc on 2010-02-06
..Looks like a recent koala kernel upgrade broke my rc.local fix above. This one fixes it again. 

Notice I removed the '-e' after /bin/sh on the first line, so the script keeps running if an error is hit on any line below (ie. try to umount an already unmounted share)... otherwise, the script will terminate pre-maturely if it hits one of these..


**in /etc/rc.local:**

#!/bin/sh
# no sh -e so we don't die on errors below..

#make sure cifs directory structure in /proc/fs/ is created, do so by mounting once
/bin/mount /a_myshare
#now remove the mount so the echo command below has effect (nothing can be mounted when flag is changed)
/bin/umount /a_myshare
#repeat in case fstab mount also already took place so one isn't leftover)
/bin/umount /a_myshare
#fix the flag to turn off linux extensions
/bin/echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled
#remount the share
/bin/mount /a_myshare
#now everything should work
exit 0

---

