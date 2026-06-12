---
title: "Permissions issue"
date: 2010-12-12
forum: General Help
---

### Post by Mosabama on 2010-12-12
I have a directory in the home directory called ftp with the following permissions:

```
drwxrwxr-x  3 root  root  4096 2010-12-13 00:58 ftp

```

I have a user "mosab" that is a member of root group, /etc/group:

```
root:x:0:mosab
```

why cant user mosab write or copy files to ftp folder?

thanks.

---

### Post by gdonwallace on 2010-12-12
You are correct, it is a permissions issue.  Your permissions drwxrwx**r-x** should be rwx all the way across.  That should give you the write permissions You need.

---

### Post by matt_symes on 2010-12-12
Hi

Being a member of the root group does not automatically give you the privileges to write and delete any files or folders owned by root.

Imagine if you were a member of the root group. You could perform all the havoc you wanted without knowing the sudo password. All because you are a member of the group root.

Ubuntu does not work like this. To manipulate files and folders owned by root you must either use sudo to get temporary privileges (the preferred method) or change to root user. Both these elevations in privilege require knowing the admin password.

All that is happening is you are getting a 'permission denied error'.

One could _very_ easily destroy the file system by accident if you could manipulate roots files by being a member of roots group. At least with sudo it stops to make you think about what you are about to do and just makes it _quite_ easy to destroy your file system. ;)

Why is the folder owned by root anyway?

Kind regards

---

### Post by Mosabama on 2010-12-13
Actually when I installed vsftpd that directory was created during the installation process. and the ownership is as it is .. I didnt change it.

what I wanted to do is ad mosab "my default user" to the group root so I can drag and drop files to this folder in GUI so I can share it autonomously (any one would [ftp://my-lap](ftp://my-lap). and download files.

what I tried to do is changing the group of the file to ftp group and add user mosab to ftp group. but when I did that I couldnt access the files by ftp:// !!! I have no idea why!!

---

### Post by Mosabama on 2010-12-13
> **gdonwallace said:**
> You are correct, it is a permissions issue.  Your permissions drwxrwx**r-x** should be rwx all the way across.  That should give you the write permissions You need.


but I dont want any one else to write in this directory !

---

### Post by Mosabama on 2010-12-13
and btw, when I chown to user ftp and chgrp to user ftp. when ever I connect to ftp server it will ask for a username and pass while anonymous=yes in vsftpd.conf.

but when its own by root it works correctly why ?

---

### Post by ender4 on 2010-12-13
I think what you really want to do is change the ownership of the folder.  If you only want the user mosab to be able to write in it run ```
chown mosab:mosab ftp
```, and mosab, and only mosab will be able to write in it.  Alternatively you could create a group for the specific purpose of writing in the directory, and give that group ownership, (either with chown or chgrp) then add any users you want to have write access to that group.  Remember that root is able to read and write anywhere on the file system.

---

### Post by Mosabama on 2010-12-13
well, that worked perfectly ender4 thanks mate.

but out of curiosity. why when I change it to ftp:ftp it will ask for a user name pass?

---

### Post by matt_symes on 2010-12-13
Hi

> what I wanted to do is ad mosab "my default user" to the group root so I can drag and drop files to this folder in GUI 
That will not work.

Press Alt + F2 to display the run application dialog and the type

gksudo nautilus

Enter your password. This will open nautilus with root privileges. You can then use nautilus to drag and drop files into the directory. When you have finished close Nautilus.

Kind regards

---

