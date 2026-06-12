---
title: "Library files &quot;too short&quot;"
date: 2010-02-14
forum: General Help
---

### Post by MrNatewood on 2010-02-14
I am using Ubuntu Karmic 64-bit on my Dell 1555 laptop.

Some software won't start, giving an error of a too short library.
Latest examples:
```
mrnatewood@mrnatewood-laptop:~$ mplayer
mplayer: error while loading shared libraries: /usr/lib/libx264.so.67: file too short
mrnatewood@mrnatewood-laptop:~$ supertux2
supertux2: error while loading shared libraries: /usr/lib/libSDL_image-1.2.so.0: file too short

```

Tried re-installing the libraries, didn't help.
What can I do?

---

### Post by sanderj on 2010-02-14
What's the size of /usr/lib/libx264.so.67 ?

See mine below.


```
sander@quirinius:~$ ls -al /usr/lib/libx264.so.67 
-rw-r--r-- 1 root root 628308 2009-06-21 19:18 /usr/lib/libx264.so.67
sander@quirinius:~$ 
```

If your file is much smaller, or missing, consider reinstalling the package libx264-67 / libx264. See [http://packages.ubuntu.com/karmic/libx264-67](http://packages.ubuntu.com/karmic/libx264-67) for an example package.

---

### Post by MrNatewood on 2010-02-15
Thnaks, for some reason re-installing for the second time worked. Go figure.

---

