---
title: "rsync from Ubuntu to VirtualBox Ubuntu Guest SharedFolders in Windows 2003"
date: 2009-12-29
forum: General Help
---

### Post by DaleEMoore on 2009-12-29
Should I expect rsync to work from Ubuntu to VirtualBox Ubuntu Guest 
SharedFolders on Windows Server 2003? Over the last 25 days I've 
rsynced about 500 GB but I have to nursemaid it, restarting it 
frequently after this type of error:

2009/12/29 12:55:45 [9195] KFS/web/mojoPortal/mojoPortal/Data/pix/3o/
2009/12/29 12:57:47 [9195] rsync: opendir "/KFS/web/mojoPortal/mojoPortal/Data/pix/3o" (in All) failed: Interrupted system call (4)
2009/12/29 12:57:47 [9195] rsync: connection unexpectedly closed (413 bytes received so far) [generator]
2009/12/29 12:57:47 [9195] rsync error: error in rsync protocol data stream (code 12) at io.c(600) [generator=3.0.6]

Once the rsync failure occurs I can no longer ssh into the Ubuntu Guest.
root@SaveSeth:~/bin# ssh -Y bubu
Connection closed by 192.168.1.8

Any sugguestions are very much appreciated,
Dale E. Moore

---

