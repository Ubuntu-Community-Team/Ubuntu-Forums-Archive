---
title: "NFS server fsils to start"
date: 2011-03-19
forum: General Help
---

### Post by 8301 on 2011-03-19
Hello
When I restart the NFS server I end up with this

```
/etc/init.d/nfs-kernel-server restart 
 * Stopping NFS kernel daemon                                                   start-stop-daemon: warning: failed to kill 1609: Operation not permitted
start-stop-daemon: warning: failed to kill 1604: Operation not permitted
start-stop-daemon: warning: failed to kill 1603: Operation not permitted
start-stop-daemon: warning: failed to kill 1602: Operation not permitted
start-stop-daemon: warning: failed to kill 1601: Operation not permitted
start-stop-daemon: warning: failed to kill 1600: Operation not permitted
start-stop-daemon: warning: failed to kill 1599: Operation not permitted
start-stop-daemon: warning: failed to kill 1598: Operation not permitted
start-stop-daemon: warning: failed to kill 1597: Operation not permitted
                                                                         [ OK ]
 * Unexporting directories for NFS kernel daemon...                             exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                         [ OK ]
 * Exporting directories for NFS kernel daemon...                               exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [fail]
```

This is something new to me. Nfs server have worked fine until now.

---

### Post by papibe on 2011-03-19
Are you running that as root? or Are you sudo the restart?
Regards.

---

### Post by 8301 on 2011-03-20
Haha I just got pawned

Ive been running Linux for 4 years... and I didn't see that stupid :D

---

