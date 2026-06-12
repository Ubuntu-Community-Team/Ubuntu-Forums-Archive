---
title: "dbus-send documentation"
date: 2006-04-07
forum: General Help
---

### Post by philipacamaniac on 2006-04-07
Where you do find a list of the various messages that can be received by any given app via dbus-send?

For example, I want to make Rhythmbox go to the next track using dbus-send. I actually already know how to do that, but where is it documented, so I can figure out what else I can do?

Don't most GNOME apps have dbus calls similar to those KDE DCOP calls I'm almost starting to miss? Where do I find those calls?

---

### Post by ranf on 2006-04-08
Maybe you know this already:
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

---

### Post by philipacamaniac on 2006-04-08
[quote=ranf]Maybe you know this already:
[http://www.freedesktop.org/wiki/Software/dbus]("http://www.freedesktop.org/wiki/Software/dbus")[/quote]

I've seen that. I'm looking for the other side of the equation, as in documentation for, say, Totem, that lists the dbus calls Totem accepts.

---

### Post by wooster on 2006-06-17
I ran across this problem and I wasn't sure if you found a solution. I found a solution with dbus-send to make rhythmbox go to the next track. Here it is. 

```
dbus-send --dest='org.gnome.Rhythmbox' /org/gnome/Rhythmbox/Player org.gnome.Rhythmbox.Player.next
```

Hope this is of use to someone. Sorry if this problem was already solved.

---

### Post by doclivingston on 2006-06-18
Try running "dbus-viewer" and then choosing the appropriate thing from the drop menu (org.gnome.Rhythmbox for example). If the application supports "DBus introspection" (as Rhythmbox does) you should be able to see the methods is has.

It's fairly clumsy and can be hard to use at times, but it works.

---

