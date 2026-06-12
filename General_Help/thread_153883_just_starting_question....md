---
title: "just starting question..."
date: 2006-04-01
forum: General Help
---

### Post by Dmitridj on 2006-04-01
Alright, I'm trying to get the mplayer-mozilla plugin to work for .avi and .wmv files...I can play everything else (like [www.apple.com/trailers](www.apple.com/trailers)) but on websites like [www.adultswim.com](www.adultswim.com) or cnn.com I get a grey screen and sometimes a beeping sound. I found a how-to earlier and it said to create a new folder called win32 in the File System >  usr > local > lib However, when I right click to create a new folder, the option isnt clickable. Any help would be great

Thanks,
Addison

---

### Post by dcstar on 2006-04-02
[QUOTE=Dmitridj]Alright, I'm trying to get the mplayer-mozilla plugin to work for .avi and .wmv files...I can play everything else (like [www.apple.com/trailers](www.apple.com/trailers)) but on websites like [www.adultswim.com](www.adultswim.com) or cnn.com I get a grey screen and sometimes a beeping sound. I found a how-to earlier and it said to create a new folder called win32 in the File System >  usr > local > lib However, when I right click to create a new folder, the option isnt clickable. Any help would be great

Thanks,
Addison[/QUOTE]
Open a terminal (or create a launcher):
```
gksudo "nautilus --browser %U"
```

---

