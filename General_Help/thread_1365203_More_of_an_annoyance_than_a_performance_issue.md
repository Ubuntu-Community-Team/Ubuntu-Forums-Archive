---
title: "More of an annoyance than a performance issue"
date: 2009-12-26
forum: General Help
---

### Post by rtyb on 2009-12-26
So i don't know but my firefox doesn't display search engines icons

btw, sorry for the big image, don't know how to resize them :\


[IMG]http://img526.imageshack.us/img526/9127/screenshotxc.png[/IMG]

---

### Post by Ben Wright on 2009-12-26
I am sorry but I do not quite understand your question are you having trouble with the drop down search engine icon system in ubuntu not showing the icons? I believe in the current firefox releases for Ubuntu the icons are not shown by default. If you find that this issue is really bugging you, you could always post a bug report on launchpad. Thanks.

---

### Post by howefield on 2009-12-27
Fix this by opening a terminal, (Applications > Accessories > Terminal) and type

```
gconf-editor
```

Navigate to desktop > gnome > interface and check the box beside "menus_have_icons"

Does this do it for you ?

---

### Post by Shpongle on 2009-12-27
im sure theres an option in about:config , thats where all the firefox preferences/options are set

---

### Post by Uncle Spellbinder on 2009-12-27
@ rtyb

Try here: [http://forums.mozillazine.org/viewforum.php?f=49](http://forums.mozillazine.org/viewforum.php?f=49)

You're likely to get quicker Firefox-specific support there. 

Hope that helps.

---

### Post by howefield on 2009-12-27
Don't think it is Firefox specific, it seems tied to the recent gnome decision to drop menu icons.

Editing gconf-editor did it for me.

Should also have said above, if you have Firefox running when you change the option, you'll need to close Firefox and restart for the option to take effect.

---

