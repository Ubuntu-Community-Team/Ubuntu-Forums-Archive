---
title: "I installed wine, yet I have no ~/.wine"
date: 2011-05-07
forum: General Help
---

### Post by ryandward on 2011-05-07
I have tried wine 1.2 and wine 1.3, but I still don't have a wine directory, I am so confused. What am I supposed to do?

I used sudo apt-get install wine1.3

---

### Post by synapsys on 2011-05-07
Have you tried showing hidden files? Files that start with a . in Linux are hidden.

---

### Post by Throne777 on 2011-05-07
> **ryandward said:**
> I have tried wine 1.2 and wine 1.3, but I still don't have a wine directory, I am so confused. What am I supposed to do?

I used sudo apt-get install wine1.3

The wine directory is hidden. You'll find it in your home folder if you make nautilus show you hidden files (View -> Show Hidden Folders).

---

### Post by ryandward on 2011-05-07
Yeah, I am showing hidden files, it's not there. I can't see it through Nautilus or Terminal.

---

### Post by SavageWolf on 2011-05-07
Have you used wine yet? The folder is created the first time you use it, not on install.

---

### Post by ryandward on 2011-05-07
Doh :( Thanks

---

### Post by matt_symes on 2011-05-07
Hi

Try running winecfg as well to configure Wine. This will create your wine directory.

```
matthew@matthew-laptop:~$ winecfg
wine: created the configuration directory '/home/matthew/.wine'
<snip>
```

kind regards

---

