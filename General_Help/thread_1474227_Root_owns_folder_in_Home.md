---
title: "Root owns folder in Home"
date: 2010-05-05
forum: General Help
---

### Post by Lolpanda on 2010-05-05
As the title suggests. I have a Hidden folder in my home directory, " .Ut2004 " its a game folder from when I installed Unreal Tournament a few weeks back. Never understood why it wouldnt play but I guess I know now. 

Havent had to use terminal for ownership, can someone tell me the command to change the ownership of that folder, and all subfolders, from root to myself?

---

### Post by WorMzy on 2010-05-05
```
chown -R USERNAME:USERGROUP /home/.ut2004
```


Note: unless you've set it up differently, USERGROUP will usually be the same as your username. You can omit the ":USERGROUP" if you want and just do

```
chown -R USERNAME /home/.Ut2004
```

EDIT: you should use sudo chown, since root currently owns it, not chown.

---

### Post by MooPi on 2010-05-05
```
 sudo chown -R yournamehere /directory/location
```

---

### Post by Jonny87 on 2010-05-05
I have recently just done this after finding that the button on the permissions window to apply to sub folders and files didn't work.

---

