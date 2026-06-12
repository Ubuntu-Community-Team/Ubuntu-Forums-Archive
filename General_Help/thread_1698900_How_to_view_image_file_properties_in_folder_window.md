---
title: "How to view image file properties in folder windows - height width"
date: 2011-03-02
forum: General Help
---

### Post by nloxford on 2011-03-02
I am trying to sort image files I've assembled for document production, and I need to be able to see the height and width of the images without having to open them one by one. Is there a way to view an image's physical size in the folder window?

---

### Post by TeoBigusGeekus on 2011-03-03
I don't know how to do it in gui, but in cli install feh
```
sudo apt-get install feh
```
and then
```
feh -l /path/to/pics/*
```

---

