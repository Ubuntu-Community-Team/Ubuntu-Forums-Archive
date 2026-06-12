---
title: "Nautilus Breadcrumb problem"
date: 2009-08-20
forum: General Help
---

### Post by AwesomeTux on 2009-08-20
The "[Breadcrumb]("http://en.wikipedia.org/wiki/Breadcrumb_%28navigation%29")" navigation in Nautilus, you are supposed to be able to drag and drop files on to the Breadcrumb navigation bar and the file will be move to the folder the file was dropped on.

Example, my location is "Home>Documents>My Cool Stuff" if I were to drag and drop a file on "Documents" on the Breadcrumb navigation bar, the file will end up in my "Documents" directory. This is useful for moving files from one directory to the previous one, without opening any tabs.

But for some reason I can't do this anymore, all that happens is a border appears around "Documents" and I can't move the file to that directory, and the border doesn't disappear when I hover-off the Breadcrumb.

Any ideas what could be going on?

Nautilus: 2.26.3

---

### Post by AwesomeTux on 2009-08-22
The border appears and remains when dragging an item over the tabs as well.

Here is the output of "gksu nautilus":
```

Initializing nautilus-open-terminal extension

** (nautilus:29685): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///

(nautilus:29685): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:29685): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
Shutting down nautilus-open-terminal extension

```

---

### Post by Copernicus1234 on 2009-08-22
It could have something to do with some extension, if any, that you have installed for Nautilus I guess. I tried this and it works for me. I dont have that nautilus-open-terminal extension you have though. It seems like it might be causing the problem.

---

### Post by AwesomeTux on 2009-08-22
> **Copernicus1234 said:**
> It could have something to do with some extension, if any, that you have installed for Nautilus I guess. I tried this and it works for me. I dont have that nautilus-open-terminal extension you have though. It seems like it might be causing the problem.

No luck. Uninstalled, restarted Nautilus, still there, and this problem preexisted any of my Nautilus extensions for me.

I am using Nautilus on Ubuntu 9.04 64bit, and I didn't have this problem on 32bit, could this possibly be a bug in Nautilus for 64bit? Or a related library? 

Or maybe permissions on Nautilus files?

---

### Post by AwesomeTux on 2009-08-22
I've submitted a bug [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/417336](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/417336)

---

