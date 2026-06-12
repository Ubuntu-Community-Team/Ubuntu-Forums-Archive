---
title: "Setting default permissions for folder"
date: 2006-04-17
forum: General Help
---

### Post by dickohead on 2006-04-17
Good evening,

After playing with umask, chmod and chgrp for about an hour and half I have finally given up and am asking for some help.

This is what I have:

/var/www/* owned by www-data, group set to tim and permissions set to 775
or:
drwxrwxr-x www-data tim www


Now when I create a directory under /var/www/ say images, it gets the following permissions:

/var/www/images/* owned by tim, group set to tim and permissions set to 755
or:
drwxr-xr-x tim tim images

I then create a file in the /var/www directory, say index.php, it gets the following permissions:

/var/www/index.php owned by tim, group set to tim, permissions set to 644
or:
-rw-r--r-- tim tim index.php

How do I FORCE the directory of /var/www so that ANYTHING (file or folder) created underneath it by anyone of any group or any username is set to:

owned by www-data, group set to tim, permissions set to 775
drwxrwxr-x

Setting the umask won't cut it because that does every file and only sets permissions not users and groups.....

Surely there has to be someway to specify the default user and group for files under a folder as well as their permissions...?

---

### Post by nagilum on 2006-04-19
[QUOTE=dickohead]Surely there has to be someway to specify the default user and group for files under a folder as well as their permissions...?[/QUOTE]
None that I know of and it would actually be very bad if you could create files which belong to someone else. Whenever a file is created it belongs to the user who created it and its primary group. All you can change (during the creation) are the permissions with the umask setting.
As a normal user it is also impossible to change the owner of a file, only the group can be changed to one you are a member of.

---

### Post by dickohead on 2006-04-19
no it's not, changing owners and groups of files is very handy, and very easy.

sudo chown -R user folder/*
sudo chgrp -R group folder/*

but in the situation I have it's a very good idea to be able to create files that belong to someone else, because those files are for the web server and multiple users need to access them, so when creating a file, it's utterly important that the file always belongs to www-data and has the permissions of rwxrwxr-x or 775, but this never happens... very annoying to constantly have to type in chmod -R 775 /var/www/* and chgrp -R /var/www/* and occasionally chown -R www-data /var/www/* It would be great if these things were automatically done with a mask..... not to worry, i'll find a way :(

---

### Post by nagilum on 2006-04-20
[QUOTE=dickohead]no it's not, changing owners and groups of files is very handy, and very easy.

sudo chown -R user folder/*
sudo chgrp -R group folder/*
[/quote]
Well, you issue these commands after the files have been created already. This is of course possible, although only root can do that. As a regular user you cannot change the owner. What I meant was that setting a default user for newly created files is impossible (only root has the rights to do so anyway).

Nevertheless, one solution to your problem might be WebDAV. You can configure your Apache to enable WebDAV and let users upload their files this way. These files are then created by Apache itself and are consequently owned by www-data. Just make sure you enable some authentication mechanism to limit the write access.

---

### Post by TreetopClimber on 2006-04-30
This thread seems to be along the same issues I have made in this post > [http://ubuntuforums.org/showthread.php?t=166176](http://ubuntuforums.org/showthread.php?t=166176) < any detailed help would be greatly appreciated

---

