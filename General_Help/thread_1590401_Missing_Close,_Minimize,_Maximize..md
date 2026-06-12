---
title: "Missing Close, Minimize, Maximize."
date: 2010-10-07
forum: General Help
---

### Post by Syf1n on 2010-10-07
So i booted up my computer after awhile and now i can't move windows or see any of the buttons to close, maximize or minimize. Any ideas?

---

### Post by NT4usB on 2010-10-07
I'd get this when I messed with the appearance/desktop effects.
I try turning on the effects, remember once again why I don't use them, and when I disable them windows get pinned and locked.

Sometimes the graphics break while I'm using the computer.

Either way, a visit back to desktop effects, to pick the settings again that I've been using, fixes it.

---

### Post by nlsthzn on 2010-10-07
Try Alt+F2 then run  ```
gtk-window-decorator --replace
```

---

### Post by Syf1n on 2010-10-07
Thanks for the help man, i googled some more and tried a few things then restarted and now they work.. hopefully it stays.

---

### Post by Merthod on 2010-10-07
If ubuntu 10.04 the command is Alt+F2: "metacity --replace" and after you re-enable compiz with Alt+F2: "compiz --replace"

---

### Post by nlsthzn on 2010-10-07
> **Merthod said:**
> If ubuntu 10.04 the command is Alt+F2: "metacity --replace" and after you re-enable compiz with Alt+F2: "compiz --replace"

Strange... when I installed a theme that used emerald I ran "emerald --replace" and when I wanted to revert back to the default I ran "gtk-window-decorator --replace" and it worked perfectly for me in 10.04... however I will keep these commands in mind too :D

---

