---
title: "Eclipse problems in Karmic: Cancel works, Next does not"
date: 2010-01-18
forum: General Help
---

### Post by nimonika on 2010-01-18
Yesterday all of a sudden, when I started eclipse, I found I could no more create any new java project. Thinking it may be a problem with my workspace, I made another workspace and tried creating a project there, with no success. 

The strange thing is that the interface closes when I hit the cancel button, but when I do Next the system just freezes. Urgent help needed

Thanks

---

### Post by keya.nema on 2010-02-08
Try setting the environment variable, GDK_NATIVE_WINDOWS to true and restart eclipse:

$ GDK_NATIVE_WINDOWS=true; ./eclipse

This should help.  It worked for me.  Though I am still finding few icons missing in my IDE.

---

