---
title: "How To Stop updatedb.mlocat? (Stops umount)"
date: 2010-05-09
forum: General Help
---

### Post by JamieKitson on 2010-05-09
How can I stop updatedb.mlocat? It stopped me unmounting my SD card last night.

(kill -9 did not work)

---

### Post by VCoolio on 2010-05-09
Was it running as a cronjob? Check if updatedb is in /etc/cron.daily and either completely disable by 'sudo chmod -x /etc/cron.daily/updatedb' or make it run weekly by moving it into cron.weekly. It's not a bad idea to have it run regularly I guess.

---

### Post by gmargo on 2010-05-09
"updatedb" (aka "updatedb.mlocate") is configured in the file /etc/updatedb.conf.  In that file there is a PRUNEPATHS and a PRUNEFS variable that will allow you to control what directories or file systems are searched by updatedb.  If you are mounting your SD card under /media, then the PRUNEPATHS variable should contain /media.

The 10.04 Lucid default /etc/updatedb.conf contains:
```

PRUNE_BIND_MOUNTS="yes"
# PRUNENAMES=".git .bzr .hg .svn"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 rpc_pipefs afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf fuse.
glusterfs fuse.sshfs ecryptfs fusesmb devtmpfs"


```

---

