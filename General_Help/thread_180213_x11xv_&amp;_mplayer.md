---
title: "x11/xv &amp; mplayer"
date: 2006-05-21
forum: General Help
---

### Post by simo on 2006-05-21
I'm confused, why does in mplayer plugin x11/xv on fedora core 4 works fine, but on ubuntu 5.10 does not? I'm new to ubuntu and linux so I'm using diferent distributions. 
How can this be fixed?

Maybe this can help?

simo@ubuntu:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
simo@ubuntu:~$

Are there packages to download, or something to configure?

Thankss!

---

### Post by neoflight on 2006-06-21
[QUOTE=simo]I'm confused, why does in mplayer plugin x11/xv on fedora core 4 works fine, but on ubuntu 5.10 does not? I'm new to ubuntu and linux so I'm using diferent distributions. 
How can this be fixed?

Maybe this can help?

simo@ubuntu:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
simo@ubuntu:~$

Are there packages to download, or something to configure?

Thankss![/QUOTE]

i have the same problem? any solution yet?


edit: solved !!! by

```
 sudo aticonfig --overlay-type=Xv
```
and restart X by **alt+ctrl+backspace**

---

