---
title: "&quot;metacity --replace&quot; in terminal caused compiz to never load."
date: 2010-10-10
forum: General Help
---

### Post by Billt Joe on 2010-10-10
I typed the metacity --replace command in Maverick to turn off compiz so I could change compiz files for the "mac minimize" effect. The default Ubuntu installation had compiz working but now it won't work at all. I tried downloading the proprietary driver from "system --> additional drivers" as well, but it said it failed to install.

I have an ATI radeon 3200 HD card. What can I do?

---

### Post by nlsthzn on 2010-10-10
You can try:
```
compiz --replace
```

---

### Post by Billt Joe on 2010-10-10
I tried that

I get a "window borders fail to load" error
I forgot to mention it in my original post. >.>

---

### Post by nlsthzn on 2010-10-10
You wrote in the OP: "change compiz files" ... Do you think you might have borked something with changes you made?

---

### Post by hawthornso23 on 2010-10-10
```
metacity --replace 
```
is unlikely to have caused a problem with compiz and can be easily reversed by ```
compiz --replace 
```

However
> so I could change compiz files for the "mac minimize" effect.
this looks much more likely to cause a compiz problem.

Try undoing the changes that you made.

---

### Post by WorMzy on 2010-10-10
If you need to modify your Compiz settings, you should use compizconfig-settings-manager (ccsm).

---

### Post by Billt Joe on 2010-10-10
I had made a backup of compiz using Ubuntu tweak. Reverting to the backup didn't help either. :/
I guess I'll have to reinstall. By the way...where's the "use largest continuous free space" button go?

---

### Post by nlsthzn on 2010-10-10
> **Billt Joe said:**
> I had made a backup of compiz using Ubuntu tweak. Reverting to the backup didn't help either. :/
I guess I'll have to reinstall. By the way...where's the "use largest continuous free space" button go?

Won't it be easier just to try and re-install compiz (remove it in the USC and then put it back)..?

---

### Post by Billt Joe on 2010-10-10
...and that's why I always ask first. lol
*shoulda had a V8*

---

### Post by afrodeity on 2010-11-03
updates this morning borked compiz, it refuses to do anything ouch.

---

