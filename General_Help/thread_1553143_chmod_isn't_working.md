---
title: "chmod isn't working"
date: 2010-08-14
forum: General Help
---

### Post by sdlynx on 2010-08-14
I am trying to change the permissions for a folder I have mounted on an ntfs partition that if mounted through fstab on startup.  It is owned by me through fstab, and is also owned by my group (just me).  I used
```
sudo chmod -Rv 755 /windows/XAMPP/htdocs
```
It runs through saying that it has changed all the permissions but when I run an ls -l the permissions aren't changed at all.

It's currently drwxrwx--- and I want drwxrwxr-x.

My fstab line for that partition looks like:
```
UUID=1E6EF10F6EF0E087 /windows        ntfs    defaults,nls=utf8,umask=007,gid=1002,uid=1002 0       0
```

I think the problem is with my umask setting, perhaps it needs to be 002?  I just realized this now though, I will try it and get back to this thread (via Edit).  For now, any input would be great.

The reason for changing the permissions is because I want to make a symlink from my default apache directory (currently set to ~/www) at ~/www/htdocs and make that directory work for both my windows apache and linux apache.

---

### Post by sdlynx on 2010-08-14
UPDATE: It was the umask, when I set it to umask=002 it worked perfectly.  Well, what a waste of a thread.  Hopefully at least someone gets assistance from it...

---

