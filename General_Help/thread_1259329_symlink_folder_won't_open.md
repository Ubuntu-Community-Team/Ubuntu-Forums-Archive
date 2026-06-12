---
title: "symlink folder won't open"
date: 2009-09-06
forum: General Help
---

### Post by ac13 on 2009-09-06
Hi, I'm trying to symlink a folder containing images from one place to another on my apache server with this command

**sudo ln -s design/default/img/ user/53/img**

The folder gets created but I cannot open it, not in bash or over the FTP.

*-bash: cd: img: No such file or directory*

What am I missing here?

---

### Post by CatKiller on 2009-09-06
What does ```
ls -l usr/53/img
``` say?

---

### Post by ac13 on 2009-09-06
It reports

**lrwxrwxrwx 1 root root 23 2009-09-06 21:48 user/53/img -> design/default/img**

(I'd removed the file since my last try and created a new one now... hence the creation time)

---

### Post by CatKiller on 2009-09-07
I think the problem is probably one of relative path. You've got two directory trees - design/default/ and user/53/ and your link doesn't know that it needs to go back up one tree and down the other to successfully traverse to the source directory.

There may be a way to make it all work in one ln command, but I don't know what it is; ```
cd user/53
ln -s ../../design/default/img img
``` should work, though.

---

### Post by ac13 on 2009-09-07
Thank you that solved it! :)

---

