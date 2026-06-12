---
title: "how to make permissions?"
date: 2011-04-08
forum: General Help
---

### Post by rahulbest on 2011-04-08
i cannt create folder or open some of the files in var/www ....what to do so that i can create folder,read  and write and execute files...
plz help me out

---

### Post by wolfen69 on 2011-04-08
You need to be root to do this. Open a terminal and:
```
gksudo nautilus
```
then navigate to the directory you want and make the changes. Just be careful as root.

---

### Post by Joe of loath on 2011-04-08
Or, open a terminal and type

```
sudo chown -R (username) /var/www
```

---

### Post by Enigmapond on 2011-04-08
> **Joe of loath said:**
> Or, open a terminal and type

```
sudo chown -R (username) /var/www
```

Well I would refrain from changing permissions in the file system. Kinda defeats the purpose. Better to do it temporarily with nautilus.

---

### Post by Joe of loath on 2011-04-08
True, although on my server it's made scripting and updating easier, especially if I don't want to give some people sudo access.

---

### Post by Enigmapond on 2011-04-08
> **Joe of loath said:**
> True, although on my server it's made scripting and updating easier, especially if I don't want to give some people sudo access.

Wow, are YOU living on the edge, especially running a server....NO ONE gets access to my file system. Not even ME without TEMPORARILY being root. But that's me.... :)

---

### Post by Joe of loath on 2011-04-08
Well, that server's sat idle for a while now, and no one's hacked it, so I assume it's fine XD My production server (running a forum) is a little more locked down.

---

