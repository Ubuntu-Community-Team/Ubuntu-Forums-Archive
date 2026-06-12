---
title: "Reset AWN"
date: 2010-05-23
forum: General Help
---

### Post by kantu on 2010-05-23
I was trying to reset AWN and as shown in FAQ i did this
```

 gconftool-2 --recursive-unset /apps/avant-window-navigator

```
Previously i had changed Icon of firefox after resetting AWN everything will fall back to System Default(i.e theme) icons except firefox
This looks very annoying to me . I reseted AWN and removed it but still its entries are in Gconf-editor i looked up in ~/.gconf/app and avant-navigator is not there but still its in gconf ..  i am confused .. 
how else should i reset it so that it will uses sys icons

---

### Post by -humanaut- on 2010-05-23
You could just sudo apt-get purge avant-window-manager && sudo apt-get install avant-window-manager That's the only way I can really think of to reset the configuration to default though I'm not very familiar with docks since I don't use them.

---

