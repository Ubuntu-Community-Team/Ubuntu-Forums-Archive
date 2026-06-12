---
title: "rhythmbox and suspension issues"
date: 2012-01-01
forum: General Help
---

### Post by mattia.tamellini on 2012-01-01
hi everyone!

I'm not sure this is the right section, forgive me if it is not...anyway, I noticed that when on battery the system (ubuntu 11.10) automatically goes into suspension after the time set in power manager option has passed, as if it were idle, even though rhythmbox is playing. It is not a big deal, I know, but it is somewhat annoying. Does anyone know how to fix this? 
Thanks a lot

---

### Post by 2F4U on 2012-01-01
As far as I know, idle in that context is defined as no user interaction taking place. So it would be the correct behaviour that the system goes to sleep given that the system is just playing music and you are not doing anything on it (typing on the keyboard, moving the mouse),

---

### Post by mattia.tamellini on 2012-01-01
I see...but in previous releases this did not happen (I just installed ubuntu 11.10, I had 10.10 until last week). And when the laptop is connected to power this does not happen either. Is there any way to prevent this from happening also on battery? 

ps: may it be caused by the fact that I also installed jupiter in order to get more battery life, since this last release is pretty weak on that aspect? should I make any change to jupiter configuration files?

---

### Post by mattia.tamellini on 2012-01-03
ok, the solution is to enable rhyhtmbox plugin "power manager"...I have it installed on my laptop, since I found it in ```
/usr/lib/rhythmbox/plugins/
``` 

but it doesn't appear in rhythmbox plugins list in settings/plugins

I tried reinstalling it by doing:
```
sudo apt-get remove --purge rhythmbox-plugins
sudo apt-get autoremove --purge
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install rhythmbox-plugins
```

but still nothing...how do I enable it?

---

