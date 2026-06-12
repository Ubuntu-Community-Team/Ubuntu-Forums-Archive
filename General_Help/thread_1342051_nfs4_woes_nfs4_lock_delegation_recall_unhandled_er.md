---
title: "nfs4 woes: nfs4_lock_delegation_recall: unhandled error -10018."
date: 2009-11-30
forum: General Help
---

### Post by ajmcello on 2009-11-30
Any idea what's going on here? Using 9.10 with latest updates. Remote NFS server is opensolaris ZFS.

These are my fstab options:

rw,rsize=8192,wsize=8192,timeo=14,intr,sec=sys,bg,ac,_netdev,hard   

Nov 29 07:37:27 ssp1 kernel: [280935.737197] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:27 ssp1 kernel: [280935.739378] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:27 ssp1 kernel: [280935.741713] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:27 ssp1 kernel: [280935.743895] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:36 ssp1 kernel: [280944.574920] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:36 ssp1 kernel: [280944.577650] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:36 ssp1 kernel: [280944.580365] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:36 ssp1 kernel: [280944.582396] nfs4_lock_delegation_recall: unhandled error -10018.
Nov 29 07:37:36 ssp1 kernel: [280944.584608] nfs4_lock_delegation_recall: unhandled error -10018.

---

