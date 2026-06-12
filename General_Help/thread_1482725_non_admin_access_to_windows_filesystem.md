---
title: "non admin access to windows filesystem"
date: 2010-05-13
forum: General Help
---

### Post by wallywally on 2010-05-13
I'm dual booting XP and UNR and I want to give users access to the windows file-systems but not to admin of Ubuntu.

At present I have given them a Desktop user account but that doesn't allow access to the XP file-systems.  The only way I can see to enable that is to go to Advanced User Setting and allow them to Administer the System - which I don't want to do.

Any suggestions?

---

### Post by quixote on 2010-05-14
You could allow any user to mount the windows partition.  The user who mounts a partition has all permissions that aren't excluded.  Since Windows in a Linux context has 777 permissions, any user could read, write, or execute any file.  You can, if need be, limit it to specific users.

You have to make the dir which will be the mountpoint first.  Here, I'm calling it /mnt/win.  You can find out the UUID of the windows partition by using "sudo blkid" (without quotes).

In /etc/fstab add the options in bold to the line that allows mounting of the windows partition:```
#Windows 7 *(or any descriptor you like)*
UUID=*windows-partition-number* /mnt/win   ntfs   noauto,**rw**,**users,noexec** 	0	0

```Instead of "users" one could have uid=1001, for instance, and then (besides root) only the user whose id is 1001 will be able to mount the drive.

That's just as an example.  There's a full explanation [here]("https://help.ubuntu.com/community/Fstab"). You might prefer other options than the ones above, eg "auto" instead of "noauto" to have the drive mounted at login.

---

