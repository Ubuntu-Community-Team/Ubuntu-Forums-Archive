---
title: "jfs2 mounts"
date: 2010-11-09
forum: General Help
---

### Post by mprodman on 2010-11-09
How do I mount a nfs jfs2 filesystem from a aix unix platform to ubuntu client

When I issue mount aixbox:/jfs2fs  /mnt  on the ubuntu box I get...

mount: wrong fs type, bad option, bad superblock on aixbox:/jfs2fs,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Is there a package that allows ubuntu to mount jfs2 filesystems from other unix boxes?

---

### Post by mprodman on 2010-11-09
Ended up needing nfs-common pkg and then using nfsvers=2 option with the mount command
mount -o nfsvers=2 aixbox:/jfs2fs /mnt

---

