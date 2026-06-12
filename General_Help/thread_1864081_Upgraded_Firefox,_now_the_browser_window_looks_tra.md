---
title: "Upgraded Firefox, now the browser window looks transparent?"
date: 2011-10-18
forum: General Help
---

### Post by scorbett on 2011-10-18
Ubuntu 10.04, recently upgraded Firefox to 7.01, and now the browser window appears very slightly transparent, which is incredibly distracting and annoying. I've attached a screenshot so you can see what I mean - if you look closely, you can see the background window showing through. This is most visible in the title bar area, but even in the content area you can still kind of see through, and I don't like it. No other window or application seems to exhibit this behaviour, only FF. I went through all the preference menus but I didn't see any mention of it, and google isn't turning up anything obvious. How can I disable this? Why is it only FF doing this? Which developer thought this would ever be a good idea?

---

### Post by effenberg0x0 on 2011-10-18
Open  terminal (Dash / Terminal)

Enter this.
```
gconftool-2 --set /apps/compiz-1/plugins/obs/screen0/options/opacity_values --type int 100

```

Effenberg

---

### Post by scorbett on 2011-10-18
Bingo! Thanks very much man.

---

