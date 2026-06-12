---
title: "xscreensaver"
date: 2011-06-14
forum: General Help
---

### Post by Rodney9 on 2011-06-14
Hello,

I built 10.10 from a minimum cd and added Openbox .
I have sound, wireless, background, conky etc working.

Yet, I can not see xscreensaver, I have installed it, it is running, but I can't see it ?

Any Ideas, I have google and googled, I have  

> xscreensaver -no-splash in xinitrc and autostart.sh

Rodney

---

### Post by jake.anq on 2011-06-14
Hi

If you go to System->Preferences, how many 'Screensaver' entries are there?  If there are 2, click on the second one and see if an alert pops up saying 'xscreensaver daemon not running' or similar.  If there is only one entry, click on it and see if there are any of the screensavers from xscreensaver have appeared.

---

### Post by Rodney9 on 2011-06-14
My fault , I should of been clearer, from the minimum cd I added ONLY Openbox, no Gnome.

---

### Post by Rodney9 on 2011-06-14
The odd thing is I can run xscreensaver-demo, it will preview just fine and I can also go to menu-screens-next saver and it will work.
But the timer on xscreensaver-demo doesn't seem to work, I can set it for any amount of time but the screensaver never comes on.

---

### Post by 4Orbs on 2011-06-14
Have you an entry for xscreensaver in your Openbox autostart.sh file located in ~/.config/openbox?

---

### Post by Rodney9 on 2011-06-14
> **4Orbs said:**
> Have you an entry for xscreensaver in your Openbox autostart.sh file located in ~/.config/openbox?

I have```

xscreensaver -no-splash
```
in xinitrc and autostart.sh

---

### Post by 4Orbs on 2011-06-14
Have you tried it without the no splash portion? The entry on mine is:
```
xscreensaver &
```

---

### Post by Rodney9 on 2011-06-14
> **4Orbs said:**
> Have you tried it without the no splash portion? The entry on mine is:
```
xscreensaver &
```

Thank You for your ideas, xscreensaver & works ok as well, it does really seem to be the timer that is not working.

---

