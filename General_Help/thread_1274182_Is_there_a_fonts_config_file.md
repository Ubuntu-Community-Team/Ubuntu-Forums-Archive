---
title: "Is there a fonts config file?"
date: 2009-09-24
forum: General Help
---

### Post by sortia on 2009-09-24
Does anybody know where the location to the font size config file is? I take it the sizes are stored in a config file? I just cant find it!

I know I can set the font size in preferences - appearances, but im using switchconf to select between screens at boot (which is working) and I want the font sizes to be different on each screen!

Appreciate any help!

---

### Post by pmlxuser on 2009-09-24
its in home directory in a hidden folder .fontconfig

```

cd ~/.fontconfig

```

---

### Post by wojox on 2009-09-24
/etc/defoma/

---

### Post by sortia on 2009-09-24
> **pmlxuser said:**
> its in home directory in a hidden folder .fontconfig



Ok that doesn't seem to work, those files just seem to be cache files.

Im going to try wojox's suggestion now!

Thanks guys!

---

### Post by sortia on 2009-09-24
Ok the application font config file is:

~/.gconf/desktop/gnome/interface/%gconfig.xml

After I had set user permissions to the switchconf files/folders its working!

Thanks for putting me on the right track guys!

---

