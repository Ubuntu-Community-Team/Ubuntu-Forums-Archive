---
title: "mount dir using smbfs to windows share.  Can't write to file. Permission Denied??"
date: 2010-06-19
forum: General Help
---

### Post by roadrawts on 2010-06-19
Mount a Windows share where my user account has admin privileges.  All permissions granted to the share on the windows pc side.

Mount statement is as follows:

sudo mount -t smbfs -o username=johndoe //winname/directoryname  /mnt/tmp/

Share mounts ok but does not let me create or write to an existing file.  When I select Properties on the directory it says that permissions are unknown on the share looking at it from Ubuntu.

This worked in Ubuntu 9.04 but not in 9.10.  

Any ideas on how to make it work again?

---

### Post by megamandos on 2010-06-19
Ok, so the share is one a windows box? Then check "share permissions" AND "ntfs permissions". they are two separate sets of permissions under windows. Right click on the folder being shared and click properties: ntfs permissions is under the "security" tab and share permissions is under the "sharing" tab.

---

### Post by roadrawts on 2010-06-19
I'm using an older version of XP, I guess, because I don't have a security tab under properties, only permissions.  Each time I look at properties, the Read-Only box has a green block in it, not checked.  I clear that and 'Apply' but each time I look at it the green block is back in the Read Only tag.


> **megamandos said:**
> Ok, so the share is one a windows box? Then check "share permissions" AND "ntfs permissions". they are two separate sets of permissions under windows. Right click on the folder being shared and click properties: ntfs permissions is under the "security" tab and share permissions is under the "sharing" tab.

---

### Post by chrismitt2002 on 2010-06-20
im haveing a similar problem here 

[http://ubuntuforums.org/showthread.php?t=1512831](http://ubuntuforums.org/showthread.php?t=1512831)

---

### Post by yorua007 on 2011-03-09
I solved this problem.Try the following command in the mounted dirctory:
ls -al
and you will seee that every file and directory are owned by the root,so you can not creat or write to an existing file.Solution is mount the share folder with the options:
-o uid=current_user,gid=current_usergroup.

---

