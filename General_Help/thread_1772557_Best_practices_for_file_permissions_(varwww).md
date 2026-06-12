---
title: "Best practices for file permissions (var/www)"
date: 2011-05-31
forum: General Help
---

### Post by 0vertone on 2011-05-31
Hello there everyone,

I'm pretty new to the Linux scene but I'm already in love with Kubuntu.
I've still got a learning curve to go before I'll be happy and just have 1 or 2 questions about file/folder permissions.


There are lots of tutorials and opinions on file permissions and web hosting.
So lets say I wanted to allow write permissions to the /var/www folder.


which would be best practice?

Chown -R user...  allow a specific user to have write capabailities.

use gksudo nautilus   (unsure what this does)

or open the folder to all parties.


If anyone has any opinions on file permissions in general or web hosting security then feel free to throw them at me.

Thanks.

---

### Post by Joe of loath on 2011-05-31
IMHO, keep the permissions for /var/www as writable by root only, readable by everyone else, unless a specific program (IE mediawiki, phpbb) requires something else for config files and the like.

---

### Post by 0vertone on 2011-05-31
In my case I was manually copying files eg index.html into the folder. 

More convinient to drag and drop. You think i should go into temrinal and copy manually with sudo.....blah.... to var/www?

or is there a way im not familiar

---

### Post by Joe of loath on 2011-05-31
Personally I use the terminal, creating all the files in a directory, then running sudo cp -r * /var/www or similar. Any archives for install I use sudo wget [www.example.com/file.tar](www.example.com/file.tar), then extract in situ.

If you like mouse waving though, gksu nautilus will open up a root terminal window, allowing you to drag stuff around at will.

---

### Post by Toz on 2011-05-31
I generally create another group, say wwweditors, and set the ownership as root:wwweditors and set the permissions as 2775```
chown -R root:wwweditors www
chmod -R 2775 www
...
drwxrwsr-x  2 root wwweditors 4096 2011-05-31 19:07 www/
```then I add whoever needs write access to the directory to the wwweditors group.

This way: 
- root owns www with full permissions (7=read,write,execute) 
- wwweditors are the group owners of the directory with full permissions (7=read,write,execute - plus the setgid bit (2) set to ensure that any files created by any member of wwweditors automatically inherits wwweditors as the group owner ensuring ongoing access for all group members regardless of who created the file)
- and everyone else with read/execute rights (5=read,execute) for basic access

Then on in, I just manage group membership.

---

