---
title: "How to enable Nautilus thumbnails for RW2 format"
date: 2010-06-04
forum: General Help
---

### Post by GreaterCore on 2010-06-04
I am currently using Ubuntu 10.04 and is stuck in enabling RW2 thumbnails under Nautilus. I have successfully installed "ufraw" and "gimp-ufraw" packages. They are tested to be working.

Any ideas on how to get the thumbnails out when exploring a directory? The icon appears like a black screen at the moment. Any help is greatly appreciated.

---

### Post by Leppie on 2010-06-04
try installing the libopenrawgnome1 package:
```
sudo apt-get install libopenrawgnome1
```

---

### Post by GreaterCore on 2010-06-11
Thanks to Leppie who offered help.

I got it to work by using
```
rm ~/.thumbnails/fail/gnome-thumbnail-factory/*
```

The code above deletes off all the references to failed thumbnail generation and enables Nautilus to generate them. I have previously installed and configured the system to display RW2 thumbnails, but it is not retroactive thus requiring the deletion of the said references.

I will be closing this thread once I managed to figure out exactly what packages are to be installed and what files to tweak before deleting the failed thumbnails.

---

### Post by John Bean on 2010-06-11
> **GreaterCore said:**
> I have previously installed and configured the system to display RW2 thumbnails, but it is not retroactive thus requiring the deletion of the said references.

Could you explain how you configured it? It would be handy if I could see thumbs of .rw2 files too and have failed to make it work so far (although I haven't tried very hard!)

---

