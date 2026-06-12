---
title: "Directory permissions"
date: 2010-07-14
forum: General Help
---

### Post by =ChAoS= on 2010-07-14
Ok so my ubuntu server install was created with a root user. I then used that to install a basic gnome desktop and 2 new users that have there own home directories. We can both ftp and ssh into it and now have nx mainly for my mate to see whats what.
 
I can create folders etc in /home/username but not in /home as its owned by root. I would like to be able to allow both myself and the one other user (he's a joint renter in the server) to be able to create folders that we both have equal rights to in this section mainly for the things we download and share, but would like to keep the current permissions on our personal /home folders which are the default.
 
Is this possible?
 
At present there is my home folder, his home folder and lost and found. I know roughly what that is and dont think i need it particularly and if i did i would log in as root.
 
I'm not sure about groups or how to give permissions to this directory and have looked around quite a bit. Does the group admin give this right or do i need to change ownership?
 
Everything i found on it would make it my directory if i chown it and i want equal access to both of us.
 
I hope this makes sense and thanks for any help. 
 
=ChAoS=

---

### Post by sisco311 on 2010-07-14
> **=ChAoS= said:**
>  
Is this possible?


Yes, but what do you mean by *equal rights*? Full read/write permissions for all the files from the directory? Or would you like to share some files with read only permissions?

---

### Post by =ChAoS= on 2010-07-15
Hi and thanks for the response. 
 
I tried a different approach and created a new folder as root and chmod it to 777. I can as normal user create/delete folders etc inside but my mate still can't. I'm wondering if this is something to do with groups?
 
I have seen a list of the default groups but still ain't sure what they actually allow you to do. Would adding him to say the admin group change his permissions?
 
Tbh i dont remember adding myself to any group but i still have access to a root created folder/sub folders but obviously can't change permissions unless root.
 
Thanks =ChAoS=

---

### Post by sisco311 on 2010-07-15
Hi, please check out [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Add both users to a common group, e.g. users:
```
sudo gpasswd -a user1 users
sudo gpasswd -a user2 users
```

Log out and log back, in order the new group membership to take effect.

Create the shared directory as root:
```
sudo mkdir /home/shared
```

Change the group of the directory to users:
```
sudo chgrp -R users /home/shared
```

Set read/write/execute permissions for the group:
```
sudo chmod 0775 /home/shared
```

Now any user in the users group will be able to create, delete, rename, copy and move files to the directory.

If you set the setgid bit of the directory, new files created in the directory will inherit the group of the directory (and not the primary group of the user who created the file):
```
sudo chmod 2775 /home/shared
```

---

### Post by =ChAoS= on 2010-07-15
Thanks a lot. I used those commands to change the permissions of an existing folder that was causing the problems. It seems to have worked. When my mate comes on line i will see if hes ok now.
 
I realise that ubuntu has a lot of security features that i have yet to learn and use correctly but this is a remote server and only we have access to it. we will not be letting anyone else use it but who knows in the future.
 
Again many thanks

---

### Post by =ChAoS= on 2010-07-15
Sorry to bump this with another question but what would be the command to remove a group from a folder/directory like the opposite of ... 
 
sudo chgrp -R users /home/shared ?
 
Thanks =ChAoS=

---

### Post by Lampi on 2010-07-15
> **=ChAoS= said:**
> what would be the command to remove a group from a folder/directory like the opposite of ... 
 
sudo chgrp -R users /home/shared ?
You can't do that - you can **change** it, but not **remove** it.

---

