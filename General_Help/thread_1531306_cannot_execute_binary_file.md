---
title: "cannot execute binary file"
date: 2010-07-14
forum: General Help
---

### Post by zespri on 2010-07-14
Hello I have a strange issue on one of my machines. The same thing works fine on all the others.
When I execute:
```
sudo -u myuser -i ls
```
I get: 
```
/bin/ls: /bin/ls: cannot execute binary file
```

On the other hand if I just run
```
sudo -u myuser -i
```
and then run ls, it executes successfully, but I don't want to stay logged in as myuser I just want to run a single command.

Why is this happening and how do I resolve this?

Cheers,
Andrew

---

### Post by prodigy_ on 2010-07-14
Broken /bin/ls perhaps? Try ```
/bin/ls
``` command without sudo to see if works at all. And also ```
stat -c "%A %U %G" /bin/ls
``` to see if permissions are right.

---

### Post by zespri on 2010-07-14
Thank you for getting back to me.

> **prodigy_ said:**
> Try /bin/ls command without sudo to see if works at all.

It does work perfectly

> **prodigy_ said:**
> And also stat -c "%A %U %G" /bin/ls to see if permissions are right.

This gives:
```
-rwxr-xr-x root root
```

I see nothing wrong with this.

---

