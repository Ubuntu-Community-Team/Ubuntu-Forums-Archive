---
title: "How to map in Windows a external linux directory"
date: 2010-11-10
forum: General Help
---

### Post by duffed on 2010-11-10
Hi,
 
I would like to be able to map on my laptop a directory of my Linux server.
 
I try into Windows to map is using [\\MYIP\directory]("file://\\MYIP\directory") name and Its not working.
 
SAMBA is install and working as if my laptop is connected on my home network I can map it using my server name.
 
But I would like to be able to also map it when i'm ouside. Is there any setting I have to add in my Linux server or any software I need to add ??
 
Thanks for your help.

---

### Post by DeMus on 2010-11-10
> **duffed said:**
> Hi,
 
I would like to be able to map on my laptop a directory of my Linux server.
 
I try into Windows to map is using [\\MYIP\directory]("file://\\MYIP\directory") name and Its not working.
 
SAMBA is install and working as if my laptop is connected on my home network I can map it using my server name.
 
But I would like to be able to also map it when i'm ouside. Is there any setting I have to add in my Linux server or any software I need to add ??
 
Thanks for your help.

Did you share the map on your server? Of course you did but I ask this anyway.
Isn't the syntax like this:
```
\domain\server\folder
```
domain can be the name of your home network
server is either the name of the server or its IP-address
folder is the share-name of the directory
When you don't use domain and server but just the name of the folder it should be: ```
\\\folder
``` if I am correct.
I can't try this since I don't have a Windows computer anymore but maybe somebody else can help you with this.
Success.

---

