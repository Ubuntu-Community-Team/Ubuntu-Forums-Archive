---
title: "rc.local"
date: 2009-09-26
forum: General Help
---

### Post by Anman on 2009-09-26
Hello, I was just wondering what the rc.local is chmoded to by default.

I'm new to ubuntu and had to edit it so I did *chmod 777 rc.local* and now I'd like to know what to set it back to.

Does anyone know this?

---

### Post by chili555 on 2009-09-26
```
chili@LAPTOP60:~$ ls -al /etc/rc.local
-rwxr-xr-x 1 root root 380 2009-04-29 11:03 /etc/rc.local
```

---

### Post by Anman on 2009-09-26
So I assume I'd do:

[I]chmod 380 /etc/init.d/rc.local
[/I]
right?

And thanks for your help. :)

---

### Post by The Cog on 2009-09-26
```
sudo chmod 755 /etc/init.d/rc.local
```
Don't go changing the permissions of these files - you should temporarily elevate your own permissions instead, like borrowing the janitor's keys. This reference explains:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Anman on 2009-09-26
> **The Cog said:**
> ```
sudo chmod 755 /etc/init.d/rc.local
```Don't go changing the permissions of these files - you should temporarily elevate your own permissions instead, like borrowing the janitor's keys. This reference explains:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Thanks but I know that now. :)

---

