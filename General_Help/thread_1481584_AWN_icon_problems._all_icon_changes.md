---
title: "AWN icon problems. all icon changes"
date: 2010-05-12
forum: General Help
---

### Post by fortygogetters on 2010-05-12
sorry if this has already been discussed but i've looked for a thread with the same issue but could not find one.

what my problem is that when i change one icon all the other icons change. these icons would be icons that i create launchers for. maybe i am making the launcher commands wrong? any help would be greatly appreciated.

---

### Post by robincawser on 2010-05-12
Wow I was just googling for the same issue! 
I have two chromium launchers. One to launch gmail as a standalone app, with the command
 ```
chromium-browser --user-data-dir=~/.gmail --app=http://www.gmail.com --class=Gmail $*
``` 

and one to just launch plain chromium
```
chromium-browser %U
```

I set the gmail-chromium launcher to have a gmail icon. But this change it for both launchers.

---

### Post by robincawser on 2010-05-12
I think I solved my above issue. I created a launcher on the desktop for my gmail app, and then added that to AWN. Seems to be working.

---

