---
title: "Reset terminal colors from profile"
date: 2012-02-22
forum: General Help
---

### Post by altjx on 2012-02-22
I am actually using BackTrack 5/Gnome, and wondering how to reset my Terminal colors back to the default settings.

---

### Post by raja.genupula on 2012-02-22
[http://askubuntu.com/questions/14487/how-to-reset-the-terminal-properties-and-preferences](http://askubuntu.com/questions/14487/how-to-reset-the-terminal-properties-and-preferences)

---

### Post by altjx on 2012-02-22
> **raja.genupula said:**
> [http://askubuntu.com/questions/14487/how-to-reset-the-terminal-properties-and-preferences](http://askubuntu.com/questions/14487/how-to-reset-the-terminal-properties-and-preferences)

Tried to remove the gnome-terminal, but that didn't fix the problem. Colors are still the same.

---

### Post by bluexrider on 2012-02-22
The correct  way 

```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

This will reset the gnome terminal back to OEM configuration

---

### Post by altjx on 2012-02-22
> **bluexrider said:**
> The correct  way 

```
gconftool-2 --recursive-unset /apps/gnome-terminal
```

This will reset the gnome terminal back to OEM configuration

This actually set it back to something I've never seen before. Eh...

---

### Post by raja.genupula on 2012-02-22
> **altjx said:**
> Tried to remove the gnome-terminal, but that didn't fix the problem. Colors are still the same.


Remove gnome terminal ? in the link i have given to you , i havent seen anything like that .. look at the first answer . If you are in the Ubuntu with the basic theme then its easier to get back to default color  . 

tell me , what you have tried  tried ? If you tried any commands i need terminal flow of that .

---

### Post by altjx on 2012-02-22
> **raja.genupula said:**
> Remove gnome terminal ? in the link i have given to you , i havent seen anything like that .. look at the first answer . If you are in the Ubuntu with the basic theme then its easier to get back to default color  . 

tell me , what you have tried  tried ? If you tried any commands i need terminal flow of that .

I don't mean gnome terminal literally. I meant the apps/gnome-terminal folder, sorry. I was able to restore it, but I used someone else's default colors to just match my RGB settings with theirs. tHanks

---

