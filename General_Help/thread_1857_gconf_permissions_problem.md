---
title: "gconf permissions problem"
date: 2004-10-23
forum: General Help
---

### Post by butters on 2004-10-23
I just installed on an older machine which mounts a FAT32 volume of mp3s and such.  I chose to mount the FAT32 volume on /home/myuser/music in the partitioner.  When I booted, I realized that the ownership of myuser's home directory was root:root.  I figured out that I needed to add uid=1000,gid=1000 to /etc/fstab to mount the volume with myuser's ownership, then I could do chown -R myuser:myuser . in my home directory.

When I try to start GNOME, it fails trying to create gconf keys for nautilus and gnome-panel, saying that it cannot find a writeable configuration database.  I verified that both ~/.gconf and ~/.gconfd directories exist, are owned by myuser:myuser, and are writeable by owner.  I tried removing and recreating these directories and tried without the FAT32 volume mounted.  Still no dice.  GNOME starts with any mounted volumes iconized on the desktop and a right-click desktop menu, but no panels or background.

Any ideas?

---

### Post by arctic on 2004-10-23
i once had a similar problem with yoper when i tried to install gnome2.8. the reason for the problem was an old gnome-package that collided and some outdated libraries. update all your libraries, maybe this helps.

---

