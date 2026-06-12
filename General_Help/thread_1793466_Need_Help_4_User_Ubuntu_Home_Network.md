---
title: "Need Help 4 User Ubuntu Home Network"
date: 2011-06-29
forum: General Help
---

### Post by grunge09 on 2011-06-29
I have 4 pcs on the network, I have a 4tb NAS array I manaully use Rsync once a week to do backups.  (mostly cause its very loud so I don't have it on longer than I need it). 

I used to run a 80 user NT40 Server Domain network with windows 95 pcs, I was wanting something like that for me.  

Basically I want a centralized server for backup of user home directories.  I want the users to be able to log on the server from their pc (like a windows domain logon), and have access to their home directory as it if were local on their pc (ecept its on the server pc), meaning I don't want to to look like an NFS share icon.  SO if they click on PLACES on the top menu bar and computer or home folder it shows their home folder on the server.  

I want user leverl security meaning I don't want them to have acces sto others home folders unless I specify.  Also I want them all to have access to certain folders (music, pictures, media, etc.

Do I need Ubuntu Server and Samba/NFS, or Open LDAP Server?

NFS just seems to be basic dir/file sharing.  Samba goes a step further to allow user authenticaion.  

I just want a centrailized server, separate home user directories, public directories.  User security.  

So if a local PC goes down, I still ahve all the users stuff on the server.  and can just put in a new HD or new pc and setup the client side and they are back in nusiness.

---

### Post by Dangertux on 2011-06-29
> **grunge09 said:**
> I have 4 pcs on the network, I have a 4tb NAS array I manaully use Rsync once a week to do backups.  (mostly cause its very loud so I don't have it on longer than I need it). 

I used to run a 80 user NT40 Server Domain network with windows 95 pcs, I was wanting something like that for me.  

Basically I want a centralized server for backup of user home directories.  I want the users to be able to log on the server from their pc (like a windows domain logon), and have access to their home directory as it if were local on their pc (ecept its on the server pc), meaning I don't want to to look like an NFS share icon.  SO if they click on PLACES on the top menu bar and computer or home folder it shows their home folder on the server.  

I want user leverl security meaning I don't want them to have acces sto others home folders unless I specify.  Also I want them all to have access to certain folders (music, pictures, media, etc.

Do I need Ubuntu Server and Samba/NFS, or Open LDAP Server?

NFS just seems to be basic dir/file sharing.  Samba goes a step further to allow user authenticaion.  

I just want a centrailized server, separate home user directories, public directories.  User security.  

So if a local PC goes down, I still ahve all the users stuff on the server.  and can just put in a new HD or new pc and setup the client side and they are back in nusiness.

I would consider using Samba with Open LDAP to accomplish this. I think it would be the most direct route to what you are looking for. 

Samba for user authentication/sharing, LDAP for domain policies etc.

Also I have heard Samba 4 (which is only in beta I believe) offers domain controller functionality within it; however I am not sure how this works as I have not personally used it or even done any real research on it.

---

