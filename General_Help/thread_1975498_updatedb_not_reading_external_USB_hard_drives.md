---
title: "updatedb not reading external USB hard drives"
date: 2012-05-07
forum: General Help
---

### Post by Silvernail on 2012-05-07
After my upgrade to Oneiric, I noticed the 'locate' was not accessing either of my 2 USB external hard drives. Research led me to '/etc/updatedb.conf' where I removed '/media' in 'PRUNEPATHS=". That corrected the problem.

The config file is still as I edited it.
> 
PRUNE_BIND_MOUNTS="no"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /home/.ecryptfs"
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.glusterfs fuse.sshfs curlftpfs ecryptfs fusesmb devtmpfs"


This new problem started after the big kernal upgrade a day or two ago, 'updatedb' is again NOT reading either of my external drives.

Is there somewhere else that 'updatedb' gets its configuration data?

Dave

---

