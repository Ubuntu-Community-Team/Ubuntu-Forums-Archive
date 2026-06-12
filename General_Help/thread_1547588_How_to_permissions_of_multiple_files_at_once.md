---
title: "How to permissions of multiple files at once?"
date: 2010-08-06
forum: General Help
---

### Post by Mr_VeRiTy on 2010-08-06
Hi, I made some files belong to root, so that my sister couldn't read them while she was staying with me, there were about 40 files altogether but I did them all at once by change the permissions of the folder and clicking "apply Permissions to enclosed files" but now I want to change them back to belonging to my user account so Opened a gksudo nautilus windows and I went on folder properties and set the permissions to [user] and clicked apply to enclosed files, but it only did the folder. I tried selecting all the files and changing them all at once that way but it won't let me, how can I make the files belong to me again, other then one by one? I dont know how to use the CLI that much.

---

### Post by darolu on 2010-08-06
Use the CLI is not hard at all, you'll love it.
This is an example of how to do it:
```
sudo chown -R user:group /my/dir
```
chown is the command to change a file/directory's owner; the -R option stands for Recursive so it will apply changes to the directory and all files  and subdirectories in it recursively, then user:group where user is your user and group the desired owner-group and finally the route to your directory.
It's very likely your default group will be the same as your username so use:
```
sudo chown -R <yourusername>:<yourusername> /your/directory
```

Read this links to learn more:

[http://linux.die.net/man/1/chown](http://linux.die.net/man/1/chown)
[http://linux.die.net/man/1/chgrp](http://linux.die.net/man/1/chgrp)
[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)

---

### Post by SaintDanBert on 2010-08-06
You login and get a graphic desktop. Whatever you run from the desktop, like file manager windows, have your permissions and identification. You need something with root permissions and ident.

Open your favorite terminal on the desktop.
Since you have several files and maybe some folders, I suggest that you use ** sudo -i **.  The "-i" option tells sudo to simulate an initial login. You'll get a shell prompt with a pound-sign to signal that you have root permissions.

Now you can make changes:
[list]
[*]chown --verbose  someUID:someGID  fileName
[*]chown --verbose --recursive  someUID:someGID  /some/path/folder/
[*]chmod --verbose  permissions  fileName
[*]chmod --verbose --recursive   permissions  /some/path/folder
[*]ls -lh  
[/list]

Check the respective man-page for **chown** and **chmod** for the details.  Use **ls -lh** to check that you are getting what you want with your commands.

When you are finished with your ownership (chown) and permission (chmod) changes, use **exit** or simply type **ctrl-d** to end your sudo session.

~~~ 0;-Dan

---

### Post by Mr_VeRiTy on 2010-08-06
> **darolu said:**
> Use the CLI is not hard at all, you'll love it.
This is an example of how to do it:
```
sudo chown -R user:group /my/dir
```chown is the command to change a file/directory's owner; the -R option stands for Recursive so it will apply changes to the directory and all files  and subdirectories in it recursively, then user:group where user is your user and group the desired owner-group and finally the route to your directory.
It's very likely your default group will be the same as your username so use:
```
sudo chown -R <yourusername>:<yourusername> /your/directory
```Read this links to learn more:

[http://linux.die.net/man/1/chown](http://linux.die.net/man/1/chown)
[http://linux.die.net/man/1/chgrp](http://linux.die.net/man/1/chgrp)
[http://linux.die.net/man/1/chmod](http://linux.die.net/man/1/chmod)
Also, what if the files were on a flash drive (sdb), would it be ```
sudo chown -R <username>:<username> /dev/sdb
```
EDIT: I figured it out, It would be sudo chown -R <username>:<username> /media/[device name]

---

### Post by Mr_VeRiTy on 2010-08-06
> **SaintDanBert said:**
> 
[LIST]
[*]chown --verbose  someUID:someGID  fileName
[*]chown --verbose --recursive  someUID:someGID  /some/path/folder/
[*]chmod --verbose  permissions  fileName
[*]chmod --verbose --recursive   permissions  /some/path/folder
[*]ls -lh
[/LIST]
 Whats a UID and GID?
EDIT: I figured it out, lol GroupID and UserID

---

