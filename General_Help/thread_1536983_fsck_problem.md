---
title: "fsck problem"
date: 2010-07-22
forum: General Help
---

### Post by tzinkoi on 2010-07-22
im having a problem loading my ubunto and this will appear if i will open my system...
and how to solve this problem??? need help



Checking drive /dev/sdal:50% ( stage 1/5, 109/150 )
  /dev/sdal: Inodes that were part of a corrupted orphan linked list found
  /dev/sdal: UNEXPECTED INCONSINSTENCY; RUN fsck MANUALLY
  ( i.e without &#8211;a or &#8211;p options )
  Fsck died with exit starts 4
  Checking drive/dev/sdal : 55%  ( stage 1/5, 118/150 )                                  [ [COLOR=red]failed [/COLOR]]
  
  [COLOR=red]*[/COLOR] An automatic file system check ( fsck ) of the root filesystem failed.
  A manual fsck must be performed, then the system started.
  The fsck should be performed in maintenance mode with the root filesystem mounted in read-mode
   
  [COLOR=#f79646]* [/COLOR]The root filesystem is currently mounted in read-only mode.
  A maintenance shell will now be started.
  After performing system maintenance, press CONTROL &#8211;D
  to terminate the maintenance shell and restart the system.
  bash: no job control in this shell
  root@database &#8211; server : `#

---

### Post by SkyNet2029 on 2010-07-23
> [COLOR=red]*[/COLOR] An automatic file system check ( fsck ) of  the root filesystem failed.
  A manual fsck must be performed, then the system started.
  The fsck should be performed in maintenance mode with the root  filesystem mounted in read-mode 

is telling you that the automatic file system check has failed.
You need to boot into single user mode and manually run the file system checks.
Once the file system check has completed its run, you must reboot your system.

you can do this like so:
Boot into single user mode
login as root
do this:

```
#fsck -a
```

reboot once it is complete.

---

