---
title: "AWN Installed - How To Delete Both Panels?"
date: 2009-12-04
forum: General Help
---

### Post by Uncle Spellbinder on 2009-12-04
Now that I have AWN installed, I see no need for either panel. For the time being, I've eliminated the top panel (actually, the first thing I do on a fresh install of Ubuntu is eliminate the top panel). The bottom panel I've made transparent and made it the same height as AWN.

Is there a way to delete both panels when neither is needed/necessary?

---

### Post by Uncle Spellbinder on 2009-12-04
Bump

EDIT:
Nevermind. Did further searching and found a solution to try from [http://ubuntuforums.org/showthread.php?p=8280994#post8280994](http://ubuntuforums.org/showthread.php?p=8280994#post8280994)

> **Paqman said:**
> There's a setting in your gconf that you'll have to modify to allow you to get rid of the last panel.

1. press Alt + F2
2. type gconf-editor
3. click Run
4. in the Configuration Editor look for panel under desktop > gnome > session > required_components
5. right-click panel and select Edit Key..
6. delete gnome-panel
7. click OK

Log out then log in again and you should be good to go.

---

### Post by Grenage on 2009-12-04
Can you not simply right-click on the panel and select *"delete this panel"*?

---

### Post by Uncle Spellbinder on 2009-12-04
> **Grenage said:**
> Can you not simply right-click on the panel and select *"delete this panel"*?

Nope, as when only one panel is left, that option is grayed out. I'm going to try the suggestion from the other thread I located and see if it works.

---

### Post by Grenage on 2009-12-04
That's really odd, the option isn't greyed out for me.

---

### Post by Uncle Spellbinder on 2009-12-04
Weird that the option was grayed out on my end. Oh, well. the gconf-editor setting worked.

---

### Post by Belizeian on 2010-01-05
Doesn't work for me I can't get rid of the last panel.

---

### Post by MooPi on 2010-01-05
In terminal:

```
sudo chmod -x /usr/bin/gnome-panel
```I prefer to just make the last panel transparent. The reverse of that will revert the change.
```
sudo chmod +x /usr/bin/gnome-panel
```

---

