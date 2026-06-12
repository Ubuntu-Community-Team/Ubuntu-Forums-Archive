---
title: "Can't access my own files"
date: 2009-10-17
forum: General Help
---

### Post by white-zilla on 2009-10-17
after toying with ubuntu for the past few years, I made it my primary OS on my new desktop computer, I'm currently running 9.10 and i'm still pretty green.

My system has 2 hard drives, I want all my music and what not to go on one (hdb) and the OS to go an another one (hda).  When I put my music on to my hard drive (hdb) it wont let me access it unless I open it through "gksudo nautilus".

If i look at hdb in a window it says its mounted. And i've followed several tutorials how to mount it through terminal.  If i go into Filesystem>media>hdb I can see the contents of hdb but it wont let me in stating "You do not have the permissions necessary to view the contents of "(insert folder name here)"

What the heck is stopping me?  Did i not mount the drive correctly? or is it something totally different?  I'm clueless, any help is greatly appreciated

---

### Post by ugm6hr on 2009-10-17
You need to change the permissions / ownership of hdb.  I suspect that when you formatted, you will have done so as root.  Hence all files are now owned by root; you should be able to read the files, but won't be able to write without sudo.

```
sudo chown -R *username:username* /*mountpoint*
```

Where 
*username* = your username
*mountpoint* = directory location of hdb (e.g. /media/music, but with only one / at start)

If you want anyone to be able to read / write to the media hd, you will have to use chmod.

---

### Post by white-zilla on 2009-10-17
holy crap that worked.  Thank you so much good sir.

---

