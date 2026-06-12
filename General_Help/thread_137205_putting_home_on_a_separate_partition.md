---
title: "putting /home on a separate partition"
date: 2006-02-27
forum: General Help
---

### Post by oldmanstan on 2006-02-27
i decided to install dapper flight 4 but before i do i want to move my /home directory to my other hard disk (which is currently being occupied by a winxp installation i never use). i know i saw a post here a couple days ago or so that dealt with this but now i can't find it.

can someone either help me out or point me to the post i'm thinking of?

thanks

---

### Post by jimbren on 2006-02-27
I think this is the entry you're thinking of.  [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

There are a few other references in the forums, too, but the blog entry above is excellent.

---

### Post by Xian on 2006-02-27
I don't know your exact setup, but in general one procedure is:

mv /home /home_old 
mkdir /home 
add/edit the mount point for /home in /etc/fstab 
mount /home 
cp -af /home_old/* /home

---

