---
title: "Letting user to access only particular directory"
date: 2011-07-06
forum: General Help
---

### Post by newn on 2011-07-06
Hi.
I'm using Ubuntu x64 10.04 edition. How can I set only one particular directory (and it's contents) to be accessible to a user while make everything else inaccessible for him? I already added the user by using adduser command.

Thanks!

---

### Post by SeijiSensei on 2011-07-06
By default users can write to /home/user and /tmp.  However they can list most other directories, and often read the files therein.  They can't change them though, because they won't have root privileges via sudo.  You can't, for instance, lock users out of /usr/bin; they wouldn't be able to run any of the programs stored there.

What specific restrictions do you need to implement?

Read this first:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by oldfred on 2011-07-06
I really do not know how to do what you want, but have saved some links to similar requests, I think you may want to review the links on groups:

Shared users using bindfs:
[http://ubuntuforums.org/showpost.php?p=8983087&postcount=25](http://ubuntuforums.org/showpost.php?p=8983087&postcount=25)
HowTo: Create shared directory for local users (with bindfs). 
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)


[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

