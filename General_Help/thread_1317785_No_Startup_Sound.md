---
title: "No Startup Sound"
date: 2009-11-07
forum: General Help
---

### Post by CaKiwi on 2009-11-07
This is a really minor problem but I am not getting a startup sound when I boot up Karmic. I think the last time I heard it was Intrepid. Once I boot up, sound works fine. 

Any help appreciated

---

### Post by JamesUser on 2009-11-07
Check system -> preferences -> sound and check the sound theme.. Not sure if this is the only thing to be checked.

---

### Post by fragos on 2009-11-07
System-> Preferences-> Startup Applications lists a program called "GNOME Login Sound" which can be disabled to remove that sound.

---

### Post by CaKiwi on 2009-11-07
In Sound Preferences, Sound Theme is set to Ubuntu

System-> Preferences-> Startup Applications "GNOME Login Sound" is set to
```

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

```
But I don't get a login sound. Any thoughts?

---

### Post by CaKiwi on 2009-11-07
Never mind. The Alert Volume in the Sound Preferences was turned down.

Thanks for the responses

---

