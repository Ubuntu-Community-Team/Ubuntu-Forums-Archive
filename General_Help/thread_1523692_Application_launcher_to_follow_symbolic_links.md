---
title: "Application launcher to follow symbolic links"
date: 2010-07-04
forum: General Help
---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-04
Hey everyone,

Does anyone know how to get an applications launcher to follow a symbolic link. I got it to work using the absolute path name to the executable, but the other doesn't seem to work.

-Thanks

---

### Post by khuttger on 2010-07-04
Yes, so on the desktop I created new launcher and since my application is in terminal i did 'Application in Terminal' and just selected the symbolic link (e.g. ~/sbin/weather) and worked fine.

---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-04
I think the problem is with my symbolic link. I created by ln -s  targetFileName LinkFileName
Here I am talking about the absolute path name. The link was created,  but it still appears to be a hard link...that is the contents of the  target are the same as this when I display the contents of the link. I  am just trying to create a 'shortcut' that runs the executable when I  use it in the launcher as you have described above. If I try to run the  link out of the terminal I get an error telling me to set an environment  variable that is local to the program ... help

-thanks

---

### Post by Perfect Storm on 2010-07-04
Try use sh -c instead of symblink:

sh -c "cd <path> && ./<binary>"

---

