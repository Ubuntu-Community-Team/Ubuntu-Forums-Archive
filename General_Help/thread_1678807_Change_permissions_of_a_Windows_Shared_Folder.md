---
title: "Change permissions of a Windows Shared Folder"
date: 2011-01-31
forum: General Help
---

### Post by K.abhijit on 2011-01-31
Hi all..

I'm new to the forum, (but not new to Ubuntu) so please forgive any gaffes.

I'm in an organization where each user has a Windows network username, and a central windows server with a folder for each user. I can access the folder using SAMBA and my (windows) network user name. I want to change the permissions (sharing settings) for my folder on this windows server - using only Ubuntu. 

Had i been using windows I would simply right-click on the folder, go to permissions settings and add/modify users in the list. 

First of all, is it even possible to do this using Ubuntu?

Thanks!
Abhijit

---

### Post by garvinrick4 on 2011-01-31
You cannot change permissions from a Linux machine using samba in a windows workgroup for windows shares on a windows server. Must go to windows box and change permissions there if you have the permissions. You can change permissions in the linux machine in your samba shares that other machines may see and or read-write-execute. again with permissions. 
Are you the administrator or trying to find a way to change your permissions without him? No can do.

---

### Post by K.abhijit on 2011-02-03
Well i'm not the admin, but I have the required permissions. Just to clarify things:

There is a file server FS. I have a directory in it called D. So in windows I just have to use \\FS\D and log in with my LAN username / pass to read/write/modify content. In Linux, to access the same directory i do smb://FS/D/
In windows I can right click on the directory D and change permissions (which means my network login has the right permissions) - and i'm looking for the equivalent from *Ubuntu*...

From what you say garvinrick4, there's no way to do this. Am i right?

Thanks for your help,
Abhijit

---

