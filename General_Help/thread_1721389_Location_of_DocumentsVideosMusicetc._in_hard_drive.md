---
title: "Location of Documents/Videos/Music/etc. in hard drive."
date: 2011-04-04
forum: General Help
---

### Post by abeam on 2011-04-04
So my 10.10 computer died on me a few weeks ago, and I've just got a new 10.04 machine up and running. I'm trying to pull some files off of the 10.10's hard drive via external connection, but I've got no idea where to look. In addition to that, I'm being told that I don't have the permissions to access several areas of the drive (like the root folder).

Where should I look, and how do I get the permissions to look there?

---

### Post by TeoBigusGeekus on 2011-04-04
Documents, Music, etc are in the
```
/home/yourusername
```
folder.

Assuming you use a live Ubuntu cd, you could start nautilus with root priviledges from terminal
```
gksu nautilus
```

---

### Post by abeam on 2011-04-04
Great, I found everything I needed. Thanks. :)

---

### Post by Anonymous is Incognito on 2011-04-04
If you find yourself in another situation like this, but you need to access the root folder, you can change the permissions of the drive with chmod.

```
chmod 777 'the concerning harddrive'
```

---

