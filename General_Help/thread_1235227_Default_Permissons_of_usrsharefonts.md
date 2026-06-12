---
title: "Default Permissons of /usr/share/fonts"
date: 2009-08-08
forum: General Help
---

### Post by SnarlSlayer on 2009-08-08
Greetings!

I searched for this on the forum but either my search skills are lacking or it could just be a stupid question.

I changed the permissions on /usr/share/fonts so I could copy some fonts into the folder.

Genius that I am, I didn't check the permissions of the folder before I did it, so now I have no idea of what I should reset it to.

The question is:  What are the default permissions on /usr/share/fonts  ?

I'm using 9.04


SS

---

### Post by abhilashm86 on 2009-08-08
> **SnarlSlayer said:**
> Greetings!

I searched for this on the forum but either my search skills are lacking or it could just be a stupid question.

I changed the permissions on /usr/share/fonts so I could copy some fonts into the folder.

Genius that I am, I didn't check the permissions of the folder before I did it, so now I have no idea of what I should reset it to.

The question is:  What are the default permissions on /usr/share/fonts  ?

I'm using 9.04


SS
```

abhilash@abhilash:~$ ls /usr/share/fonts/ -l
total 12
drwxr-xr-x 16 root root 4096 2009-07-22 07:54 truetype
drwxr-xr-x  3 root root 4096 2008-04-23 03:22 type1
drwxr-xr-x  8 root root 4096 2008-04-23 03:26 X11


```
as you see the file owner is root, if you want to copy those things, use sudo.....
like,
```

gksudo nautilus 

```
you have one more option, change ownership of file using chown command:)

---

