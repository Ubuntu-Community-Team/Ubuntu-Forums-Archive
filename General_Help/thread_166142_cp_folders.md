---
title: "cp folders"
date: 2006-04-25
forum: General Help
---

### Post by kasemodz on 2006-04-25
I have this raw image and I've mounted it on a folder. It is root right now, so in terminal I tried to copy that folder into another location and it copies everything except folders. Any clue why? I tried putting a-r and that didn't work.

---

### Post by jazzmuzik on 2006-04-25
Root folders might require extra priviledges to copy them. Use sudo for that. "a-r" is a malformed pair of options. Just use -a, it implies -r.

sudo cp -a /source /destination

BTW, to use multiple options use something like -xy or -x -y. Not x-y.

---

### Post by enopepsoo on 2006-04-25
and if the file is owned by root you may need to do something like
```
sudo chmod +777 masterfulphotography.raw
```
This will give absolutely any user on the system access to the file.
[chmod]("http://www.computerhope.com/unix/uchmod.htm") info.

---

### Post by Toxicity999 on 2006-04-26
sudo chown usernamehere /path/to/whatever.ext that will give you complete ownership to edit things as you will... the chmod suggestion still applies though.

---

