---
title: "Help?"
date: 2010-02-05
forum: General Help
---

### Post by TheLinuxUser on 2010-02-05
Running 9.10, Karmic Koala

So I wanted to replace my password prompt with this: 
[http://www.gnome-look.org/content/show.php/Homeland+Security+Password+Prompt?content=91742](http://www.gnome-look.org/content/show.php/Homeland+Security+Password+Prompt?content=91742)

it says to write it over the system files in ubuntu, under usr/share/gnome-screensaver

but i cant do that, as it says permissions are denied... 

how do i do this??

---

### Post by howefield on 2010-02-06
Do it with elevated rights.

Open the file manager by typing into a terminal...

```
gksudo nautilus
```

This will give you the ability to overwrite the file, so navigate to the required folder and copy/move the file you want, but be careful not to destroy the wrong stuff.

---

### Post by stoneage on 2010-02-06
> **howefield said:**
> 

..... but be careful not to destroy the wrong stuff.

Indeed, it might be a good idea to backup or rename the system files first.....

---

