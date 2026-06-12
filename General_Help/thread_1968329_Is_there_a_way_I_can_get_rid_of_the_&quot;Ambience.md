---
title: "Is there a way I can get rid of the &quot;Ambience&quot; theme for good."
date: 2012-04-28
forum: General Help
---

### Post by djtcircuit on 2012-04-28
I'm not going to get into a rant here, but I got tired of Unity and removed it.  I switched to MATE, which was working out great until I actually tried to use Compiz with Cairo-Dock.

Compiz slows down my netbook ridiculously, but what I also noticed is that every time I toggle it on all my window borders change to that awful charcoal-color title bar with orange buttons, overriding the custom theme settings I had, and seemingly messing with them.

Is there a way I can fix this?

---

### Post by zombifier25 on 2012-04-28
Compiz currently only uses 3 windows decorator: gtk-window-decorator (which is what you're using), kde-window-decorator and emerald. So if you want to change the decorator, you must change the default GNOME theme.

---

### Post by pqwoerituytrueiwoq on 2012-04-29
if you want to get rid of ambiance theme
[FONT=Courier New]sudo apt-get remove light-themes[/FONT]
but that is not going to fix compiz window theme in mate
```
gtk-window-decorator --replace --metacity-theme "[INSERT THEME HERE]"
```
adding that to start-up might

I have a box with xfce and mate this is my login script i use to get mate working with compiz and what ever else i want in mate i dont want to run in xfce some of it maybe useful to you
```
#!/bin/sh
ogg123 /usr/share/sounds/freedesktop/stereo/service-login.oga &
if [ 0`pidof mate-session` -gt 0 ]; then
    if [ 0`pidof compiz` -lt 1 ]; then
        while [ 0`pidof marco` -lt 1 ]; do
            sleep 0.25
        done
    fi
    killall marco
    compiz --replace &
    gtk-window-decorator --replace --metacity-theme "Ambiance" &
    fusion-icon --no-start &
    sleep 3
    conky &
    sleep 5
    if [ 0`pidof conky` -lt 1 ]; then
        conky &
    fi
fi
```

@zombifier25
you missed one compiz-decorator

---

