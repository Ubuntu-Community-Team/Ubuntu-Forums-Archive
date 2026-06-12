---
title: "help???"
date: 2010-02-06
forum: General Help
---

### Post by TheLinuxUser on 2010-02-06
Running 9.10, Karmic Koala

So I wanted to replace my password prompt with this: 
[http://www.gnome-look.org/content/show.php/Homeland+Security+Password+Prompt?content=91742](http://www.gnome-look.org/content/show.php/Homeland+Security+Password+Prompt?content=91742)

it says to write it over the system files in ubuntu, under usr/share/gnome-screensaver

but i cant do that, as it says permissions are denied... 

how do i do this??

---

### Post by cariboo on 2010-02-06
This isn't a security question. Moved to General Help.

You will have to run file-roller as root in order to extract the files to usr/share/gnome-screensaver. Press Alt-F2 and type:

```
gksu file-roller
```

Enter your password, and extract the files to where you want.

---

### Post by howefield on 2010-02-06
Actually, it is a duplicate post.

Original posted in General Help, 9 hours previously :)

---

