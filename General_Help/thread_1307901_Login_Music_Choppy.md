---
title: "Login Music Choppy"
date: 2009-10-31
forum: General Help
---

### Post by Rosemachinegun on 2009-10-31
I just upgraded to Karmic without any problems but one!

The login music is terribly choppy. I don't care that much but I really just want to turn it off for future logins. However, it's not readily apparent how to do this. There's no system sound options in System/Preferences/Sound anymore so I don't know how to go about this.
Any advice?

Thanks!

---

### Post by Relysis on 2009-11-02
I'd like to bump this and say that mine does the same thing.  The launchpad bug highlights the problem by running 
```
canberra-gtk-play --id="desktop-login" --description="GNOME Login"
``` 
The actual sound file plays normally.  This is the first I've heard of canberra... anybody else have an idea?

---

