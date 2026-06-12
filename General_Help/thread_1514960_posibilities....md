---
title: "posibilities..."
date: 2010-06-21
forum: General Help
---

### Post by killer62491 on 2010-06-21
is it possible to use a terminal to install/run currently installed WINE apps...? if so, please let me know how to do so, i'm trying to run my guild wars game client, and its saying that the program doesn't have sufficient priveleges to run... thanks beforehand. 

EDIT: i think i figured it out, but it gives me this code: 
wine: /home/ahs62491/.wine is not owned by you
any clues as to whats up...? thanks beforehand =P

.::ALPHA::HECTOR::SIERRA::.

---

### Post by 3Miro on 2010-06-21
Try
```
ls -al /home/ahs62491/.wine
```

You should get something along the lines of:
```

drwxrw-rw- ... ahs62491 ahs62491 ...

```

If it is anything other than ahs62491, then you will have to run
```

sudo chown -R ahs62491:ahs62491 /home/ahs62491/.wine

```

I hope this helps.

The error indicates that someone else owns the folder, which can happen if you installed the game as another user. "chown" is the command that changes the ownership of files.

---

### Post by killer62491 on 2010-06-23
ok..... i got to do the abovementioned terminal code, and it no longer says the error message, but now it says that it (guildwars) doesn't have the privileges to run.....
also, how would one use sudo privileges to run an installed wine app...?

thanks again,

.::ALPHA::HECTOR::SIERRA::.

---

