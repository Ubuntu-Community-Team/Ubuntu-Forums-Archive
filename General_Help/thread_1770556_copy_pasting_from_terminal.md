---
title: "copy pasting from terminal"
date: 2011-05-29
forum: General Help
---

### Post by roopunk on 2011-05-29
hi all,
I am new to linux and have just installed ubuntu 11.04.
For testing a website, I installed the LAMP packages and got them up and running.

Now I want to use a cms: modx and I need to copy paste the cms files in the root folder. But I am not able to paste anything in the root folder. I figured out that apache directories are readonly for a general user. So how do I paste that as a super user? I know about the sudo command but that works only in the terminal. Is there a command to copy paste the whole directory from the terminal?

I know it might be a very obvious query. But please help me, I've just started using linux and am loving it. :)

---

### Post by ajgreeny on 2011-05-29
```
sudo cp -R /path/to/directory /path/to/destination
``` or ```
sudo cp /path/to/directory/* /path/to/destination
``` will copy the directory recursively, ie, with all files in the folder.

---

