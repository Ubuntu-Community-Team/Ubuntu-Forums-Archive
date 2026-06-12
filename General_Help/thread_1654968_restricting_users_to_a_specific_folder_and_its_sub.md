---
title: "restricting users to a specific folder and its subfolders"
date: 2010-12-29
forum: General Help
---

### Post by raviepic3 on 2010-12-29
Hello,   I wanted to restrict users within a particular folder say /var/lib/tomcat/webapps.  I want the users to see all subfolders inside webapps and work with it (edit+read but no delete).  I understood that chroot is the way, and i read this   [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)  community discussion, but what i understand out of it is, they are trying to give a complete working installation of ubuntu to the user within a directory which i dont want to.  Would be happy if somebody tell me how to proceed.

---

### Post by hawthornso23 on 2010-12-29
You usually control user access with chmod. By default users can read but not edit or delete. Allowing them to edit but not delete is ... unusual. There isn't usually much point in trying to stop users from deleting if you are going to allow them to edit, since anyone with the power to edit a file is able to edit in in such a way as to remove all contents, which is effectively the same as deleting it.

---

### Post by raviepic3 on 2010-12-29
Hello,  Thanks for replying. Using chmod how can we restrict the user from getting into other folders ?   When the user connects to my machine using ssh, he needs to be inside a folder which i specify without the permission to get outside the specified folder but with the permission to get into the subfolders of the folder which i specified.  Oh yeah, allowing editing but restricting deleting doesn't make much sense, so i can allow  the user to do anything he wants to within the folder i have specified.

---

### Post by mikeobeda on 2010-12-29
You can look at the permissions that are set for the files inside a directory using the ls -l command.  You'll see the list of files and directories.  At the left side you'll see the code that tells you permissions.  It starts with a d if the file is a directory.  So you'll see something like: drwxr-xr-- as the permission code for a directory.  r stands for read, w stands for write, and x stands for execute.

There are three different designations for a permission.  You can set permissions for the owner, a group, and people that are not either the owner or the group (others).  The permissions code follows in that order, so in my example above, the owner of the directory has read, write and execute permissions, the group that the directory belongs to can read and execute but not write to(therefore not delete either), and all other people can read but neither write to or execute the files inside that directory.

You can modify the permissions with chmod.  chmod g=rwx filename would give the group the same permissions as the owner for the file or directory named filename(referring to my example above).  chmod o=r-x would give others the ability to execute files, but still stop them from editing.

If you would like to change the owner or group associated with the file, the command is chown owner:group filename

Hoping this helps!

---

