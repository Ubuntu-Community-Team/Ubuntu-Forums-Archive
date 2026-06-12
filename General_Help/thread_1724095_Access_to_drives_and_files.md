---
title: "Access to drives and files"
date: 2011-04-07
forum: General Help
---

### Post by kiwinsn on 2011-04-07
Hi all

A real dumb question, I think.

Our computer is loaded with Ubuntu, and my wife and I have separate accounts, which is fine.

I have a backup drive with data and music and, if I want to reinstall or back something up, I have to log in as each user to do so. That is OK security wise, but I want to do a complete reload and would prefer to be able to access her home folder from my account, back it up to the other drive, reinstall and then copy everything back so she can use her files.

Also, I have a couple of files in my home partition that she wants access to occassionally. I would like her to be able to access my home directory to get to those files.

If I put them on the backup drive, she cannot open them as I have the permissions.

We also run KMyMoney, and would like to be able to use the same file whichever user is logged in.

Can anyone help?

Cheers

---

### Post by Buntumatic on 2011-04-07
This is what groups are for. Create a group, say *family*, and allow this group to access files and directories you want to share.

---

### Post by JKyleOKC on 2011-04-07
Also, have a look at Clonezilla for doing your backups; it allows you to make a full disk copy without having to log in as each user individually.

---

### Post by oldfred on 2011-04-07
I have not done groups as my wife just uses my sign on.

Some links I saved in case.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

---

