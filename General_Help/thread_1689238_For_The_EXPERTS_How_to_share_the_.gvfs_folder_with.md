---
title: "For The EXPERTS: How to share the .gvfs folder with samba"
date: 2011-02-16
forum: General Help
---

### Post by m.karrer on 2011-02-16
Or in other words how to mount a ftp directory to the local file system and then provide this folder via samba to windows users as a normal directory?!?

It was pure hell:

First i tried it with **curlftpfs** wich was working for the mounting part but has a lot of errors while transfering files and it is a dead project after all - so this is no option!

Then i found out that there is the whole **gvfs** thing with gnome wich mounts the ftp drive perfectly for the current linux user under the **.gvfs User-Folder** BUT gvfs seems to do some magic sauce for the user permissions: **NO OTHER USER NOT EVEN ROOT is able to see the files** in this directory?!?

I found an interesstin thread about it here: 
[http://74.54.219.50/~lxgator/gnome/forum/viewtopic.php?p=11629&sid=1d24bf947190c03fe4fe815ad1daefba](http://74.54.219.50/~lxgator/gnome/forum/viewtopic.php?p=11629&sid=1d24bf947190c03fe4fe815ad1daefba)

It tells about problems with rules for fuse and i were able to add this rule and get at least the right permissions showing up for the .gvfs folder in the user directory BUT STILL no one else can see it exept the user who created the gvfs-mount ?!?!


So it seems ubuntu has a perfect way to mount external ftp shares but no way to provide this to the outer world - just because of security decisions by the fuse or the gvfs team?!? ](*,)](*,)](*,)

Please anyone before i really loose my mind: **HOW TO MOUNT A FTP SHARE AND THEN PROVIDE THIS FOLDER WITH SAMBA FOR WINDOWS USER**?!?

---

