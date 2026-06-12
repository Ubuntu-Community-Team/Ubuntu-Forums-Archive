---
title: "Screen Saver crash"
date: 2010-03-20
forum: General Help
---

### Post by Devon64327 on 2010-03-20
so i know similar posts are already on these boards but they haven't been able to help me. The problem is that whenever my screensaver pops up my computer locks up forcing me to hard boot. When i try to change or turn off my screensaver the preview of the currently set one just locks up my computer as well. I'd like to know if there is some terminal commands i can use to just shut down my screensaver. Thnx

---

### Post by Devon64327 on 2010-03-20
Im gonna bump this before i go to bed and cant find it tomorow

---

### Post by Dantevus on 2010-03-21
I'm assuming your using 9.10. If so, System-Preferences-Screensaver should help. Just uncheck the box that says "Activate screensaver when computer is idle" and even change the time it takes for it to become idle just in case.

---

### Post by Devon64327 on 2010-03-23
But when i open that window it just freezes up cuz the preview of the current screensaver crashes it

---

### Post by Dantevus on 2010-03-25
```
gconftool-2  --set "/apps/gnome-screensaver/idle_activation_enabled" --type boolean false
```

That SHOULD do it for you.

---

