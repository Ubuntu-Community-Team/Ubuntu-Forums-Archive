---
title: "How to replace emerald with gtk again?"
date: 2010-11-01
forum: General Help
---

### Post by TheNerdAL on 2010-11-01
When I login, emerald starts automatically and I want gtk to start automatically. :(

How can I fix this?

Thanks!

---

### Post by hhh on 2010-11-01
In the run dialog (Alt+F2) run ```
metacity --replace
```

You must have added Emerald to start somewhere though, either in the Compizconfig Settings Manager or in Startup Applications. Which was it?

Also, you could remove Emerald...```
sudo apt-get purge emerald
```

---

### Post by TheNerdAL on 2010-11-02
> **hhh said:**
> In the run dialog (Alt+F2) run ```
metacity --replace
```You must have added Emerald to start somewhere though, either in the Compizconfig Settings Manager or in Startup Applications. Which was it?

Also, you could remove Emerald...```
sudo apt-get purge emerald
```

That turns off desktop effects and compiz and now I can't get desktop cube to work.

---

### Post by hhh on 2010-11-03
> **TheNerdAL said:**
> That turns off desktop effects and compiz and now I can't get desktop cube to work.
Ack, of course. Sorry.
> You must have added Emerald to start somewhere though, either in the Compizconfig Settings Manager or in Startup Applications. Which was it?
Anyway, in the run dialog enter ```
gtk-window-decorator --replace
```
Make sure that in CompizConfig Settings Manager>Effects>Window Decoration>Command you hit the broom icon so it says /usr/bin/compiz-decorator again. More info...
[http://wiki.compiz.org/Decorators/GTKWindowDecorator](http://wiki.compiz.org/Decorators/GTKWindowDecorator)
[http://wiki.compiz.org/Decorators/Emerald](http://wiki.compiz.org/Decorators/Emerald)

---

### Post by 3Miro on 2010-11-03
Install CCSM. Then from Sys -> Prefs -> Compiz Config, you can select windows decorations and chose between Emerald and gtk-window-decorator (both with --replace).

---

### Post by hhh on 2010-11-03
@3Miro, I pretty much just said that.

---

