---
title: "need help for ubuntu 9.04!!!"
date: 2009-10-16
forum: General Help
---

### Post by saurabh.mnnit08 on 2009-10-16
I was trying to install vlc in ubuntu 9.04 and suddenly power goes off, I don't have power backup at that time later when I open 'add and remove program' ,It is not opening and following message is showing

error:opening the cache(E:Type'/host/ubuntu/disk/root.disk' is not known on line 1 in 
source list/etc/apt/sources.list, E the list of sources could not be read.

I'm unable to open synaptic package manager also which is showing the problem:

E: Type '/host/ubuntu/disks/root.disk' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report. 

and even the command 'sudo aptitude update' or restarting the computer is of no use 

please help

---

### Post by 3rdalbum on 2009-10-16
> **saurabh.mnnit08 said:**
> 
E: Type '/host/ubuntu/disks/root.disk' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Error messages are your friend, not your enemy - in this case it has told you exactly where to look.

Open up the /etc/apt/sources.list file:

```
gksudo gedit /etc/apt/sources.list
```

All lines in this file must begin with "deb" or be "commented out" by use of a hash (#) symbol at the beginning. So, comment-out the line that is causing problems, save your changes and you should be able to sudo apt-get update.

In future, don't add things the /etc/apt/sources.list by hand in a text editor - use the Software Sources program, it won't let you add invalid lines.

---

