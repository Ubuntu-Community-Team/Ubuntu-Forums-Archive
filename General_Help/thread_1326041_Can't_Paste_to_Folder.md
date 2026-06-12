---
title: "Can't Paste to Folder"
date: 2009-11-14
forum: General Help
---

### Post by Froobloops on 2009-11-14
There is a folder for a game (Cube Sauerbraten) that has music files in it.  I want to add additional music files into said folder.  The folder will not allow me to paste anything into it because the owner is specifically "root" even though I am the root user.  How do I gain access to this folder and any other folder that is protected in this way?

---

### Post by shaon3343 on 2009-11-14
go to terminal and enter this command [COLOR=Red][COLOR=Black]:[/COLOR]*** gksudo nautilus***[/COLOR]
    then a file browser appears which allow you super user priviliges. use this file browser and do the copy/ paste or whtever you want ! :)

---

### Post by quixotic-cynic on 2009-11-14
The above generalises to ```
gksudo name-of-file-manager
``` so thinks like ```
gksudo thunar
``` work too. IIRC, the console equivalent is ```
sudo cp /path/to/source/file/sourcefile.ogg /path/to/music/folder/
```

---

### Post by 3rdalbum on 2009-11-14
You are not root, you are a user. By default, your account does allow you to open programs and run commands as root, but only if you tell the system to run them as root. The easiest way to open a folder as root is by installing the "nautilus-gksu" package. When you next log in, you can right-click a file or folder and choose "Open As Administrator".

---

