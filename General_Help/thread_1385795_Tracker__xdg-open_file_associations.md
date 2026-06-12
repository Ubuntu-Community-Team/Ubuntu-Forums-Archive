---
title: "Tracker / xdg-open file associations"
date: 2010-01-20
forum: General Help
---

### Post by hugo87 on 2010-01-20
I'm running a standalone compiz (not in gnome, but just compiz, gnome-do and AWN).

I use tracker to search for my stuff all the time, however, since I started using compiz without gnome, when I click results they're always opened by the browser (folders, mp3s, etc).

I belive tracker uses xdg-open, and I noticed xdg-open exhibits the same behaviour.
Where do I change the file associations xdg-open uses? I've found little to no documentation about it.

BTW: I use dolphin, so if I could get it to use the same associations, that would be realy cool.

---

### Post by hugo87 on 2010-01-20
I couldn't find a proper solution nor much xdg-open documentation so I just edited /usr/bin/xdg-open

```

detectDE()
{
#COMMENT BELOW
#    if [ x"$KDE_FULL_SESSION" = x"true" ]; then DE=kde;
#    elif [ x"$GNOME_DESKTOP_SESSION_ID" != x"" ]; then DE=gnome;
#    elif `dbus-send --print-reply --dest=org.freedesktop.DBus /org/freedesktop/$
#    elif xprop -root _DT_SAVE_MODE 2> /dev/null | grep ' = \"xfce4\"$' >/dev/nu$
#    fi
    ####### EDIT HERE ######
    DE=kde 
}

```

I just force xdg-open to think it detected kde (could have been gnome), and override the proper value.

---

