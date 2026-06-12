---
title: "x-ray vision"
date: 2010-05-14
forum: General Help
---

### Post by dpiddyTx on 2010-05-14
So i installed emerald this weekend and it freaked on me yesterday while I was working, but after I killed emerald I noticed that my gnome-term window now had xray vision... I have my gnome-term bg set to transparent and all my other windows that were open behind my gnome-term were no longer visible, instead I could see straight through to my desktop.  I ended up having to kill compiz for metacity bc things were still screwy.

I have no idea how it happened, or how to reproduce it, but I thought having gnome-term xray vision was pretty neat and I want it back.  Is there a feature out there somewhere to enable this same behavior, or perhaps a setting in compiz/emerald that I am just missing?


(karmic)

---

### Post by jocko on 2010-05-14
What you had was fake transparency (which just shows you a part of the desktop wallpaper instead of what's really behind the window).
It probably happened because compiz crashed and left you without compositing. I don't think you can set compiz to use fake transparency, but unless you activate metacity's compositor, metacity will give it to you...

---

