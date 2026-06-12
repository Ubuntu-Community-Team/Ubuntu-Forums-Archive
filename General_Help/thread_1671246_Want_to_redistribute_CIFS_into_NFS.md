---
title: "Want to redistribute CIFS into NFS"
date: 2011-01-19
forum: General Help
---

### Post by CalSciTim on 2011-01-19
The reasons are long, but I want to mount an external cifs share and reshare it using NFS.  I've gotten as far as mounting the CIFS share using SAMBA, but I get an error when trying to share that directory with NFS-Kernel-Server.

  When I restart the NFS-Kernel-Server, I get the following error.

 >  *Exporting Directories for NFS kernel daemon...
  exportfs: Warning: /share does not support NFS export

  Is this something that is possible?  If so, does anyone have any suggestions. 

If not, does anyone know why this definitely won't work?

 Thanks!

---

### Post by SeijiSensei on 2011-01-19
There are a couple of reasons.  First, CIFS, like NTFS and other Windows file systems, doesn't support Unix primitives like permissions and locks.  The file system it presents to the operating system isn't one that can be exported by NFS because it doesn't look like Unix.

There's also a security issue that applies to re-exports.  Suppose you have a file system for which you have rights, and you re-export it to another system. That system won't be able to enforce rights or locks on the original export.  nfs-kernel-server, for instance, won't re-export an NFS mount. 

In a couple of places I saw mention that you might be able to do this with a user-level NFS server.

---

