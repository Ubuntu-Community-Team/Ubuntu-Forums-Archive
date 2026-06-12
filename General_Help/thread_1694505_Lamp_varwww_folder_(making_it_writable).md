---
title: "Lamp /var/www folder (making it writable)"
date: 2011-02-24
forum: General Help
---

### Post by iconz113 on 2011-02-24
Hello i just switched from osx and am using ubuntu 10.10. im trying to setup a local server and am having trouble moving files into the localhost folder (/var/www) i know i need to change permissions of the folder to be able to place files in it. i was told to use chmod, but i dont know what that is or how to use it, if anyone can help me by providing a step by step to making that folder writable i would really appreciate it, thank you in advance:)

---

### Post by wiggly81 on 2011-02-24
i think its 
```
sudo chown <username> /var/www
```
that will make <username> the owner of the directory

---

### Post by LemursDontExist on 2011-02-24
Assuming you've got files in /var/www already, you'll want to change ownership recursively: ```
 sudo chown -R <username> /var/www
```

Alternatively, you could change the permissions
```
sudo chmod -R a+rwX /var/www
``` if you want all users to be able to make changes.

Probably the most correct thing to do, however, is to make a group to access the folder:

```
sudo groupadd www
sudo useradd -g <username> www
sudo chown -R :www /var/www
sudo chmod -R g+rwX /var/www
sudo chmod g+s /var/www
```

This creates a new group, adds you to the group, gives the group ownership and read and write permissions to the folder, and ensures that files created in the folder will continue to be owned by the group.

Hope that helps!

---

### Post by LemursDontExist on 2011-02-25
One thing about my last post has been bugging me.  If you already have folders in /var/www then 
```
chmod g+s /var/www
```
would not be enough to set the setgid flag for all subfolders.

Something more like
```
find /var/www -type d -exec chmod g+s '{}' \;
```
should work to recursively set the setgid flag on all subdirectories.  This is useful if you want to ensure that the group owner remains www for all files created in the folder.

Of course if your /var/www has no subfolders, then the original command is fine.

---

### Post by Iglebekk on 2012-05-09
I still get a 550 error when I try to do add/remove files with FTP client.

---

### Post by oldos2er on 2012-05-09
Old thread closed. If you have a question, please start a new thread.

---

