---
title: "Can't find installed game ... (installed with wine)"
date: 2012-04-19
forum: General Help
---

### Post by Petar Stoyanov on 2012-04-19
So i downloaded Monkey Island 2 - iso file. I mounted it using terminal with the command:
mount -o loop file/directory/filename.iso /mnt/disk
then i used the command: wine setup.exe
Wine showed up, I browse a directory and the game was installed.

However when i try to find where the game is the directory just don't exist. I try in 
.wine/drive_c/Program Files where it should be , but there's nothing there. I installed the game 3 times using different paths and my total disk space was getting smaller every time ... so there's got to be  games installed on my computer. None of the directories showed up. The .wine folder is only 87 Mb, while there's got to be 3 games around 2Gb each.
I'm using Ubuntu 11.10, and wine-1.3.28

How can I find out what happened and where are the games ...
Thanks for the help!

---

### Post by jwbrase on 2012-04-19
Could you post the output of:

```
ls -al "~/.wine/drive_c/Program Files"
```

---

