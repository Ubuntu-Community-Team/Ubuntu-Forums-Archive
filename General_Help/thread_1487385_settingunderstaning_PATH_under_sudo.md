---
title: "setting/understaning PATH under sudo"
date: 2010-05-18
forum: General Help
---

### Post by equaeghe on 2010-05-18
Hi,

I have a problem getting the PATH under sudo right.
The following sequence of console commands illustrates my problem/confusion.

```

$ echo $PATH
/usr/local/texlive/2009/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$ sudo echo $PATH
/usr/local/texlive/2009/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
$ tlmgr --version
tlmgr revision 17811 (2010-04-12 06:05:03 +0200)
tlmgr using installation: /usr/local/texlive/2009
TeX Live (http://tug.org/texlive) version 2009
$ sudo tlmgr --version
sudo: tlmgr: command not found
$ cat /etc/environment 
PATH="/usr/local/texlive/2009/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.utf8"
$ sudo screen
# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

```

If anybody could help me getting "sudo tlmgr --version" working, I'd be grateful.

TIA,

Erik

---

