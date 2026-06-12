---
title: "Unity Search for files not working"
date: 2011-05-09
forum: General Help
---

### Post by Martin_sensei on 2011-05-09
Hello,

Is there anything special I need to do to get file searching working in Unity?

Currently Search for Files never finds anything in my documents area.  I just get "Your Search did not match any files"

---

### Post by mc4man on 2011-05-09
The 'Search for Files & Folders' in the unity dash or launcher icon only looks/finds files that you've previously opened in some manner

The old 'search for files' tool will search for any that exist
(gnome-search-tool

---

### Post by dc46and2 on 2011-05-13
Wouldn't it be more accurate to name it "Search for Recently Opened Files and Folders"?

---

### Post by mc4man on 2011-05-13
> **dc46and2 said:**
> Wouldn't it be more accurate to name it "Search for Recently Opened Files and Folders"?


Maybe - file a bug on, it's a simple source edit, maybe like in screen?
(though for personal use one can have that line say whatever they wish - 
```
gksudo gedit /usr/share/unity/places/files.place
```

the SearchHint= line is what will show in the file place lens

---

### Post by robinmurray on 2011-05-30
Hi there,

I also found it annoying that it would only search recent files.

Try this solution, not mine I just found it.
[http://www.addictivetips.com/ubuntu-linux-tips/search-files-and-folders-faster-in-unity-with-new-unity-lens/](http://www.addictivetips.com/ubuntu-linux-tips/search-files-and-folders-faster-in-unity-with-new-unity-lens/)

this adds another "lens" that will search the filesystem.

Hope this helps

Robin

---

