---
title: "how to get full admin rights without using sudo command?"
date: 2009-07-20
forum: General Help
---

### Post by serious7 on 2009-07-20
Hi how do i enable full admin rights? I want to change files in usr/local/lib section manually thru the browser and not in the terminal but I keep getting a "access denied you do not have privilege to do this action" stuff.

---

### Post by grayn0de on 2009-07-20
> **serious7 said:**
> Hi how do i enable full admin rights? I want to change files in usr/local/lib section manually thru the browser and not in the terminal but I keep getting a "access denied you do not have privilege to do this action" stuff.

From Terminal:
```
gksudo nautilus
```

That will open a root Nautilus window.

---

### Post by bacil on 2009-07-20
I guess easiest to get something like krusader and use it in admin mode. what dm are you using ?

---

### Post by ACMiller on 2009-07-20
A better solution :
Rather than using something like krusader (which isn't a native gnome app) you could incorporate grayn0de's method to make a root nautilus launcher on your panel:

Right click on your panel, click 'add to panel' and then add a Custom Application Launcher. Once this has been added, right click on the new laucher and click 'properties'. Here you can put Root Nautilus or anything like that under name, and under command put > gksu nautilus. Also, make sure the type is Application.

Now when you click that launcher a window opens asking you for the password, then you're good to go.

Hope this helps.

---

### Post by michy99 on 2009-07-20
I would add to be careful what you do in a root nautilus session, and close it out as soon as you finish what you are doing. It is easy to forget that it is running as root, and you might do something you will regret later.

---

### Post by CatKiller on 2009-07-20
> **michy99 said:**
> I would add to be careful what you do in a root nautilus session, and close it out as soon as you finish what you are doing. It is easy to forget that it is running as root, and you might do something you will regret later.

+1.

My favoured method is to make the nautilus window, when run as root, strikingly ugly, so you aren't tempted to use it any more than strictly necessary. Salmon pink is such a *lovely* colour, don't you think?

---

### Post by The Cog on 2009-07-20
> **CatKiller said:**
> +1.

My favoured method is to make the nautilus window, when run as root, strikingly ugly, so you aren't tempted to use it any more than strictly necessary. Salmon pink is such a *lovely* colour, don't you think?

Spooky! That's the background colour I set my root nautilus to! I tried poster red, but it's just too violent on the eyeballs.

---

### Post by CatKiller on 2009-07-20
> **The Cog said:**
> Spooky! That's the background colour I set my root nautilus to! I tried poster red, but it's just too violent on the eyeballs.

Well, it's red (as a warning), but it's not so red that you can't get anything done. Besides, a really dramatic red might look good with some striking desktop themes. You wouldn't want that. Convergent evolution at work :)

---

