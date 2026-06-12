---
title: "Folder and file permissions on web directories"
date: 2011-09-27
forum: General Help
---

### Post by diogoteix on 2011-09-27
I'm trying to set the right folder/file permissions for my web directories. 

In order to "cd" into a folder, execute permission seem to be compulsory (which I find a bit odd, I was expecting read permissions to be enough...)

But to give execute permissions on all folders of the directory tree, while excluding the files, I'd like to know the proper arguments in the chmod -R command (without doing it folder by folder!).

Any guess on how to do it??

Thanks a lot

---

### Post by diogoteix on 2011-09-27
> **diogoteix said:**
> I'm trying to set the right folder/file permissions for my web directories. 

In order to "cd" into a folder, execute permission seem to be compulsory (which I find a bit odd, I was expecting read permissions to be enough...)

But to give execute permissions on all folders of the directory tree, while excluding the files, I'd like to know the proper arguments in the chmod -R command (without doing it folder by folder!).

Any guess on how to do it??

Thanks a lot

Found it!

chmod -R g+X *
chmod -R u+X *

makes only directories executable (not files)

---

### Post by cj13579 on 2011-09-27
This is useful to know - thanks!

---

