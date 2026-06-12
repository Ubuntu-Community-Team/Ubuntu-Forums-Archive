---
title: "Mount Drive without Showing on Desktop"
date: 2010-07-25
forum: General Help
---

### Post by lewisforlife on 2010-07-25
I have an Ubuntu 8.04 machine, I have a NFS drive being mounted when the system starts up.  The entry in /etc/fstab looks like:

```

server:/srv/Pictures     /mnt/share     nfs     rw,hard,intr     0 0

```

The drive is mounting fine, but I would really like it if the icon did not show up on the desktop for this drive.  Is there anyway to keep it from showing?

---

### Post by geoffjay on 2010-07-25
Open gconf-editor and browse to /apps/nautilus/preferences/desktop and uncheck volumes_visible

---

### Post by Morbius1 on 2010-07-25
I don't know anything about NFS but I'm rather surprised it's not following the normal rules concerning mountpoints.

If this were a standard mountpoint for an internal partition, a mount point of /home/username/share or /media/share would produce a mount icon on the desktop. A mountpoint at /mnt/share or /share would not.

---

### Post by lewisforlife on 2010-07-25
Oops,  I actually was mounting it in the /home directory.  For some reason I was thinking that I was mounting somewhere else.  This fixed the issue.  Thanks.

---

