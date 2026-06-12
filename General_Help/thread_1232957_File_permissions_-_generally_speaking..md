---
title: "File permissions - generally speaking."
date: 2009-08-06
forum: General Help
---

### Post by Blundey on 2009-08-06
Maybe I'm thinking about this the wrong way. But let me try to explain my dilema.

I have a folder called xxx:

dr--rwx---  3 bob hug    4096 2009-08-06 09:31 xxx

Now ive set the permission 470 so that anyone with the UID of "bob" can only read the folder contents and anyone one in the group "hug" can read write and execute.

The way i see it, i should be able to add say 10 people to the group called "hug" all with different UIDS and they should be able to read write and execute in this folder?

However upon testing, this is not the case and im not sure why. In fact with a different UID no one can see the contents of the folder. 

I want to be able to have a group have access to this folder and these permissions are managed by groups and not UIDS.

---

### Post by kpkeerthi on 2009-08-06
Did you log out and login after adding the users to the group?

---

### Post by Blundey on 2009-08-06
All users have been added to the group "hug" for a long time. I want to create new groups for different permissions. 

All users will have the same UID if they are in the same company. But they will all have individual group ids. I want to restrict permissions on folders and files based on group permissions rather than User ID permissions.

Hence my example above. Give userID read only access, give everyone in the group rwx!

Should be simple not its not working, just get permission denied on trying to even cd /folder/.

---

### Post by mcduck on 2009-08-06
> **Blundey said:**
> Maybe I'm thinking about this the wrong way. But let me try to explain my dilema.

I have a folder called xxx:

dr--rwx---  3 bob hug    4096 2009-08-06 09:31 xxx

Now ive set the permission 470 so that anyone with the UID of "bob" can only read the folder contents and anyone one in the group "hug" can read write and execute.

The way i see it, i should be able to add say 10 people to the group called "hug" all with different UIDS and they should be able to read write and execute in this folder?

However upon testing, this is not the case and im not sure why. In fact with a different UID no one can see the contents of the folder. 

I want to be able to have a group have access to this folder and these permissions are managed by groups and not UIDS.
Permissions for directories are not exactly the same as they are for directories, for example the execute permissions for a directory allows you to cd into that directory, not to execute everything inside it..

Also you should note that permissions for files inside a directory are not always the same as permissions for the directory itself.

---

### Post by Blundey on 2009-08-06
Even still, ANYONE who is a member of group hug should have rwx perms on that directory?

---

### Post by mcduck on 2009-08-06
> **Blundey said:**
> Even still, ANYONE who is a member of group hug should have rwx perms on that directory?
They should have right to access the directory, and create/delete files in it, and list directory contents. But not execute files inside the directory, that permission has to be set for the files themselves.

---

### Post by Blundey on 2009-08-06
Thats my point. Ive given group hug rwx on that folder, so if they create files or folders in there, they will be the owners so it should not be a problem as they all share the same UID, but have different groups.

So if anyone create a file in folder XXX then they should all be able to access the files.

Right now im struggling to even get in the folder and i dont know why!

---

### Post by mcduck on 2009-08-06
> **Blundey said:**
> Thats my point. Ive given group hug rwx on that folder, so if they create files or folders in there, they will be the owners so it should not be a problem as they all share the same UID, but have different groups.

So if anyone create a file in folder XXX then they should all be able to access the files.

Right now im struggling to even get in the folder and i dont know why!

Could be related to trying to use same UID for different users, when UID really is how users are told apart by the system. (file systems don't store file owners based on user names, but based on UID).

---

### Post by Blundey on 2009-08-06
Well the server is running samba. People/companyie are mapping a network drive and all require permissions that equal to that of there colleagues so they can modify the same files etc...

However there is sometimes a requirement for them to have a group of users only access to one particular folder. So to combat this i was going to create a group called lets say company-private, and then add a select few users to that group to inherit the permissions of said folder.

---

### Post by Dithers on 2009-08-17
[QUOTE=Blundey;7742096]Well the server is running samba. People/companyie are mapping a network drive and all require permissions that equal to that of there colleagues so they can modify the same files etc...



if your running samba your problems are probably in your smb.conf

the create/folder mask and share definitions can mess with your actual access permissions.

---

### Post by Dithers on 2009-08-17
your problem may also be your umask

sudo gedit /etc/profile

and change your umask to 002

the umask is subtracted from the actual file permissions
if your permissions are set to dr--rwx---  or 770 a umask of 022 "defult" will change it to 750 or dr--rw-- and not alow user to cd to the dir

---

