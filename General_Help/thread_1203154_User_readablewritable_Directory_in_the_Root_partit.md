---
title: "User readable/writable Directory in the Root partition?"
date: 2009-07-03
forum: General Help
---

### Post by AoSteve on 2009-07-03
I'm not sure on how to do this and chmod's help isn't very revealing on what I'm trying to accomplish..   

I want a folder in the "file system" for my AVI movies.  My / partition has more space for these files then the /home partition does and I'd like to keep them there for all of the user accounts to read/write files to.   

Would "sudo chmod 777 /videos" work for this if I created a directory on the / partition?  I want read/write access for all of my user accounts, and I'm not clear on what effects that.

---

### Post by Hobgoblin on 2009-07-03
> **AoSteve said:**
> 
Would "sudo chmod 777 /videos" work for this if I created a directory on the / partition?  I want read/write access for all of my user accounts, and I'm not clear on what effects that.

Yes, that would work, a crude way to do it but it will work.

you'll have to use sudo to make the directory first.

As for what affects what, [this may help](http://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions).

---

### Post by AoSteve on 2009-07-03
I just want full access to the folder through all three of my accounts on this machine..   I would like to also be able to "network" share it if possible.   I just don't know exactly how to do it.

---

### Post by AoSteve on 2009-07-03
Problem Solved with a friends help..  Here's what I did to fixxer it up...

First, in the "System -> Administration -> Users and Groups"  I added a new group.   I had to unlock the ability with the "Unlock" button and enter my password.   

I created the group called "video" and added all of the users that I wanted to have access to it, or my three accounts with the laptop.  This process was easy.  

Since I was logged on as steve, I used the following command in a terminal to promote access to the folder "/videos"

```

sudo chown -R steve:cideo /videos

```

Now all of my accounts can access that directory with the file browser in the different desktop environments by going to "File System" and entering the "videos" folder.   

I also used the same command for my Music files.   This is a LOT easier to use then having these files on the home folder for each account.  :)  Plus it's on my root partition and every account can easily access the files.  :)   I can restrict access simply by editing the groups in the "User and Groups" dialog.  :)

---

