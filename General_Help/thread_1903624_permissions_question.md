---
title: "permissions question"
date: 2012-01-02
forum: General Help
---

### Post by crutch145 on 2012-01-02
I have my backup drive (spare hard drive) automatically mounted to /media/backup upon system bootup. I only want my user account to have access to the /media/backup directory. I created a user account called guest. However, when I log in as guest, it has full access to /media/backup. I do not want guest to have access to this directory, because it contains a backup of all my personal documents. Root is the owner of /media/backup. What terminal command do I need to use deny access to the guest user account?  I imagine the command will begin with "sudo chmod" but I am not sure what should follow.

Thanks,

Justin

---

### Post by chipbuster on 2012-01-02
chmod 700 will lock it down to everyone but the owner (root).

chmod 770 will lock it down to everyone but the owner and whoever's in the group.

The big question is: is guest in the same group as your main account? If it is, there's a way to change it, but I don't know what it is.

---

### Post by crutch145 on 2012-01-03
The group for /media/backup is root.  There are no user accounts that are a member of this group.  I do have a group called crutch, and guest is not a member of that group.  I will chown and chmod to crutch.

---

### Post by claracc on 2012-01-04
You can do the necessary permissions adjustments through the gui, deploying the menu system, administration, users and groups.

I think this is a safer way.

---

### Post by crutch145 on 2012-01-04
Thanks to altair4 from Linux Mint forums, I resolved it like this:

added this line to the end of /etc/fstab - UUID=0868FA6A68FA5642 /media/BACKUP ntfs defaults,nls=utf8,uid=1000,umask=077,windows_names 0 0

Then manually unmounted BACKUP drive and ran the following command: sudo mount -a

---

