---
title: "Rhythmbox totem install error too many sym links"
date: 2010-06-05
forum: General Help
---

### Post by nrune on 2010-06-05
Okay gang I can't install anything b/c totem and rhythmbox is messed up. 

```
Unpacking replacement rhythmbox ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 40] Too many levels of symbolic links: '/usr/share/gconf/defaults/ln'
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 40] Too many levels of symbolic links: '/usr/share/gconf/defaults/ln'
dpkg: error processing /var/cache/apt/archives/rhythmbox_0.12.8-0ubuntu5_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 40] Too many levels of symbolic links: '/usr/share/gconf/defaults/ln'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1

```

The upgrade was done from the upgrade manager so I can't figure out what is wrong, and from what I have read it is a circular sym link somewhere.

This has broken my package system I can not remove purge upgrade or install anything new.  some one please help I am clueless.

---

### Post by nrune on 2010-06-05
The issue with the symlinks were related to two files /usr/share/gconf/defaults/ln and /usr/share/gconf/defaults/sudo 

These were links, once I removed them both the system upgraded normally and broken packages were fixed. 

thanks to MTtechnology on #ubuntu.

---

