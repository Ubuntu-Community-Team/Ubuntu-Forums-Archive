---
title: "Hard links"
date: 2006-03-30
forum: General Help
---

### Post by hove99 on 2006-03-30
Hi

Does anyone know if it is possible to create hard links to a directory? I do:
> 
sudo ln -d /media/somewhere linkname


but i get "Invalid cross-device link". I know about symbolic links, but I need this to be a hard link. Googling this problem tells me, that it is possible for unix.

Thanks

---

### Post by hove99 on 2006-03-30
I may have found a work-around: I just make a symbolic link to the directory and then hard link to the symbolic link :-)

If anyone have a better or more direct approach, please let me know.

---

### Post by tedius on 2006-03-30
Why do you need to hard link it?

From the error message I believe you are trying to put a hard link across devices (ie from hda1 to hdc1), and you are not allowed to do this with hard links.

---

### Post by hove99 on 2006-03-30
Is was trying to work around:

[http://www.ubuntuforums.org/showthread.php?p=875698#post875698](http://www.ubuntuforums.org/showthread.php?p=875698#post875698)

and I did by just making a symlink. Yestoday it didn't work, today it did :-)

---

