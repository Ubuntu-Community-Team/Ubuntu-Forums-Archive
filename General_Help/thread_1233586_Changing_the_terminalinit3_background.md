---
title: "Changing the terminal/init3 background ??"
date: 2009-08-06
forum: General Help
---

### Post by xterminal01 on 2009-08-06
I just was wondering if it would be possible to change the background of the plain black terminal when i go into the init3 or whatever its called something like this..  

[http://www.kde-look.org/content/preview.php?preview=1&id=87663&file1=87663-1.png&file2=87663-2.png&file3=87663-3.png&name=Ebola](http://www.kde-look.org/content/preview.php?preview=1&id=87663&file1=87663-1.png&file2=87663-2.png&file3=87663-3.png&name=Ebola)

---

### Post by scouser73 on 2009-08-07
This is possible, you need to open Terminal up, go to **Edit > Profile Preferences > Background** [[COLOR="Red"]**Terminal Image**[/COLOR]]("http://img36.imageshack.us/img36/438/screenshotayk.png")

---

### Post by CatKiller on 2009-08-07
> **xterminal01 said:**
> I just was wondering if it would be possible to change the background of the plain black terminal when i go into the init3 or whatever its called something like this..  

[http://www.kde-look.org/content/preview.php?preview=1&id=87663&file1=87663-1.png&file2=87663-2.png&file3=87663-3.png&name=Ebola](http://www.kde-look.org/content/preview.php?preview=1&id=87663&file1=87663-1.png&file2=87663-2.png&file3=87663-3.png&name=Ebola)

That isn't what that is. That's a standard desktop environment with a borderless transparent terminal window being drawn. There's a how-to somewhere on this forum. The gist of it is that you set up a terminal profile with a transparent background and the colours that you want, have a terminal window with that profile launch automatically on login, and then use devilspie to manage the position of that window and draw it without borders.

---

### Post by decoherence on 2009-08-07
If you want to do this on your virtual consoles, which is what it sounds like you want to do (as opposed to an x terminal,) use the setterm command

```
setterm -background magenta
setterm -foreground yellow
clear
```

you may wish to shield your eyes before running these commands ;)

man setterm for more info

---

