---
title: "centrify and nfs questions"
date: 2012-03-14
forum: General Help
---

### Post by linux.girl on 2012-03-14
Hi everyone,
 
 
 I have a question: Lets say I added a  linux computer to ad domain with centrify. then i want to make the home  folder of the ad user that I am logging in with on nfs instead of  locally. now, in ubuntu all app data is stored locally in the users'  home folder. what happens to all the appdata once the home folder is set  to be on nfs? how does the user access the data that supposedely is on  the local home folder (i.e., corporate email on thunderbird which needs  the ad authentication to work properly)?
 
 
 also - what  happens with the uid of the user? i imagine it gets an uid locally and  then a different one on nfs, correct? how would that work?
 
 
 in general - what is your opinion of having this kind of architecture,  i.e., computer and user authenticated on ad with centrify but having the  home folder on NFS?
 


I know it sounds a bit confusing, I myself dont have all the aspects and questions figured out yet :-)
 
 thanks in advance,
 
 
 linux.girl

---

### Post by lisanels47 on 2012-03-14
I run an office with a server (LDAP) that authenticates users, and autofs5 mounts their home folder on a path /server/home

All the users files remain on the server, and the desktop is just a fat client.  Seems to work great.  Any user can logon to any computer and get their same desktop.  

The uid of the user is what is on the server... usually 10000 or higher.  I've not found a way for the client side to see the actual uid's or gid's.

---

### Post by linux.girl on 2012-03-14
thanks for the answers, sounds like an interesting option! i am running the experiment with centrify, so if anyone has any experience with that it would be great!

---

