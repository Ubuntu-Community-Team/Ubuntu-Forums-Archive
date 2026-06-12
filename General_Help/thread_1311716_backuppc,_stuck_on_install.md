---
title: "backuppc, stuck on install"
date: 2009-11-02
forum: General Help
---

### Post by simon82 on 2009-11-02
Trying to install backuppc, getting a problem as u can below.
Any good hints? 




 * Starting backuppc...                                                                                          2009-11-02 22:53:00 Can't create a test hardlink between a file in /var/lib/backuppc/pc and /var/lib/backuppc/cpool.  Either these are different file systems, or this file system doesn't support hardlinks, or these directories don't exist, or there is a permissions problem, or the file system is out of inodes or full.  Use df, df -i, and ls -ld to check each of these possibilities. Quitting...
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: fel vid hantering av backuppc (--configure):
 underprocess installerade post-installation-skript gav felkod 1
Fel uppstod vid hantering:
 backuppc
E: Sub-process /usr/bin/dpkg returned an error code (1)
server@server-desktop:/var/lib$ cd backuppc/
server@server-desktop:/var/lib/backuppc$ ls -l
total 16
drwxr-xr-x 2 root root 4096 2009-10-05 22:35 cpool
drwxr-xr-x 2 root root 4096 2009-10-05 22:35 pc
drwxr-xr-x 2 root root 4096 2009-10-05 22:35 pool
drwxr-xr-x 2 root root 4096 2009-10-05 22:35 trash
server@server-desktop:/var/lib/backuppc$

---

### Post by rollback on 2009-11-05
looks like a permission problem. the folders are owned by root.

on my system, it's owned by backuppc.

---

