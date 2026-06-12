---
title: "No having luck getting proftpd setup"
date: 2010-09-19
forum: General Help
---

### Post by MrBiggz on 2010-09-19
Hi!

I have two test sites that I use on a virtual server.  I've probably screwed the permissions up so much on these folders its not even funny!

Here's the two folders with permissions:
dave@ubuntu:/var/www$ ls -all
total 20
drwxr-xr-x  4 root     root     4096 2010-09-19 02:34 .
drwxr-xr-x 17 root     root     4096 2010-06-13 00:48 ..
-rw-r--r--  1 root     root       45 2009-10-31 09:48 index.html
drwxr-xr-x  3 www-data www-data 4096 2010-09-19 01:58 mrbiggz.dyndns.org
drwxr-xr-x  3 www-data www-data 4096 2010-09-19 02:32 mrbiggz.kicks-***.net

My user is included in the group www-data

I'm really having troubles getting proftpd set up do be able to look at both folders with one log on.  I could be that it's very late or I'm just clueless at this point or a combo of a & b.

I'm really not sure of my options of how to set this up. 

I appreciate and help/references offered! 

Thanks much!

+ 

I did for some silly reason used fstab to mount these two folders into my home folder.  Not sure if that was a really great idea or not.  If you need my proftpd conf file just let me know an I'll attach it!

Thanks again!

---

