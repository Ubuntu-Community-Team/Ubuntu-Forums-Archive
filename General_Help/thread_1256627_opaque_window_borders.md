---
title: "opaque window borders"
date: 2009-09-02
forum: General Help
---

### Post by Kristofer Van Orton on 2009-09-02
okay im sorry im sure that people have asked this a thousand times
well okay i managed to get opaque backgrounds on my application menu using compizconfig but i still cant figure out how to make the window borders opaque
so can anyone tell me how to do this?
-KVO

---

### Post by ad_267 on 2009-09-02
Are you sure you mean opaque, not transparent? I'm a bit confused because by default in Ubuntu with Compiz, the window borders of inactive windows are transparent but the applications menu is opaque.

If you really do want opaque window borders, see this thread: [http://ubuntuforums.org/showthread.php?t=864564](http://ubuntuforums.org/showthread.php?t=864564)

---

### Post by coldReactive on 2009-09-02
Are you using emerald?

If not, then you'll need to set the metacity to do so. If you use metacity:

ALT+F2 and type in gconf-editor, then hit run/OK.

After that, go to apps/gwd and set metacity_theme_xxxxx_opacity to your liking. Keep in mind that the blur_type option is for what it takes, all or titlebar.

---

### Post by Kristofer Van Orton on 2009-09-02
i tried emerald and i have installed it and also installed some themes on it but i dont know how to change the theme with that

---

### Post by coldReactive on 2009-09-02
> **Kristofer Van Orton said:**
> i tried emerald and i have installed it and also installed some themes on it but i dont know how to change the theme with that

After selecting a theme:

ALT+F2 and type in **emerald --replace**. (You will NOT need to do this again each time you select a theme.)

To keep emerald starting up when the computer does:

System > Preferences > Startup Applications/Sessions

Click Add, then name it Emerald Theme Manager and then put in emerald --replace for the command. Hit OK on both dialogs.

---

### Post by Kristofer Van Orton on 2009-09-02
> **coldReactive said:**
> After selecting a theme:

ALT+F2 and type in **emerald --replace**. (You will NOT need to do this again each time you select a theme.)

To keep emerald starting up when the computer does:

System > Preferences > Startup Applications/Sessions

Click Add, then name it Emerald Theme Manager and then put in emerald --replace for the command. Hit OK on both dialogs.
 
 thank you it worked

---

