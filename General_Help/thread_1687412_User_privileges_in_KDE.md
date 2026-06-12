---
title: "User privileges in KDE"
date: 2011-02-13
forum: General Help
---

### Post by Datweakfreak on 2011-02-13
I have one drive for Kubuntu and 4 other NTFS drives. When I'm using Ubuntu Desktop Environment (GNOME), I seem to be able to delete files, create new folders, files etc, in all the NTFS drives. That is, I have full permissions to make changes in the NTFS drives. But when I switch to KDE, this isn't possible. Options like rename, delete, cut, etc, aren't working, they aren't highlighted. 

Is there any way I can have full permissions to modify NTFS drives in KDE?

---

### Post by Datweakfreak on 2011-02-13
Sorry for the double post, but I just found that I don't have user permissions in GNOME too. I can't even download stuff to the NTFS drives. This must have happened probably after I installed Kubuntu, because this problem wasn't there when I was using just GNOME.

---

### Post by WorMzy on 2011-02-13
Permissions on NTFS partitions depend on how you mount them. On GNOME, mounting an NTFS partition by using the places menu will mount it with the user's UID, GID and the umask of 775 (I think). Presumably KDE mounts the partition as root, with the same umask (which is why you can see the contents of the drive, but cannot write to it).

You can force both DE's to mount it the same way by creating an entry in /etc/fstab. See this tutorial for more info on how to do that: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

