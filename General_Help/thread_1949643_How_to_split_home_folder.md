---
title: "How to split home folder"
date: 2012-03-30
forum: General Help
---

### Post by bobman321123 on 2012-03-30
I'd like to store most of my games, programs, music, documents, etc ect, in a seperate, centralized location, but I don't know how to link them from that location to my home folder. 
Help?

---

### Post by TeoBigusGeekus on 2012-03-30
You can create soft links to the folders inside your home folder, ie.
```
ln -s /path/games/ ~/Games
```
etc.

---

### Post by bobman321123 on 2012-03-30
Say I wanted to link Music to my music.
In my home folder, just delete the original music folder?

Also, how do I store application data on the other drive/partition?

---

### Post by TeoBigusGeekus on 2012-03-30
> **bobman321123 said:**
> Say I wanted to link Music to my music.
In my home folder, just delete the original music folder?
I don't think that's necessary. Just
```
ln -s "/path/My Music" ~/Music/
```
I'm not sure though, try it and post back.

> **bobman321123 said:**
> 
Also, how do I store application data on the other drive/partition?
Again, create symbolic links from your home folder to the other partition.

---

### Post by bobman321123 on 2012-03-30
If I'm using wine, and I make a link to .wine, will wine be able to tell that it's supposed to use the link to .wine folder?

---

### Post by TeoBigusGeekus on 2012-03-30
There's only one way to find out...

---

