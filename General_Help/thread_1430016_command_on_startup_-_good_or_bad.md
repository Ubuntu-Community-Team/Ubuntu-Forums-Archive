---
title: "command on startup - good or bad?"
date: 2010-03-14
forum: General Help
---

### Post by ian2112 on 2010-03-14
Hi all,

Relative newbie here - seeking advice on having a command run on start-up.  Specifically, I want to have a chgrp and chown execute on a specific directory, subdirectory and associated files.  Is there any reason why this would be a really dumb idea?

I'm not looking for advice on how to do it (I'd like to muddle through it on my own - I learn better).  And, I'm not looking for alternatives... yet... unless it looks like it's a really dumb idea.

Background - I think this is the easiest way for me to have two users on the same PC upload photos that each user can have full access to, and do things like back-up etc.

Thoughts?

Much appreciated,
Ian

---

### Post by ibuclaw on 2010-03-14
I've never tried it myself, but you could turn on Access Control Lists (ACL) for your filesystem, then set the permissions of the directory so both users can access with same access rights.

A good graphically editor for ACLs is eiciel.

Regards
Iain

---

### Post by richs-lxh on 2010-03-14
Not much specific information there, but if it's a case of two different users needing read/write access to a directory or partition, you can do that from the folder properties.

My wife and I both have read/write access to a separate partition where our photos are stored.
Open Nautlius as root (graphical)
```
gksu nautilus
```Navigate to the directory in question, right click and choose properties. then permissions. If you allow members of the group "users" read/write access that means you will both be able to upload, backup and do whatever you need.

---

### Post by asmoore82 on 2010-03-14
It doesn't have to be that complicated...

Linux does not adhere to an inherited permissions model, and the true irony is that
this actually makes things simpler. Inherited permissions is a wolf in sheep's clothing
that appears to be a one-size-fits-all foolproof solution but in fact only causes
extremely lazy and thoughtless administrators.

So how does the Linux way make it simpler? Well the default permissions on files and folders
that users create will be readable by all. This does not create a security problem
because an unauthorized user would not have permission to a higher level folder,
effectively breaking the path of permissions so that they cannot get into the restricted area.

For example, if I want to make my home folder and hence all of its contents
private, I only need to set permissions on that one folder. It doesn't matter
that technically others still have read-only access to my Music, Pictures and Documents
folders, because they can't even get down to that level. The "inherited permissions"
mindset would lead someone to believe that they should revoke these permissions
*recursively* but this is _not_ the case ~ it would be needless extra work.

The way in which this applies to your needs is that you only need to set
group ownership on that top folder of the common area once. Users will retain
ownership of the files and folders they create below this level but that is OK
because their default permissions will allow other users to view them as well.

---

### Post by ian2112 on 2010-03-14
All,

I appreciate the suggestions.  Although I'm still looking for an opinion, or potential pitfalls to having chgrp and chmod run at startup.

I've tried Access Control Lists, but run into trouble (I think) with back-ups on the these folders.

Opening Nautilus as root is a though, however, my wife's account doesn't allow her to operate as root.  And, I want to use more than Nautilus (and so don't want to have to open every application via the terminal as sudo).

I'm looking to change the permissions to have each user (belonging to a common group) have read, write and execute permission.

Thanks for the replies so far... 

Ian.

---

### Post by fluffman86 on 2010-03-14
Read up on adding the chmod commands you want to execute either to crontab (runs every so often) or /etc/rc.local (runs on each boot).  I would type more but you said you wanted to fumble through it all yourself...

---

### Post by rsay on 2010-03-14
The main reason I don't like your idea of running a program at bootup is that you have to reboot to switch which person is able to edit photos. The first time your wife just switches users without rebooting, she won't be able to access the photos.

I have tried various ways of sharing a pictures folder over the years including attempts at changing umask while the program was running and then changing it back when the program exited. I have finally found a way that works quite easily, using bindfs. Most importantly, my wife hasn't found a way to mess it up yet!

```
sudo apt-get install bindfs
```
```
sudo mkdir /home/shared
```

Edit /etc/fstab and add a line similar to the following

```
bindfs#/mnt/data/current  /home/shared  fuse  mirror=husband_name:wife_name,group=users,perms=0000:u+rwD:g+rwD  0 0
```

After you reboot (or mount /home/shared) you will each be able to access the /home/shared directory with read/write permissions as if the files are your own.

For other options:
```
man bindfs
``` 

For further reading about the other cool tricks bindfs can do:
[http://code.google.com/p/bindfs/]("http://code.google.com/p/bindfs/")

---

### Post by dcstar on 2010-03-14
> **ian2112 said:**
> 
Relative newbie here - seeking advice on having a command run on start-up.  Specifically, I want to have a chgrp and chown execute on a specific directory, subdirectory and associated files.  Is there any reason why this would be a really dumb idea?
.......
Background - I think this is the easiest way for me to have two users on the same PC upload photos that each user can have full access to, and do things like back-up etc.


If you want to do such a thing then it means you are misusing folders that are supposed to be secure.

If you want a shared folder then set it up **totally outside** of the Linux system folders (including the first level of /home) and simply have it with the appropriate permissions and then put in links in the user's folders to it.

As first user:
```
sudo mkdir /Shared
sudo chmod 777 /Shared
ln -s /Shared /home/user-name1-whatever/Shared
```
As other user:
```
ln -s /Shared /home/user-name2-whatever/Shared
```

---

### Post by rsay on 2010-03-15
This problem is more complicated than most people think when the first try to tackle it. Symlinks seem like a good way to go until the first time that your wife tries to delete a photo that you created and she gets a permission denied error. Been there. 

Many of the issues that you will face are laid out in this thread from ubuntu brainstorm. It may take a while to read, but it will prevent you from wasting time trying ideas that have already been tried and found to be unsatisfactory.
[Easy file sharing between local users ]("http://brainstorm.ubuntu.com/idea/3916/")

Hopefully, this will become a non-issue in one of the future releases. Here are links to some blueprint pages for future releases that propose to address this issue:
1. [Share Folder to store Documents to be seen by other users]("https://blueprints.launchpad.net/ubuntu/+spec/share+folder")
*You'll see in this one that they are discussing placing the shared directory in /home, which is why I suggested placing it there. I don't understand the benefits of placing the folder "totally outside" of the normal linux folder hierarchy, as suggested by dcstar.

2. [Enabling a shared-files-directory, accesible to all users, and having Samba default to sharing this directory when enabled.]("https://blueprints.launchpad.net/ubuntu/+spec/sharing-files")

---

### Post by ian2112 on 2010-04-13
Again - thanks again for the options to try.  Just checked back on this thread (life got busy) and am happy to read up more and experiment.

Much appreciated,
Ian.

---

### Post by 3rdalbum on 2010-04-13
I know it's the totally incorrect way of doing it, but I have a Samba share that is sometimes accessed by a guest and sometimes by a user account. The computer that runs the Samba share runs chmod -r every ten seconds on the folder so there are no permissions troubles.

You could set up the same thing with Cron (I used Gnome-Schedule which is a frontend for Cron).

---

