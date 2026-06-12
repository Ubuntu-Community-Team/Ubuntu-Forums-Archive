---
title: "Others users can't browse my private home folder"
date: 2010-05-19
forum: General Help
---

### Post by Elris on 2010-05-19
Hi,
I used the command 
sudo chmod 0750 /home/Gianni 
to make my home folder private. 

Now, I would like that another user in my pc can read files in a subdirectory of my home. I was running several commands with chmod and chown and I tried with Nautilus too, but without success. 

I just would like to place a link on the second user's desktop, that he can click on and access my subdirectory. 

Thanks!

---

### Post by oldfred on 2010-05-19
Welcome to the forums.

lI saved this as it seemed useful and my be what you really want. It discusses a music folder but it could be any or several other folders.

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

---

### Post by sisco311 on 2010-05-19
> **Elris said:**
> Hi,
I used the command 
sudo chmod 0750 /home/Gianni 
to make my home folder private. 

Now, I would like that another user in my pc can read files in a subdirectory of my home. I was running several commands with chmod and chown and I tried with Nautilus too, but without success. 

I just would like to place a link on the second user's desktop, that he can click on and access my subdirectory. 

Thanks!

Add the user to your user's primary group. By default, your user's primary group name is the same as your login name. 

i.e.:
```
sudo gpasswd -a **user** Gianni
```

---

### Post by Elris on 2010-05-20
> **oldfred said:**
> Welcome to the forums.

lI saved this as it seemed useful and my be what you really want. It discusses a music folder but it could be any or several other folders.

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Unfortunately my folder is a subdirectory of my home folder.
So, /home/my_user/subfolder

So, I can't place it directly in /home

The problem is that when I have a subdirectory of my home folder I can't let others reach it despire waht permissions I give it.

---

### Post by Elris on 2010-05-20
> **sisco311 said:**
> Add the user to your user's primary group. By default, your user's primary group name is the same as your login name. 

i.e.:
```
sudo gpasswd -a **user** Gianni
```

But in the case it seems to me that the second user can read all my files. Instead, I want that he can read just files in a specific folder.

---

### Post by Elris on 2010-05-20
The reason why I can't have my shared folder in /home but I need it in my user's folder is because it is a subdirectory of Dropbox folder. 

So, I need something like this:

/home/gianni/dropbox/sharedfolder

and I need the second user to access it.

Thanks a lot

---

### Post by sisco311 on 2010-05-21
> **Elris said:**
> The reason why I can't have my shared folder in /home but I need it in my user's folder is because it is a subdirectory of Dropbox folder. 

So, I need something like this:

/home/gianni/dropbox/sharedfolder

and I need the second user to access it.

Thanks a lot

Sorry for the delay. 

You have to create the shared directory outside of your home. It must be owned by you and you have to set read permissions for a group and add the second user to this group. You also have to set the [setgid]("http://en.wikipedia.org/wiki/Setuid#setgid_on_directories") permission on the directory, in this way new files created in the shared directory will inherit its groupid.

[list=i]
[*]Create a directory in /home:
```
sudo mkdir /home/.shared
```


[*]Set the owner:
```
sudo chown gianni /home/.shared
```


[*]Set the group you want to allow to read the directory (i.e. users):
```
sudo chgrp users /home/.shared
```


[*]Add the second user to the users group:
```
sudo gpasswd -a **username** users
```


[*]Set the permissions:
```
sudo chmod 2750 /home/.shared
```


[*]Copy/Move the files you want to share in /home/.shared.


[*]Create a symbolic link in the dropbox directory:
```
ln -s -T /home/.shared /home/gianni/dropbox/sharedfolder
```


[*]Create a symbolic link to the shared directory in the second user's home, as the second user run something like:
```
ln -s -T /home/.shared /home/**username**/**whatever**
```
[/list]

---

### Post by Elris on 2010-05-27
Thanks. Great explanation. It worked perfectly!

---

