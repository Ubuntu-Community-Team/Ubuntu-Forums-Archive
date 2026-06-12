---
title: "auto terminal comands?"
date: 2010-04-06
forum: General Help
---

### Post by Fenderian_Mayhew on 2010-04-06
is there a way to setup a file to click that will auto activate commands?

example, i want to load a program on wine and jump straight to it. but the program is in "program files" and  "fallout tactics" so to load in terminal i have to use 

$ cd ~/.wine/dosdeviecs/c:/Program\ Files/Interplay/Fallout\ Tactics/
$ wine BOS.exe -wg

and i want to find a way to activate BOS.exe with -wg either by a launcher or by the "configure wine" options but i dont know what -w or -g associate with?

---

### Post by dominiquec on 2010-04-06
You could write a shell script to do that.  See [https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html), for instance.  

Basically, just put those commands into a file and change the permissions of the file

```
chmod +x script.sh
```

---

