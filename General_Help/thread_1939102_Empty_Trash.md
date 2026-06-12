---
title: "Empty Trash"
date: 2012-03-10
forum: General Help
---

### Post by linux_trojan on 2012-03-10
I am using Ubuntu 11.10, in "classic" mode.   Where is the trash can?  Do you still need to empty it?

---

### Post by raja.genupula on 2012-03-10
bottom right corner i think , it should be there .

---

### Post by Diametric on 2012-03-10
Usually the thrash is locatd in the /home/user/trash path

Try that.

---

### Post by codemaniac on 2012-03-10
Just open a terminal and trash the trash .
```
rm -rf ~/.Trash/*
```

---

### Post by linux_trojan on 2012-03-10
I dont see a .Trash folder

---

### Post by raja.genupula on 2012-03-10
[http://ubuntuforums.org/showthread.php?t=1860565](http://ubuntuforums.org/showthread.php?t=1860565)

look at post # 2

---

### Post by 3rdalbum on 2012-03-10
> **linux_trojan said:**
> I dont see a .Trash folder

It's a hidden folder. Press Control H.

All folders starting with a . are hidden folders.

---

### Post by codemaniac on 2012-03-10
> **linux_trojan said:**
> I dont see a .Trash folder

Which version of Ubuntu you are using ?
In 11.10 trash resides here 
```
~/.local/share/Trash/
```

---

### Post by linux_trojan on 2012-03-11
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=1860565](http://ubuntuforums.org/showthread.php?t=1860565)

look at post # 2

I am also using LXDE.  How can I find this tweak tool there?  One computer has CLASSIC and the other LXDE.

---

### Post by linux_trojan on 2012-03-11
> **linux_trojan said:**
> I am also using LXDE.  How can I find this tweak tool there?  One computer has CLASSIC and the other LXDE.

NEVERMIND !!!  I just ran "gnome-tweak-tool" in Konsole and it worked.  Thanks for the info.

---

### Post by raja.genupula on 2012-03-11
so you found Trash ?

---

### Post by linux_trojan on 2012-03-11
I may have spoke too soon.  It appears that gnome tweak tool only works in Classic and not in LXDE.  I dont see a trash can in LXDE.

---

### Post by raja.genupula on 2012-03-11
What i know is LXDE using pcmanfm file manager and its not having Trash . so if you delete anything it will directly delete because of that file manager . 

if you change your file manager to thunar(its a light weight FM) then you can get Trash 

[http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html](http://www.ubuntugeek.com/switch-to-a-lightweight-filemanager.html)

---

### Post by linux_trojan on 2012-03-11
I see the trash can in pcmanfm, I can empty it.  Thats all I care about, that I can empty it and save on disk space.  Thank you for your help.

---

