---
title: "dpkg-source: not found"
date: 2010-09-12
forum: General Help
---

### Post by Praveen30 on 2010-09-12
i am getting  this error after executing a command..i think my ubuntu is lacking some of the packages..can anybody tell me how to fix it..here is the description-->

$ apt-get source smplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2,155kB of source archives.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (dsc) [1,055B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (tar) [2,144kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse smplayer 0.6.7-1 (diff) [9,146B]
Fetched 2,155kB in 5min 14s (6,851B/s)                                         
sh: dpkg-source: not found
Unpack command 'dpkg-source -x smplayer_0.6.7-1.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed

---

### Post by llamabr on 2010-09-12
```
sudo apt-get install dpkg-dev
```

---

### Post by Praveen30 on 2010-09-12
thanks for reply but i had  done it already..for others go here--
 [http://http://tricksfind.blogspot.com/2010/09/how-to-see-source-code-of-open-source.html]("http://http//tricksfind.blogspot.com/2010/09/how-to-see-source-code-of-open-source.html"):D

---

### Post by llamabr on 2010-09-12
And what error do you get when you try to install it?  copy/paste your command back here.

---

