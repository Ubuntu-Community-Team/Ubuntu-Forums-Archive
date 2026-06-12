---
title: "nfs-common and  nfs-kernel-server cannot be removed/installed apt-get useless"
date: 2010-05-27
forum: General Help
---

### Post by originalsurfmex on 2010-05-27
i tried installing nfs-common and nfs-kernel server
(im using xubuntu) and they never finished installing, reported errors running the configuration script, now i end up with this and i cannot use apt-get or apt at all.

Errors were encountered while processing:  nfs-common  nfs-kernel-server

i tried to reconfigure -a and a few other things...tried starting portmap...what else can i do?

---

### Post by OkoSanto on 2010-06-10
I might have had a similar problem.  I could not finish the installation of nfs-kernel-server because it always got stuck at ```
 Setting up nfs-kernel-server (1:1.2.0-4ubuntu4) ...
 * Stopping NFS kernel daemon                                                                                 [ OK ] 
 * Unexporting directories for NFS kernel daemon...                                                           [ OK ] 
 * Exporting directories for NFS kernel daemon...                                                             [ OK ] 
 * Starting NFS kernel daemon
```

The problem is/was that the portmap program was not started automatically.  I could solve the problem for now by starting it manually, ("sudo service portmap start") and then running dpkg --configure -a, to clean up the failed install.

The remaining problem is, to make ubuntu start the portmap service at boot time, in stead of having to start it manually each time...

---

