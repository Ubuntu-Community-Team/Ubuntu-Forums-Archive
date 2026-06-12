---
title: "Error while copying (Ubuntu to USB external disk drive)"
date: 2009-12-02
forum: General Help
---

### Post by francoise_peace on 2009-12-02
Hello,

In Ubuntu 9.09 Jaunty I always copied files to my external drive without any problems. Here with 9.10 Karmic Koala, I can't, it says:
> Files in the "src" cannot be handled because you do not have permission to see them

I am copying from: /home/fran to /media/VERBATIM some recent created files.

And I even changed /src permissions (owner):

[B]fran@Charmmy-Kitty:/$ ls -l | grep src
drwxr-xr-x   3 fran root  4096 2009-11-30 14:47 src[/B]
[B]fran@Charmmy-Kitty:/$ ls -l src
total 0[/B]

And I don't think /src has something to do with my copy paste problem.

And I didn't find no thread with this problem.

---

### Post by cdenley on 2009-12-02
The error you posted suggests there is a permissions problem with files in the src directory, not the src directory itself.
```

ls -al src

```

---

### Post by francoise_peace on 2009-12-04
Here it is:

fran@Charmmy-Kitty:/$ ls -al src
total 12
drwxr-xr-x  3 fran root 4096 2009-11-30 14:47 .
drwxr-xr-x 22 root root 4096 2009-11-30 13:39 ..
drwxr-xr-x  2 root root 4096 2009-11-30 13:39 .tmp_versions

---

### Post by cdenley on 2009-12-04
> **francoise_peace said:**
> Here it is:

fran@Charmmy-Kitty:/$ ls -al src
total 12
drwxr-xr-x  3 fran root 4096 2009-11-30 14:47 .
drwxr-xr-x 22 root root 4096 2009-11-30 13:39 ..
drwxr-xr-x  2 root root 4096 2009-11-30 13:39 .tmp_versions

```

ls -alR src/.tmp_versions

```

---

### Post by francoise_peace on 2009-12-06
fran@Charmmy-Kitty:/$ ls -alR src/.tmp_versions
src/.tmp_versions:
total 8
drwxr-xr-x 2 root root 4096 2009-11-30 13:39 .
drwxr-xr-x 3 fran root 4096 2009-11-30 14:47 ..

:)

---

### Post by cdenley on 2009-12-07
I just re-read your posts, and I'm a little confused. You're fixing the permissions for "/src", but you're copying from "/home/fran" to "/media/VERBATIM"? Try copying a file from the terminal, then post the command along with error so we can see exactly what you are doing.

---

