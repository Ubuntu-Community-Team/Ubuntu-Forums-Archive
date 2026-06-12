---
title: "error with dpkg"
date: 2009-09-18
forum: General Help
---

### Post by VideoAddicted on 2009-09-18
whenever i try to run anything along the lines of downloading straight from terminal or trying to update in the update manager i get an error stating that dpkg was interrupted and a code snippet is suggested, then when the code snippet is run, i'm told i don't have the privileges to run the code even though i'm the administrator, below i have the specific error that i get in update manager.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

also, i am running 8.04 hardy, in case that helps.

---

### Post by drs305 on 2009-09-18
Have you run the command as:
```
sudo dpkg --configure -a
```
Open a terminal: Applications, Accessories, Terminal
Enter your password when asked, you won't see it as you type.

This command must be run as 'root', thus you need "sudo" and your password to run the command.

---

### Post by VideoAddicted on 2009-09-18
i put in the suggested snippet and while i'm no longer denied access, the code continues and proclaims that it has 'failed', as shown below.

Setting up nis (3.17-12ubuntu1) ...
*Starting NIS services                                                         
*binding to YP server...                                                       *....                                                                          *....                                                                          *....                                                                          *....                                                                          *....                                                                          *....                                                                          *....                                                                          *....                                                                          *....                                                                          *....                                                                  [fail] 
                                                                         [ OK ]

does this mean that it didn't work? it is followed by an 'ok', so i'm not sure.

---

### Post by VideoAddicted on 2009-09-19
good news, my computer suddenly started working this morning despite no new changes.

---

