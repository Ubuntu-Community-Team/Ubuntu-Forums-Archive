---
title: "Access Is Denied setting folder security from Windows"
date: 2010-12-28
forum: General Help
---

### Post by ForrestDean on 2010-12-28
Is there a way to set the permissions on files and folders from a Windows server or workstation?  The partition is NTFS and is mounted as NTFS, but whenever I right click on a file or folder on the Ubuntu server from a Windows computer and try to change the permissions I get "Access Is Denied".

---

### Post by oldfred on 2010-12-28
NTFS does not support Linux permissions and ownership. So you cannot set them, nor change them. You get whatever the default is as you have mounted the partition.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by endotherm on 2010-12-28
just to clarify, the files are on an ubuntu box being shared over samba, and you are trying to change the permissions of those files from a windows  workstation, correct? 
you cannot change the share or filesystem permissions from a remote workstation, so you will have to change them from a console on the server. for NTFS you modify the permissions in the share mounting as oldfred mentioned, and for share permissions you modify samba. remember, your resultant set of permissions is the more restrictive set of the two, so usually you set your share permissions to be loose, and your filesystem permissions to be tighter. 
[]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

---

### Post by ForrestDean on 2010-12-28
OK thanks.  That's pretty much what I needed to know. :)

---

