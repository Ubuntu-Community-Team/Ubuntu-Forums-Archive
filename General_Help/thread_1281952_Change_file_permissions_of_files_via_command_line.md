---
title: "Change file permissions of files via command line"
date: 2009-10-03
forum: General Help
---

### Post by hellocatfood on 2009-10-03
I recently had to log into my computer using a liveCD to resuce my data before completely reinstalling Ubuntu. When copying my data over to my hard drive I got a few errors saying that my home directory (/home/username) couldn't be moved as I (the livecd user) didn't have permissions to do so. Stupidly I changed the file permissions so that root owns it and can access and delete files. Before the owner was listed as "1000"

Miraculously I managed to fix my computer but now when I try and log in I get the following message:

```
User's $HOME/.dmrc file is being ignored. This prevents the deafault session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
```

I'll take a guess and assume that it's not loading because it's still owned by root. I tried loading the livecd back up and I can't change the owner back to "1000" or my user name. Does anyone know how to change the permissions back to the home user either via the live cd or the command line?

---

### Post by dcstar on 2009-10-03
> **hellocatfood said:**
> 
........
Does anyone know how to change the permissions back to the home user either via the live cd or the command line?

```
man chown
man chmod
```

---

