---
title: "Mounting fine initially, messes up when I leave."
date: 2010-09-10
forum: General Help
---

### Post by Obesogen on 2010-09-10
I have set up two external hard drives to automount in fstab with the following lines:

/dev/sdb1 /media/DownstairsBackup ntfs-3g rw,auto,user,exec,sync 0 0
/dev/sda1 /media/UpstairsBackup ntfs-3g rw,auto,user,exec,sync 0 0

And right after I restart, all users have permission to read and write, and everything is fine.  However, I have an automated backup utility (BackinTime) installed to back up particular (mounted network) directories every night, but whenever I check up on it the next day, I get the error "Unable to mount ..... Authorization required".  (These network directories are mounted into the local filesystem in fstab as well.)  Oddly enough, if I run BackinTime by hand as the users, it works fine.

Any suggestions as to what is the problem?  I'm running 10.04 LTS.

---

### Post by ubulal on 2010-09-10
Is that message "Unable to mount..." related to the external backups disks or to the network shares that are backed up?

---

