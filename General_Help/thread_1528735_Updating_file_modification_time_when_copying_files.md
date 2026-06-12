---
title: "Updating file modification time when copying files to a Samba share"
date: 2010-07-11
forum: General Help
---

### Post by Krooga on 2010-07-11
I've got a PC running Ubuntu 9.10 which I use as a file server, via Samba. Clients are mostly Windows machines.

I've written a simple shell script to periodically generate a list of the most recent files which have been added to the server. I'm currently using the file mtime to determine the order. 

The problem I've discovered is that when files are added to the server, they retain the modification time on the client. What I really want is the time that the copy on the file server was created. On an NTFS partition, this is stored in a 'creation time' field, but I don't think the EXT4 filesystem on the file server supports this.

Is there any way that I can have the file mtime set to the time that the copy on the file server is created? Or is there some other way this obstacle can be overcome? I've done plenty of searching and haven't been able to find anything, so any help would be much appreciated!

---

