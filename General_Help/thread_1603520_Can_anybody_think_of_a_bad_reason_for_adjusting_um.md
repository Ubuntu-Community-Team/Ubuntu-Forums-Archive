---
title: "Can anybody think of a bad reason for adjusting umask?"
date: 2010-10-22
forum: General Help
---

### Post by Roasted on 2010-10-22
Say you have two users in a group, and this group has the sticky ID for permissions on a folder they both need to share. That's all well and good, but if this group is going to have RW permissions, that's a problem. Umask by default has all new folders created with 755 permissions. 7-5-5. 5 = read/execute, no write. That's the problem. You would THINK there'd be an intelligent way using advanced permission settings in Nautilus to set it so everything new created in the folder comes down as a certain permission set, but evidently that's not the case. Example - I would LOVE to have a folder and set it so ANYTHING new in this folder gets 770 perms, whereas the umask remains at 755 perms. Not the case... The other alternative is umask, which changes the default permissions for all new files/folders system-wide.

If I set the umask from 755 to 775, what that means is anything I create comes down as me:me as 775 instead of me:me 755. As long as nobody is in my group, can anybody think of a reason this would be a BAD thing? I'm just trying to draw up scenarios of who this would effect in a negative demeanor and I can't come up with anything.

---

### Post by Roasted on 2010-10-24
:confused::confused::(:(

---

### Post by mikewhatever on 2010-10-24
Apparently, setting up a shared folder with newly created files writable by the chosen group is surprisingly complex in Linux, but, it's doable.
[http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html](http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html)

> 
Introduction

There is an often requested feature on Linux (or UNIX) to have the ability to create shared directories similar to what is possible in Windows, that is a directory in which every person who has been given access can read, write or modify files. However, because Linux file systems such as ext4 enforce file permissions that are stricter than any of the windows file systems such as FAT or NTFS, creating such a directory is not obvious. Of course, if you put your shared directory on a FAT or NTFS partition, it will automatically behave just like in Windows but that requires a separate partition and doesn't allow you to enforce permissions on a per-group basis. So here's a quick guide on how to do this with Ubuntu. The same principles apply to other Linux distributions so should be portable.
Use Cases

Let's go through a couple of classic use cases first, to identify exactly what we want to do.
Project Folder

In a company or university setting where users are assigned to project teams or departments, it can be useful to create shared folders where all members of the team can drop files that are useful for the whole team. They need to be able to create, update, delete files, all in the same folder. They also need to be able to read, update or delete files created by other members of the team. However, users external to the team should only have read access.
Web Development

For anybody doing web development on Linux, a classic problem is when you have to deal with development or test web servers. The default web server process runs with the www-data user and the document directory is owned by the same user. It would be great if all web developers on the team were able to update the document directory on the server while not requiring root access to do so.
Linux Default Behaviour

Linux has the concept of user groups. You can check what groups your user belongs to by typing the following on the command line:

$ groups
bruno adm dialout cdrom plugdev lpadmin admin sambashare

On a default Linux installation, groups are used to give access to specific features to different users, such as the ability to administer the system or use the CD-ROM drive. But one of the core feature of user groups is to support file permissions. Each file has separate sets of read, write and execute permissions for the user who is the owner of the file, the group that owns the file and others, that is everybody else. Whenever a user attempts to read, write or execute a file, the system will decide whether he can do it based on the following rules:

    * if the user is the owner of the file, user permissions apply,
    * otherwise, if the user is part of the group that owns the file, group permissions apply,
    * otherwise, others permissions apply. 

So to configure a shared directory as defined above, we need to:

    * create a user group for the team,
    * assign all team member users to that user group,
    * create a directory and configure it so that all users in the group can:
          o add new files to the directory,
          o modify any existing file in the directory,
    * and of course, all this should work without users having to do anything special.

How To
Enable ACL

The first thing we need to do is to enable ACL support on the partition where we will create the shared directory. ACL extend the basic Linux permission implementation to enable more fine grained control. As this requires the file system to be able to store more permission meta-data against files, it needs to be configured accordingly. We can do this by adding the acl option to the relevant line in /etc/fstab, such as:

UUID=b8c490d0-0547-4e1f-b052-7130bacfd936 /home ext4 defaults,acl 0 2

The partition then needs to be re-mounted. If the partition to re-mount is /, /usr or /home, you will probably need to restart the machine. Otherwise, the following commands should re-mount the partition:

$ sudo umount partition
$ sudo mount partition

where partition is the mount point of the partition as defined in /etc/fstab, such as /var/www.
Create Group

We then need to create the group to which we will give shared access, let's call that group teamgroup:

$ sudo groupadd teamgroup

Try to give the group a meaningful name while keeping it short. If it's meant to be a team group, give it the name of the team, such as marketing. Note the following restrictions on Debian and Ubuntu for group names (taken from the man page):

    It is usually recommended to only use groupnames that begin with a lower case letter or an underscore, followed by lower case letters, digits, underscores, or dashes. They can end with a dollar sign. In regular expression terms: [a-z_][a-z0-9_-]*[$]?

    On Debian, the only constraints are that groupnames must neither start with a dash (-) nor contain a colon (:) or a whitespace (space: , end of line: \n, tabulation: \t, etc.).

    Groupnames may only be up to 32 characters long. 

We then need to assign users to that group:

$ sudo usermod -a -G teamgroup teamuser

Where teamuser is the login name of the user to assign to the group. This assignment will take effect next time the user logs in. Make sure that you do not forget the -a option otherwise you will wipe out all existing group assignment for that user, rather than just adding a new one.
Create the Folder

The next step is to create the shared folder. This is easy:

$ cd /path/to/parent
$ mkdir teamfolder

Where /path/to/parent is the path to the parent folder and teamfolder is the name of the folder you want to create. We then assign group ownership of the folder to the group previously created:

$ chgrp teamgroup teamfolder

And give write access to the group on that folder:

$ chmod g+w teamfolder

Let's check what this folder looks like:

$ ls -l
drwxrwxr-x 2 teamuser teamgroup 4096 2010-03-03 14:32 teamfolder

Now, let's try to create a new file in that directory:

$ touch teamfolder/test1
$ ls -l teamfolder
-rw-r--r--  1 teamuser teamuser 5129 2010-03-03 14:34 test1

That looks good and any other user who is part of teamgroup should be able to create files in this directory. However, group members will not be able to update files created by other members of the group for the following reasons:

    * the group that owns the file is the user's primary group, rather than teamgroup,
    * the file's permissions only allow the owner of the file to update it, not the group.

Set the setgid Bit

We'll solve the first problem by setting the setgid bit on the folder. Setting this permission means that all files created in the folder will inherit the group of the folder rather than the primary group of the user who creates the file.

$ chmod g+s teamfolder
$ ls -l
drwxrwsr-x 2 teamuser teamgroup 4096 2010-03-03 14:32 folder

Note the s in the group permissions instead of the x that was there previously. So now let's try to create another test file.

$ touch teamfolder/test2
$ ls -l teamfolder
-rw-r--r--  1 teamuser teamuser  5129 2010-03-03 14:34 test1
-rw-r--r--  1 teamuser teamgroup 5129 2010-03-03 14:35 test2

So now whenever a file is created in the team directory, it inherits the team's group.
Set Default ACL

The second issue is related to umask, the default mask applied when creating files and directories. By default umask is set to the octal value 0022, as demonstrated if you run the following:

$ umask
0022

This is a negative mask that is applied to the octal permission value of every file or directory created by the user. By default, a file is created with permissions rw-rw-rw-, equivalent to 0666 in octal and a directory is created with permissions rwxrwxrwx, equivalent to 0777 in octal. umask is then subtracted from that default to give the effective permission with which files and directories are created. So for a file, 0666-0022 gives 0644, equivalent to rw-r--r-- and for a directory 0777-0022 gives 0755, equivalent to rwxr-xr-x. This default is sensible for most situations but needs to be overriden for a team directory. The way to do this is to assign specific ACL entries to the team directory. The first thing to do is to install the acl package to obtain the necessary command line tools. Well, in fact, the first thing to do would be to enable acl on the relevant partition but we already did that at the very beginning.

$ sudo apt-get install acl

Now that the package is installed, we have access to the setfacl and getfacl commands. The first one sets ACLs, the second one reads them. In this particular case, we need to set default ACLs on the team folder so that those ACLs are applied to files created inside the directory rather than the directory itself. The syntax is a bit complicated: the -d option specifies that we want to impact the default ACLs, while the -m option specifies that we want to modify the ACLs and expects an ACL specification to follow.

$ setfacl -d -m u::rwx,g::rwx,o::r-x teamfolder
$ touch teamfolder/test3
-rw-r--r--  1 teamuser teamuser  5129 2010-03-03 14:34 test1
-rw-r--r--  1 teamuser teamgroup 5129 2010-03-03 14:35 test2
-rw-rw-r--  1 teamuser teamgroup 5129 2010-03-03 14:36 test3

There we go, it all works as expected: new files created in the team folder are created with the team's group and are group writeable. To finish off, let's have a look at how the folder's ACLs are stored:

$ getfacl teamfolder
# file: teamfolder
# owner: teamuser
# group: teamgroup
user::rwx
group::rwx
other::r-x
default:user:rwx
default:group:rwx
default:other:r-x

Granting and Revoking Access

Granting a user write access to the team folder is now extremely easy: you can just add that user from the team's group when he joins the team:

$ sudo usermod -a -G teamgroup joiner

Where joiner is the user ID of the user joining the team. Revoking access is nearly as easy, you just need to remove the user from the team's group. Unfortunately, there is no way to do this in a simple command so you will have to edit the file /etc/group, find the group and remove the user ID from that group.
Variations
Restrict Delete and Rename to Owner

By default, any user who has write access to a file can delete or rename it. This means that any member of the team can delete or rename any file created by another member. This is generally OK but if it is not, it can also be restricted by setting the sticky bit on the directory:

$ chmod +t teamfolder
$ ls -l
drwxrwsr-t 2 teamuser teamgroup 4096 2010-03-03 14:32

This feature is used on the /tmp directory to ensure that all files created in that directory can only be deleted by their owners.
Restrict Access for Others

Another variation that may be more useful is to completely deny access for users that are not part of the team. it may be that a particular team is working on some sensitive stuff and you don't want anybody outside the team to see it. To do this, we just revoke all permissions and ACLs for others on the team folder:

$ chmod o-rx teamfolder
$ setfacl -d -m o::--- teamfolder


---

### Post by Roasted on 2010-10-25
> **mikewhatever said:**
> Apparently, setting up a shared folder with newly created files writable by the chosen group is surprisingly complex in Linux, but, it's doable.
[http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html](http://brunogirin.blogspot.com/2010/03/shared-folders-in-ubuntu-with-setgid.html)

Yeah. Quite unacceptable, imo... And while it may be do-able, it's hardly practical for most average users. 

Likewise, is there any downside anybody can think of in regard to changing the umask to that?? That's just something I can't see an issue with but I don't want to be blindsided either.

---

