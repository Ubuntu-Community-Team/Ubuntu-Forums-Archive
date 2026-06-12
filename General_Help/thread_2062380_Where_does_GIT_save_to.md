---
title: "Where does GIT save to?"
date: 2012-09-24
forum: General Help
---

### Post by 777funk on 2012-09-24
I just did the following and have no idea where it all went to:

> nick@NickUbuntu:~$ git clone git://github.com/rdanbrook/nestopia.git
Cloning into 'nestopia'...
remote: Counting objects: 1437, done.
remote: Compressing objects: 100% (610/610), done.
remote: Total 1437 (delta 924), reused 1338 (delta 825)
Receiving objects: 100% (1437/1437), 2.14 MiB | 41 KiB/s, done.
Resolving deltas: 100% (924/924), done.Where does the GIT function save to and what do you do next?

thanks in advance!

---

### Post by drmrgd on 2012-09-24
Check your home folder.  Looks like you downloaded it there.  I'm pretty sure, given sufficient permissions, it'll just download to wherever you are currently.

I don't know about that package.  Had a look at the Github site, though, and there is a readme.html that's part of the package.  Have a look at that, as it seems like it goes over how to use it.

---

